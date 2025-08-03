# Frappe App Development Guidelines

This document outlines the standards and best practices for developing custom Frappe applications using this template. Following these guidelines ensures consistency, maintainability, and high code quality across all Frappe projects.

## 🎯 Purpose

The goal of this template is to ensure that every custom Frappe app:
- Follows the same coding standards and conventions
- Implements consistent project structure
- Uses standardized linting and formatting tools
- Maintains high code quality and security
- Provides comprehensive documentation
- Follows Frappe best practices

## 📁 Frappe App Structure

### Standard Directory Structure

```
your_frappe_app/
├── your_frappe_app/
│   ├── __init__.py
│   ├── config/
│   │   ├── __init__.py
│   │   ├── desktop.py
│   │   └── docs.py
│   ├── modules/
│   │   └── your_module/
│   │       ├── __init__.py
│   │       ├── api.py
│   │       ├── config.py
│   │       ├── custom_fields.py
│   │       ├── dashboard.py
│   │       ├── hooks.py
│   │       ├── page/
│   │       ├── report/
│   │       ├── templates/
│   │       ├── utils.py
│   │       └── web_form/
│   ├── patches/
│   │   └── __init__.py
│   ├── public/
│   │   ├── css/
│   │   ├── js/
│   │   └── images/
│   ├── templates/
│   │   ├── includes/
│   │   └── pages/
│   ├── translations/
│   └── www/
├── tests/
│   ├── __init__.py
│   └── test_your_module.py
├── docs/
├── hooks.py
├── modules.txt
├── patches.txt
├── requirements.txt
├── setup.py
└── README.md
```

## 🔧 Development Standards

### 1. Code Organization

#### Module Structure
- **One module per business domain**
- **Clear separation of concerns**
- **Consistent naming conventions**
- **Proper import organization**

#### File Naming
```python
# Use snake_case for all Python files
customer_management.py
sales_order.py
invoice_utils.py

# Use kebab-case for JavaScript/Vue files
customer-dashboard.js
sales-order-form.vue
invoice-calculator.js
```

### 2. Python Code Standards

#### Import Organization
```python
# Standard library imports
import os
import sys
from datetime import datetime
from typing import Dict, List, Optional

# Third-party imports
import frappe
from frappe import _
from frappe.model.document import Document

# Local application imports
from .utils import format_currency
from .constants import DEFAULT_CURRENCY
```

#### Docstring Standards
```python
def create_customer(name: str, email: str, phone: str = None) -> str:
    """
    Create a new customer in the system.

    Args:
        name (str): Full name of the customer
        email (str): Email address of the customer
        phone (str, optional): Phone number of the customer

    Returns:
        str: Name of the created customer document

    Raises:
        frappe.ValidationError: If customer with same email already exists

    Example:
        >>> customer_name = create_customer("John Doe", "john@example.com")
        >>> print(customer_name)
        'CUST-2024-00001'
    """
    pass
```

#### Error Handling
```python
def process_payment(amount: float, customer: str) -> bool:
    """Process payment for a customer."""
    try:
        # Payment processing logic
        payment = frappe.get_doc({
            "doctype": "Payment",
            "customer": customer,
            "amount": amount,
            "status": "Pending"
        })
        payment.insert()
        payment.submit()
        return True

    except frappe.ValidationError as e:
        frappe.log_error(f"Payment validation failed: {e}")
        raise

    except Exception as e:
        frappe.log_error(f"Payment processing failed: {e}")
        frappe.throw(_("Payment processing failed. Please try again."))
```

### 3. JavaScript/Vue Standards

#### Vue Component Structure
```vue
<template>
  <div class="customer-form">
    <form @submit.prevent="handleSubmit">
      <div class="form-group">
        <label for="customer-name">{{ __('Customer Name') }}</label>
        <input
          id="customer-name"
          v-model="formData.name"
          type="text"
          class="form-control"
          :class="{ 'is-invalid': errors.name }"
          required
        />
        <div v-if="errors.name" class="invalid-feedback">
          {{ errors.name }}
        </div>
      </div>

      <button type="submit" class="btn btn-primary" :disabled="loading">
        {{ loading ? __('Saving...') : __('Save Customer') }}
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'CustomerForm',
  data() {
    return {
      formData: {
        name: '',
        email: '',
        phone: ''
      },
      errors: {},
      loading: false
    }
  },
  methods: {
    async handleSubmit() {
      this.loading = true
      this.errors = {}

      try {
        const result = await frappe.call({
          method: 'your_app.api.create_customer',
          args: this.formData
        })

        frappe.show_alert(__('Customer created successfully!'), 'success')
        this.$emit('customer-created', result.message)

      } catch (error) {
        this.handleError(error)
      } finally {
        this.loading = false
      }
    },

    handleError(error) {
      if (error.exc_type === 'ValidationError') {
        this.errors = error.exc[1]
      } else {
        frappe.show_alert(__('An error occurred. Please try again.'), 'error')
      }
    }
  }
}
</script>

<style scoped>
.customer-form {
  max-width: 600px;
  margin: 0 auto;
  padding: 20px;
}

.form-group {
  margin-bottom: 1rem;
}

.form-control {
  width: 100%;
  padding: 0.375rem 0.75rem;
  border: 1px solid #ced4da;
  border-radius: 0.25rem;
}

.is-invalid {
  border-color: #dc3545;
}

.invalid-feedback {
  display: block;
  color: #dc3545;
  font-size: 0.875rem;
  margin-top: 0.25rem;
}
</style>
```

### 4. Database Standards

#### DocType Design
```python
# hooks.py
def get_doctype_js(docname):
    """Return custom JS for specific DocTypes."""
    if docname == "Customer":
        return ["your_app/public/js/customer.js"]
    return []

# Custom Fields
def get_custom_fields():
    """Define custom fields for existing DocTypes."""
    return {
        "Customer": [
            {
                "fieldname": "customer_category",
                "label": "Customer Category",
                "fieldtype": "Select",
                "options": "Premium\nStandard\nBasic",
                "default": "Standard"
            }
        ]
    }
```

#### API Design
```python
# api.py
import frappe
from frappe import _
from typing import Dict, List, Optional

@frappe.whitelist()
def get_customer_details(customer: str) -> Dict:
    """
    Get detailed information about a customer.

    Args:
        customer (str): Customer name

    Returns:
        Dict: Customer details
    """
    if not frappe.has_permission("Customer", "read", customer):
        frappe.throw(_("Permission denied"))

    customer_doc = frappe.get_doc("Customer", customer)
    return {
        "name": customer_doc.name,
        "customer_name": customer_doc.customer_name,
        "customer_type": customer_doc.customer_type,
        "customer_group": customer_doc.customer_group,
        "territory": customer_doc.territory,
        "credit_limit": customer_doc.credit_limit,
        "credit_days": customer_doc.credit_days
    }

@frappe.whitelist()
def create_customer(customer_data: Dict) -> str:
    """
    Create a new customer.

    Args:
        customer_data (Dict): Customer information

    Returns:
        str: Name of created customer
    """
    if not frappe.has_permission("Customer", "create"):
        frappe.throw(_("Permission denied"))

    # Validate required fields
    required_fields = ["customer_name", "customer_type"]
    for field in required_fields:
        if not customer_data.get(field):
            frappe.throw(_("Field {0} is required").format(field))

    # Create customer
    customer = frappe.get_doc({
        "doctype": "Customer",
        **customer_data
    })
    customer.insert()

    return customer.name
```

### 5. Testing Standards

#### Unit Tests
```python
# tests/test_customer.py
import unittest
import frappe
from frappe.test_runner import make_test_records

class TestCustomer(unittest.TestCase):
    def setUp(self):
        """Set up test data."""
        frappe.db.sql("DELETE FROM `tabCustomer` WHERE customer_name LIKE 'Test%'")
        make_test_records("Customer")

    def test_create_customer(self):
        """Test customer creation."""
        customer_data = {
            "customer_name": "Test Customer",
            "customer_type": "Company",
            "customer_group": "Commercial"
        }

        customer = frappe.get_doc({
            "doctype": "Customer",
            **customer_data
        })
        customer.insert()

        self.assertIsNotNone(customer.name)
        self.assertEqual(customer.customer_name, "Test Customer")

    def test_customer_validation(self):
        """Test customer validation."""
        # Test duplicate customer name
        customer1 = frappe.get_doc({
            "doctype": "Customer",
            "customer_name": "Duplicate Customer"
        })
        customer1.insert()

        customer2 = frappe.get_doc({
            "doctype": "Customer",
            "customer_name": "Duplicate Customer"
        })

        with self.assertRaises(frappe.ValidationError):
            customer2.insert()

    def tearDown(self):
        """Clean up test data."""
        frappe.db.sql("DELETE FROM `tabCustomer` WHERE customer_name LIKE 'Test%'")
```

### 6. Documentation Standards

#### README.md Template
```markdown
# Your Frappe App

Brief description of what this app does.

## Features

- Feature 1: Description
- Feature 2: Description
- Feature 3: Description

## Installation

1. Install the app:
   ```bash
   bench get-app your_app_name
   bench install-app your_app_name
   ```

2. Run migrations:
   ```bash
   bench migrate
   ```

3. Build assets:
   ```bash
   bench build
   ```

## Configuration

Describe any configuration options.

## Usage

Explain how to use the app.

## API Reference

Document your API endpoints.

## Development

See [DEVELOPMENT.md](docs/DEVELOPMENT.md) for development setup.

## Contributing

See [CONTRIBUTING.md](docs/CONTRIBUTING.md) for contribution guidelines.

## License

This project is licensed under the MIT License.
```

## 🚀 Deployment Standards

### 1. Production Checklist

- [ ] All tests pass
- [ ] Code quality checks pass
- [ ] Documentation is complete
- [ ] Security audit completed
- [ ] Performance testing done
- [ ] Database migrations tested
- [ ] Backup procedures in place

### 2. Release Process

1. **Version bump** in `setup.py`
2. **Update changelog** in `docs/CHANGELOG.md`
3. **Create release tag**
4. **Deploy to staging**
5. **Run integration tests**
6. **Deploy to production**
7. **Monitor for issues**

## 🔒 Security Standards

### 1. Permission Management
- Always check permissions in API methods
- Use `frappe.has_permission()` for validation
- Implement role-based access control
- Document permission requirements

### 2. Data Validation
- Validate all user inputs
- Use Frappe's built-in validation
- Implement custom validation where needed
- Sanitize data before database operations

### 3. Error Handling
- Never expose sensitive information in errors
- Log errors appropriately
- Provide user-friendly error messages
- Handle exceptions gracefully

## 📊 Performance Standards

### 1. Database Optimization
- Use appropriate indexes
- Optimize queries
- Implement pagination for large datasets
- Use database transactions appropriately

### 2. Frontend Performance
- Minimize JavaScript bundle size
- Optimize images and assets
- Implement lazy loading
- Use caching strategies

## 🧪 Quality Assurance

### 1. Code Review Checklist
- [ ] Code follows style guidelines
- [ ] Tests are included
- [ ] Documentation is updated
- [ ] Security considerations addressed
- [ ] Performance impact assessed
- [ ] Error handling implemented

### 2. Testing Requirements
- Unit tests for all functions
- Integration tests for workflows
- Frontend tests for components
- API tests for endpoints
- Performance tests for critical paths

## 📚 Additional Resources

- [Frappe Documentation](https://frappeframework.com/docs)
- [Frappe Development Guide](https://frappeframework.com/docs/user/en/guides/basics)
- [Frappe API Reference](https://frappeframework.com/docs/user/en/api)
- [Vue.js Documentation](https://vuejs.org/guide/)
- [Python Best Practices](https://docs.python-guide.org/)

---

**Remember**: Consistency is key. Every custom Frappe app should follow these standards to ensure maintainability, scalability, and code quality across your entire Frappe ecosystem.

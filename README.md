# Free Email Providers

> A comprehensive list of free email providers and domains for validation and filtering

[![npm version](https://badge.fury.io/js/%40email-check-app%2Ffree-email-providers.svg)](https://badge.fury.io/js/%40email-check-app%2Ffree-email-providers)
[![GitHub license](https://img.shields.io/github/license/email-check-app/free-email-providers.svg)](https://github.com/email-check-app/free-email-providers/blob/master/LICENSE.md)
[![GitHub stars](https://img.shields.io/github/stars/email-check-app/free-email-providers.svg?style=social&label=Star)](https://github.com/email-check-app/free-email-providers)

## Overview
* Filter free email providers during user registration
* Implement business email validation
* Enhance spam prevention systems
* Complement disposable email detection

## Statistics
* **Total Domains**: 96,748
* **JSON Format**: 96,748 entries
* **Text Format**: Raw domain list
* **Regular Updates**: Monthly maintenance and community contributions

## Available Formats
### JSON Format
The `free-email-providers.json` file contains an array of domain strings with 96,748 entries.

**Usage Example:**
```javascript
const providers = require('./free-email-providers.json');
console.log(`Total domains: ${providers.length}`);
```

### Source Data
The project maintains source data that gets processed into the final JSON format through an automated build script that handles deduplication and sorting.

## Quick Start
### Node.js
```javascript
const freeEmailProviders = require('@emailcheck/free-email-providers');

function isFreeEmail(email) {
  const domain = email.split('@')[1]?.toLowerCase();
  return freeEmailProviders.includes(domain);
}

// Examples
console.log(isFreeEmail('user@gmail.com')); // true
console.log(isFreeEmail('user@company.com')); // false
```

### Python
```python
import json
import re

with open('free-email-providers.json', 'r') as f:
    providers = json.load(f)

def is_free_email(email):
    domain = email.split('@')[1].lower() if '@' in email else ''
    return domain in providers

# Examples
print(is_free_email('user@gmail.com'))  # True
print(is_free_email('user@company.com'))  # False
```

## Integration Examples
### Regex Pattern
```javascript
const providers = require('@emailcheck/free-email-providers');
const escapedDomains = providers.map(domain => domain.replace(/\./g, '\\.'));
const freeEmailPattern = new RegExp(`@(${escapedDomains.join('|')})$`, 'i');

function isFreeEmail(email) {
  return freeEmailPattern.test(email);
}
```

### Form Validation
```javascript
document.getElementById('email').addEventListener('blur', function(e) {
  const email = e.target.value;
  if (isFreeEmail(email)) {
    showError('Please use a business email address');
  }
});
```

### Server-side Validation (Express.js)
```javascript
const express = require('express');
const providers = require('@emailcheck/free-email-providers');

const app = express();

app.post('/register', (req, res) => {
  const { email } = req.body;
  const domain = email.split('@')[1]?.toLowerCase();

  if (providers.includes(domain)) {
    return res.status(400).json({ error: 'Free email providers are not allowed' });
  }

  // Continue with registration
});
```

## Maintenance
* **Daily Monitoring**: Automated checks for provider availability
* **Monthly Updates**: Manual review and new provider additions
* **Community Contributions**: Pull requests reviewed and merged
* **Quality Assurance**: Automated duplicate removal and domain validation
* **Source Aggregation**: Multiple reputable sources combined
* **Build Process**: Automated script processes and consolidates data from multiple sources

## License
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

## Contributing
1. Fork the repository
2. Create a feature branch
3. Add your changes to the source files
4. Run the build script to process and deduplicate the data
5. Submit a pull request with a clear description

## Important Notes
* **Active Providers Only**: List contains only currently active free email services
* **Regular Updates**: Providers are verified monthly for availability
* **Comprehensive Coverage**: Includes webmail, temporary, and regional providers
* **Automated Processing**: All entries are deduplicated and sorted alphabetically via build script
* **Performance Optimized**: JSON format for efficient parsing and lookup
* **Quality Assured**: Multi-source aggregation with automated validation

## Related Projects
* **[email-validator-js](https://github.com/email-check-app/email-validator-js/)** - JavaScript email validation library using this provider list
* **[Email Check API](https://email-check.app/)** - Cloud service for email validation and deliverability checking
* **[disposable-email-providers](https://github.com/email-check-app/disposable-email-providers)** - List of disposable/temporary email providers

## Support
* **Issues**: [Create an issue](https://github.com/email-check-app/free-email-providers/issues) for bugs or requests
* **Discussions**: [Join discussions](https://github.com/email-check-app/free-email-providers/discussions) for questions
* **Website**: [Email Check App](https://email-check.app)

---

**Made with ❤️ by [Email Check App](https://email-check.app)**

If you find this useful, please give us a ⭐ on GitHub!

# Configuration

ConsentCookie uses a JSON object to define its configuration. The current configuration options are:

{% hint style="info" %}
The possible values for the configuration are omitted here.
{% endhint %}

```javascript
{
  "general": {
    "gdpr": {
      "contact": ""
    },
    "consentwall": {
      "enabled": "",
      "timeout": ""
    }
  },
  "apps": {
    "endpoint": "",
    "consent": {}
  },
  "design": {
    "layout": {
      "position": ""
    },
    "colorscheme": {
      "primary": "",
      "secondary": ""
    }
  },
  "resources": {
    "nl": {
      "about": {
        "title": "",
        "text": ""
      },
      "consent": {
        "title": "",
        "text": "",
        "button": "",
        "infolink": ""
      }
    }
  }
}
```


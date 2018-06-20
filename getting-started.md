# Getting started

#### Include the script on your website:

```markup
<script type="application/javascript" src="/path/to/consentcookie.min.js"></script>
```

{% hint style="info" %}
For all configuration options: [link](configuration/)
{% endhint %}

#### Initialize ConsentCookie:

```markup
<script type="application/javascript">
  // An example of ConsentCookie initialized with a custom config
  ConsentCookie.init({
    'apps': {
      'consent': {
        'cc': {
          'initstate': 'alwayson'
        },
        'iq': {
          'initstate': 'alwayson'
        },
        'ga': {
          'initstate': 'optin'
        },
        'gtm': {
          'initstate': 'optout'
        }
      }
    }
  });
</script>
```

{% hint style="danger" %}
Using this example with the example configuration will not make you GDPR compliant. Check the following on how to correctly configure ConsentCookie: [link](configuration/)
{% endhint %}




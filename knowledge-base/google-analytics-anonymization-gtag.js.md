# Google Analytics Anonymization - gtag.js

Google Analytics \(gtag.js\) has the [option](https://developers.google.com/analytics/devguides/collection/gtagjs/ip-anonymization) to collect data of your website visitors anonymously. ConsentCookie provides the option to conditionally enable this option based on the consent setting of Google Analytics.

For example, Google Analytics is configured as opt-in but you still want to collect data anonymously when the website visitor has not yet given their consent for analytic purposes.

The default Google Analytics \(gtag.js\) sitetag looks as follow

```javascript
<script>
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  gtag('config', 'GA_TRACKING_ID');
</script>
```

By adding some extra script we can:

* If the visitor has given their consent
* Enable ip anonymization when the consent is not given

```javascript
// Check if the consent has been given by the vistor
var isAccepted = ConsentCookie && ConsentCookie.get("ga").isAccepted();
// When the consent has not been given, configure ip anonymization
var gaAnonymizeConfig = (isAccepted === true ? {} : { 'anonymize_ip': true });
```

When we update the default Google Analytics \(gtag.js\) sitetag it looks as follow

```javascript
<script>
  // Check if the consent has been given by the vistor
  var isAccepted = ConsentCookie && ConsentCookie.get("ga").isAccepted();
  // When the consent has not been given, configure ip anonymization
  var gaAnonymizeConfig = (isAccepted === true ? {} : { 'anonymize_ip': true });

  // Default gtag.js config
  window.dataLayer = window.dataLayer || [];
  function gtag(){dataLayer.push(arguments);}
  gtag('js', new Date());

  // Add the anonymization config to gtag
  // https://developers.google.com/analytics/devguides/collection/gtagjs/ip-anonymization
  gtag('config', 'GA_TRACKING_ID',gaAnonymizeConfig);
</script>
```

We can optimise this to

```javascript
<script>
    window.dataLayer = window.dataLayer || [];
    function gtag(){dataLayer.push(arguments);}
    gtag('js', new Date());

    // Add the anonymization config to gtag
    // https://developers.google.com/analytics/devguides/collection/gtagjs/ip-anonymization
    gtag('config', 'GA_TRACKING_ID',(ConsentCookie && ConsentCookie.get("ga").isAccepted()) ? {} : { 'anonymize_ip': true });
</script>
```


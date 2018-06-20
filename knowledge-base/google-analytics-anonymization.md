# Google Analytics Anonymization - [analytics.js](https://developers.google.com/analytics/devguides/collection/analyticsjs/)

Google Analytics \(analytics.js\) has the [option](https://developers.google.com/analytics/devguides/collection/analyticsjs/ip-anonymization) to collect data of your website visitors anonymously. ConsentCookie provides the option to conditionally enable this option based on the consent setting of Google Analytics.

For example, Google Analytics is configured as [opt-in](../configuration/) but you still want to collect data anonymously when the website visitor has not yet given their consent for analytic purposes.

The default Google Analytics \(analytics.js\) sitetag looks as follow

```html
<!-- Google Analytics -->
<script>
    (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
    (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
    m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
    })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

    ga('create', 'UA-XXXXX-Y', 'auto');
    ga('send', 'pageview');
</script>
<!-- End Google Analytics -->
```

By adding some extra script we can:

* If the visitor has given their consent
* Enable ip anonymization when the consent is not given

```js
// Check if the consent has been given by the vistor
var isAccepted = ConsentCookie && ConsentCookie.get("ga").isAccepted();
// When the consent has not been given, configure ip anonymization
if(!isAccepted){
    // https://developers.google.com/analytics/devguides/collection/analyticsjs/ip-anonymization
    ga('set', 'anonymizeIp', true);
}
```

When we update the default Google Analytics \(gtag.js\) sitetag it looks as follow

```js
<!-- Google Analytics -->
<script>
    (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
    (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
    m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
    })(window,document,'script','https://www.google-analytics.com/analytics.js','ga');

    // Check if the consent has been given by the vistor
    var isAccepted = ConsentCookie && ConsentCookie.get("ga").isAccepted();
    // When the consent has not been given, configure ip anonymization
    if(!isAccepted){
        ga('set', 'anonymizeIp', true);
    }

    // Default analytics.js config
    ga('create', 'UA-XXXXX-Y', 'auto');
    ga('send', 'pageview');
</script>
<!-- End Google Analytics -->
```




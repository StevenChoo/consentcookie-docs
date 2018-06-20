# Google Tag Manager - Google Analytics Anonymization

Google Tag Manager \(gtm\) can be [used](https://www.consentcookie.nl/knowledgebase/google-tag-manager-en-consentcookie/) to integeratie ConsentCookie into your website. Combining gtm and ConsentCookie give website visitors the option to control which tags are loaded based on the consent they have given.

Google Analytics, a common gtm tag, has the option to collect data of your website visitors anonymously. We can combine gtm, ConsentCookie and the [Google Analytics tag](https://support.google.com/tagmanager/answer/6107124) to enable or disable the anonymization config for Google Analytics based on the consent given by the website visitor.

The default configuration for the Google Analytics tag to enable anonymization looks as follow![](/assets/gtm-analytics1.png)

Instead of a static value `true` we can use ConsentCookie to check if a consent has been given and based on that enable or disable anonymization.

For example, Google Analytics is configured as opt-in but you still want to collect data anonymously when the website visitor has not yet given their consent for analytic purposes.

For that we need to first add a new user-defined variable that represent the consent value for Google Analytics. For that we use a Custom Javascript variable, with the following script

```js
function(){java
  // Check if the consent has been given by the vistor
  var isAccepted = ConsentCookie && ConsentCookie.get("ga").isAccepted();
  // We want enable ip anonymization when no consent has been given
  var enableAnonymizeIp = !isAccepted;
  // return the value used as field value for gtm tag config
  return enableAnonymizeIp;
}
```

And we can optimise this to

```js
function(){
  return !(ConsentCookie && ConsentCookie.get("ga").isAccepted());
}
```

The variable config will look as folllow![](/assets/gmt-analytics2.png)After adding the new user-defined variable, save the changes and assign the variable to the Google Analytics tag.![](/assets/gtm-analytics3.png)![](/assets/gtm-analytics4.png)  
After updating the Google Analytics settings make sure to update the trigger as well. When you used the [knowledge base](https://www.consentcookie.nl/knowledgebase/google-tag-manager-en-consentcookie/) article to integrate ConsentCookie using gtm, the Google Analytics tag is triggered by a custom trigger that only is fired when the consent has been accepted for Google Analytics. Because we are using the anonymization option this is not a requirement.

You can use for example the default trigger `Window Loaded` but any trigger would suffice as long as the Google Analytics tag is loaded after the ConsentCookie tag.








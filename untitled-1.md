# Untitled



Blocking third-party scripts

You can block and have user enable third-party scripts using ConsentCookie.

ConsentCookie MultiLanguage

All static text in ConsentCookie except for external loaded resources \(e.g. ConsentCookie applications\) can be translated into different languages. The current default language is Dutch.

Using the resources config, you can provide different languages for each language code.

Current used Dutch translation

```javascript
resources: {
    nl: {
      general: {
        on: 'Aan',
        off: 'Uit',
        close: 'Sluiten',
        moreInfo: 'Meer informatie'
      },
      menu: {
        applications: 'Jouw instellingen',
        about: 'Over ConsentCookie',
        open: 'ConsentCookie openen',
        close: 'ConsentCookie sluiten',
        disabled: 'accepteer eerst',
      },
      applications: {
        title: 'Jouw instellingen',
        moreInfo: 'Meer informatie over deze applicaties',
        moreInfoLink: 'https://www.consentcookie.nl',
        actions: {
          gdpr: 'Recht op...',
        },
        detail: {
          moreInfo: 'Meer informatie over',
          gdprInfo: 'Contact over jouw AVG rechten'
        },
        profile: {
          title: 'Jouw profiel',
          loading: 'Profiel wordt opgehaald',
          noPlugin: 'Deze applicatie heeft geen publiek profiel beschikbaar',
          noProfile: 'Geen profiel beschikbaar',
        }
      },
      about: {
        title: 'Over ConsentCookie',
        text: '',
      },
      consent: {
        title: 'ConsentCookie!',
        text: '',
        button: 'Ok!',
        infolink: 'https://www.consentcookie.nl',
      },
    },
  }
```


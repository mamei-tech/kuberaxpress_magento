## Magento 2 Spanish Language Pack

Magento 2 platform approves multiple languages around the world, so **Magento 2 Spanish Language Pack** is created to conduct the change of language via the in-line translation dictionary on Magento 2 store. The in-line translation dictionary is developed based on the community project at Crowdin where you can download over 12,000 phrases in Spanish to replace the default language. Magento 2 Spanish Language Package will involve the list of comprehensive guides which are essential for the perfect translation. Please keep tracking the topic to finish the interpretation at all.

Read more [Magento 2 Spanish Language Pack](https://www.mageplaza.com/magento-2-spanish-language-pack.html)

![Mageplaza Spanish language pack](https://cdn3.mageplaza.com/media/general/qjWPj1W.png)

## Overview

1. Language Package Process
2. Install Spanish Language Pack
3. How to change the language in Admin Panel Magento 2

## 1. Language Package Process

This is status of Spanish Language Pack, you can see how many percentage of this project has been done.

![Spanish language pack process](https://progress-bar.dev//?title=completed)

It is not fully translated? Feel free to contribute:
- [On Crowdin](https://crowdin.com/project/magento-2): It takes time to approve your contribution by Magento team.
- [On Github](https://github.com/mageplaza/magento-2-spanish-language-pack/blob/master/HOW-TO-CONTRIBUTE.md): It's faster, our team will approve it after you send pull request.


Find other [language packs here](https://www.mageplaza.com/magento-2-extensions/language-packs.html)

## 2. How to Install Spanish Language Pack

There are 3 different methods to install this language pack.

### ✓ Method #1. Composer method (Recommend)
Install the Spanish language pack via composer is never easier.

**Install Spanish pack**:

With Marketing Automation (recommend):

```
bin/composer require mageplaza/magento-2-spanish-language-pack:dev-master mageplaza/module-smtp
bin/magento setup:static-content:deploy --theme Magento/backend -f es_ES 
bin/magento setup:static-content:deploy -f es_ES
bin/magento indexer:reindex && bin/magento cache:clean && bin/magento cache:flush
```

Without Marketing Automation:

```
bin/composer require mageplaza/magento-2-spanish-language-pack:dev-master
bin/magento setup:static-content:deploy --theme Magento/backend -f es_ES
bin/magento setup:static-content:deploy -f es_ES
bin/magento indexer:reindex && bin/magento cache:clean && bin/magento cache:flush
```


**Update  Spanish pack**:

```
bin/composer update mageplaza/magento-2-spanish-language-pack:dev-master
bin/magento setup:static-content:deploy --theme Magento/backend -f es_ES
bin/magento setup:static-content:deploy -f es_ES
bin/magento indexer:reindex && bin/magento cache:clean && bin/magento cache:flush
```

#### Authentication required (If any)

![Authentication required](https://cdn.mageplaza.com/media/general/dmryiPk.png)

If you have not added this authentication, you can follow [this guide](http://devdocs.magento.com/guides/v2.0/install-gde/prereq/connect-auth.html)

Or use these keys:

```
Public Key: c7af1bfc9352e9c986637eec85ed53af
Private Key: 17e1b72ea5f0b23e9dbfb1f68dc12b53
```

## How to change the language in Admin Panel Magento 2

##### Change store frontend language
Let’s assume you need to change the default language settings of the platform. What is the first thing you do?

- Log in to the Admin Panel.
- Navigate to the Stores > Configuration.
- Choose Default Config, then the language for the Main Website/ Main Website Store.
- Select one of the offered languages in the drop-down menu and click the OK and Save Config buttons.

##### Change admin panel language
- Log in to your Admin Panel.
- Go to the System> All Users
- Click admin and navigate to Interface Locale drop-down menu
- Choose a desired language, click the Save User button and Flush Cache

> Note: see [change-default-language-in-magento-2](https://amasty.com/knowledge-base/change-default-language-in-magento-2.html.) 

### Errors
#### Unable to serialize value. Error: Malformed UTF-8 characters, possibly incorrectly encoded
If the deployment process throws the error _"Unable to serialize value. Error: Malformed UTF-8 characters, possibly incorrectly encoded"_, then you must modify the serialization json file, you can go look for it in our folder

```bash
cp Json.php ~/Sites/kuberaxpress-prod/src/vendor/magento/framework/Serialize/Serializer/
```

```bash
bin/copytocontainer vendor/magento/framework/Serialize/Serializer/Json.php
```
Then: 
```bash
bin/magento setup:static-content:deploy -f es_ES
```

## 8. References 

- https://www.mageplaza.com/magento-2-spanish-language-pack.html
- https://crowdin.com/project/magento-2

## Mageplaza extensions on Magento Marketplace, Github


- [Layered Navigation](https://marketplace.magento.com/mageplaza-layered-navigation-m2.html)
- [One Step Checkout](https://marketplace.magento.com/mageplaza-magento-2-one-step-checkout-extension.html)
- [SMTP](https://marketplace.magento.com/mageplaza-module-smtp.html) ; [SMTP on Github](https://github.com/mageplaza/magento-2-smtp)
- [Blog](https://github.com/mageplaza/magento-2-blog)
- [Security](https://marketplace.magento.com/mageplaza-module-security.html)
- [Social Login](https://github.com/mageplaza/magento-2-social-login)
- [SEO](https://github.com/mageplaza/magento-2-seo) ; [SEO on Marketplace](https://marketplace.magento.com/mageplaza-magento-2-seo-extension.html)
- [SMTP](https://github.com/mageplaza/magento-2-smtp)
- [Product Slider](https://github.com/mageplaza/magento-2-product-slider)
- [Banner](https://github.com/mageplaza/magento-2-banner-slider)
- [Sample Payment Method](https://github.com/mageplaza/magento-2-sample-payment-method)




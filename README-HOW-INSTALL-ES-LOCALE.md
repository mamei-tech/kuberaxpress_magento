## Magento 2 Spanish Language Pack

Magento 2 platform approves multiple languages around the world, so **Magento 2 Spanish Language Pack** is created to conduct the change of language via the in-line translation dictionary on Magento 2 store. The in-line translation dictionary is developed based on the community project at Crowdin where you can download over 12,000 phrases in Spanish to replace the default language. Magento 2 Spanish Language Package will involve the list of comprehensive guides which are essential for the perfect translation. Please keep tracking the topic to finish the interpretation at all.

Read more [Magento 2 Spanish Language Pack](https://www.mageplaza.com/magento-2-spanish-language-pack.html)

![Mageplaza Spanish language pack](https://cdn3.mageplaza.com/media/general/qjWPj1W.png)

## Overview

1. Language Package Process
2. Install Spanish Language Pack
3. How to active Spanish language pack
4. How to contribute
5. Supported Magento versions
6. Notes
7. Language package authors

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

#### How to change the language in Admin Panel Magento 2

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
### ✓ Method #2. Copy & Paste method (Not recommended)

This method suitable for non-technical people such as merchants. Just download the package then flush cache.

**Overview**

- Step 1: Download the Spanish language pack
- Step 2: Unzip Spanish pack
- Step 3: Flush Magento 2 Cache

#### Step 1 : Download the Spanish language pack

You can download the language pack from above link

#### Step 2: Unzip Spanish pack

Unzip the Spanish language pack to Magento 2 root folder. In this guide, we extract to `/var/www/html/`
Your Magento 2 root folder can be: `/home/account_name/yourstore.com/public_html/`

```
unzip master.zip app/i18n/Mageplaza/
```

Rename folder `magento-2-spanish-language-pack` to `es_es`.


You also can unzip locally and upload them to Magento 2 root folder.

#### Step 3: Flush Magento 2 Cache

Follow this guide to [Flush Cache on your Magento 2 store](https://www.mageplaza.com/kb/how-flush-enable-disable-cache.html)


### ✓ Method #3. Download and install manually (Not recommended)

To download and install Spanish pack manually, you have to access to your server via FTP or SFTP.

#### Step 1: Download the package

- [Download .zip](https://github.com/mageplaza/magento-2-spanish-language-pack/archive/master.zip)
- [Download .tar.gz](https://github.com/mageplaza/magento-2-spanish-language-pack/tarball/master)

#### Step 1: Unzip and upload

Unzip the compressed file and upload file `master.zip` into `app/i18n/Mageplaza/es_es/`

See this screenshot:

![Spanish pack](https://cdn3.mageplaza.com/media/general/language-pack.png)

This language pack code is: **es_es**

#### Step 2: Flush cache

Follow this guide to [Flush Cache on your Magento 2 store](https://www.mageplaza.com/kb/how-flush-enable-disable-cache.html)


## 3. How to Active the Spanish language pack 

Now time to active the Spanish language pack for your Magento 2 store. From Magento 2 admin panel, navigate to `Stores > Configuration > General > Locale Options`
![{{Magento 2 Spanish language pack}}](https://cdn.mageplaza.com/media/general/aPSUA0l.png)


## 4. How to contribute

Contribute to this language at :
- [On Crowdin](https://crowdin.com/project/magento-2): It takes time to approve your contribution by Magento team.
- [On Github](https://github.com/mageplaza/magento-2-spanish-language-pack/blob/master/HOW-TO-CONTRIBUTE.md): It's faster, our team will approve it after you send pull request.


## 5. Supported Magento versions

It supports all Magento 2 versions include [Magento 2 open-source](https://www.mageplaza.com/download-magento/) (Community), Magento 2 Commerce (EE), Magento Cloud, Magento B2B, Magento MSI.


- Magento v2.0.x
- Magento v2.1.x
- Magento v2.2.x
- Magento v2.3.x
- Magento v2.4.x



## 6. Notes 

- This project automatically updates weekly from Crowdin.
- Any question, issue please [create a new issue](https://github.com/mageplaza/magento-2-spanish-language-pack/issues/new)

## 7. Language package authors

- [Magento official translations project for Magento 2](https://crowdin.com/project/magento-2)
- Magento Community
- Language packages built by [Mageplaza team](https://www.mageplaza.com/)


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



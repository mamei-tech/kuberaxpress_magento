# kuberaxpress_magento
Magento code setup

## manual setup
### Create your project directory then go into it:
```bash
mkdir -p ~/Sites
```
```bash
cd $_
```

### Download the Docker Compose configs:
```bash
git clone https://github.com/mamei-tech/kuberaxpress_config.git kuberaxpress-prod
```

> Note: if dev environment run: git clone --branch dev https://github.com/mamei-tech/kuberaxpress_dockerconfigs.git kuberaxpress-dev

```bash
cd $_
```

```bash
docker compose -f compose.yaml up phpfpm -d
```

> Note: if dev environment run: `docker compose -f compose.dev.yaml -f compose.yaml up phpfpm -d`

```bash
git clone https://github.com/mamei-tech/kuberaxpress_magento.git src
```

> Note: if dev environment run: git clone --branch dev https://github.com/mamei-tech/kuberaxpress_magento.git src

### Magento core development:
 Start some containers, copy files to them and then restart the containers:
```bash
bin/start --no-dev
```

> Note: if dev environment run: `bin/start`

Initial copy will take a few minutes...
```bash
bin/copytocontainer --all
```

# If your vendor directory was empty, populate it with:
```bash
bin/composer install
```

```bash
bin/setup-composer-auth
```

### restore database

```bash
unzip ./backup/kubera.main.sql.zip
```

You can use the bin/mysql script to import a database:
```bash
bin/mysql < ./backup/kubera.main.sql
```

> Note: Update database connection details to use the above Docker MySQL credentials:
Also note: creds for the MySQL server are defined at startup from env/db.env
vi src/app/etc/env.php

Import app-specific environment settings:
```bash
bin/magento app:config:import
```

> Note: if you want to use a custom branch, run the following command:
```bash
bin/cli git checkout 2.4-develop
```

### Run the setup installer for Magento:

#### Install
```bash
bin/setup-install kuberaxpress.com
```

#### To create a DNS host entry and setup Magento base url
```bash
bin/setup-domain kuberaxpress.com
```

> Note: if dev environment run: `bin/setup-domain dev.kuberaxpress.com`

> Important: `bin/setup-install your_domain` 

open https://magento.test


## To set up multiple websites with Nginx

uncomment line three in `./images/Dockerfile`

### If modify `images/nginx/conf/default.conf`

```bash
git pull
docker-compose build
bin/restart
```

## Other commands

Generate a new certificate valid for the following names (ex: `kuberaxpress.com dev.kuberaxpress.com`)
```bash
bin/setup-ssl kuberaxpress.com dev.kuberaxpress.com
```

### Clean the Cache
```bash
bin/magento cache:flush
```

Run the following command to clean the config and full_page caches:
```bash
bin/magento cache:clean config full_page
```

# Take a backup of your existing database:
```bash
bin/mysqldump > ./backup/kubera.main.sql
```

## Docs

### Steps to access the admin for the first time without having email - 2fa

Install the Magento2-Module-DisableTwofactorah module:

```bash
bin/composer require markshust/magento2-module-disabletwofactorauth
bin/magento module:enable MarkShust_DisableTwoFactorAuth
bin/magento setup:upgrade
```

Disable 2FA in production mode:
```bash
bin/magento config:set twofactorauth/general/enable 0
```
> Note: desactivar el de production solo hasta configurar el email sender smtp, luego volver a activar. En developer mode si puedes dejarlo desactivado.  

To disable 2FA in developer mode run:
```bash
bin/magento config:set twofactorauth/general/disable_in_developer_mode 0
```

### Another via to access the admin for the first time without having email - 2fa

In case anyone needs a temporary workaround to get this working without having SMTP set up:

1. navigate to /admin and log in
2. you should see the 2FA screen now
3. add `var_dump($url);die;` on line 86 in `vendor/magento/module-two-factor-auth/Model/EmailUserNotifier.php`
4. refresh /admin
5. copy the URL that is displayed
6. remove the var_dump
7. use the URL copied earlier to navigate to the 2FA setup

### Install and configure Mail module (`https://github.com/mageplaza/magento-2-smtp`)

```bash
bin/composer require mageplaza/module-smtp
bin/magento setup:upgrade
bin/magento setup:static-content:deploy -f
```

#### To activate module

Activate the module once within the administration with the following data:
```text
register_name: kubera
register_email: admin@kuberaxpress.com
```

### Activate SMTP Auth Office 386

1. Disable smtp auth in your organization in the EAC
    - To disable SMTP AUTH globally in your organization in the EAC, go to the `Settings > Mail Flow` settings page and toggle the setting labeled Turn off SMTP AUTH protocol for your organization.
    - Follow the steps of this doc: https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/authenticated-client-smtp-submission#disable-smtp-auth-in-your-organization

2. In Magento admin
   - Go to the menu "Stores> Settings - Configuration> Store Email Addresses" and modify all sender email by `admin@kuberaxpress.com` and then `Save Config`

   - Go to the menu "Stores> Settings - Configuration" in the left lateral menu Go to the "Advanced > System" section and configure the "Mail Sending Settings" section similar to the steps above.

   - Go to the menu "Stores> SMTP - Configuration > SMTP Configuration Options" and load the __Office386__ default configuration in `Load Settings` button, then changes protocol to TLS and select LOGIN Authentication and add User and password from Email Office386. Then Send test email.

Then you can activate the 2FA for the Developer Mode and try it to see if you get the configuration mail.

### Set up multiple websites with Nginx
- https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-admin.html?lang=en
- https://experienceleague.adobe.com/docs/commerce-operations/configuration-guide/multi-sites/ms-nginx.html?lang=en

### Get and install your certificates with Certbot

#### Running the container
To run the Certbot container, execute the below script in your host machine:
```bash
script/setup-ssl-certbot
```

#### Automate Certificate Renewal
Certificates will only be valid for 90 days so we need to automate the renewal.
We setup our Cron job with:
```bash
crontab -e
```
We add the following line:
```text
0 3 * * mon /home/express/Sites/kuberaexpress/script/renew-ssl-certbot
```
This will execute the renew-ssl-certbot script every Monday at 3am.

### Disable a module
```bash
bin/magento module:disable a_module_name
```

### List of enabled modules
```bash
bin/magento module:status
```

### Remove a module

#### (Simple removal):
```bash
bin/composer remove module_name
```

#### Removing with Composer (complex):
```bash
bin/magento module:uninstall module_name
```

### Manual static content deployment
```bash
bin/magento setup:static-content:deploy -f
```

### To generate classes
```bash
bin/magento setup:di:compile
```

### Errors

If you use version `2.4.6-p3` or Magento higher you must install this module to be able to send SMTP emails:
```bash
bin/composer require laminas/laminas-zendframework-bridge:1.8.0
```

#### docs
- https://blog.jarrousse.org/2022/04/09/an-elegant-way-to-use-docker-compose-to-obtain-and-renew-a-lets-encrypt-ssl-certificate-with-certbot-and-configure-the-nginx-service-to-use-it/
- https://phoenixnap.com/kb/letsencrypt-docker
- (*) https://medium.com/@hugodelatte/configuring-an-https-server-with-nginx-and-certbot-d3abe6121af7
- https://github.com/mageplaza/magento-2-smtp
- https://www.courier.com/guides/magento-notifications/
- https://www.mgt-commerce.com/tutorial/magento-2-factor-authentication/
- https://mirasvit.com/knowledge-base/how-to-remove-magento-2-extension.html

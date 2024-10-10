
# Updates
Backup your files and database before starting the update process.

To update your project to the latest version of docker-magento, run:
```bash
bin/update
```
Remember to modify the docker-dev.yaml back to the previous state. After reviewing the code updates and ensuring 
they updated as intended, run `bin/restart` to restart your containers to have the new configuration take effect.

```bash
bin/restart
```
- Update the Composer dependencies to the latest Magento version:
```bash
bin/composer require magento/product-community-edition=2.4.7-p2 --no-update
bin/composer update
```
- Run Magento's upgrade commands:
```bash
bin/magento setup:upgrade
bin/magento cache:flush
bin/magento setup:di:compile
bin/magento setup:static-content:deploy -f
```

You can know the version of Magento by running the following command:
```bash
bin/magento-version
```

Possible errors:

You need to manually modify your composer.json file to specify the new version, then run a `composer update` command 
within the container, followed by necessary Magento upgrade commands to apply the changes to your database and static 
content; remember to back up your data before updating. 

Modify the "magento/product-community-edition": "2.4.6-p2" line in `require` to version `2.4.7-p2`.
Modify the "symfony/process": "version" line in `require-dev` to version `^6.4`.

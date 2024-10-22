
# Installation

Magento2 Marketplace Multi Seller module installation is very easy, please follow the steps for installation.

## Install marketplace module
Remember to use the correct version of the module
You can know the version of Magento by running the following command:
```bash
bin/magento-version
```

1. Unzip the respective extension zip.
```bash
unzip magento2_marketplace-hash_number_2.4.x-5.0.8-p1
```
2. Then move "app" folder (inside "src" folder) into magento root directory.
```bash
cp -R magento2_marketplace-hash_number_2.4.x-5.0.8-p19/magento2_marketplace-hash_number/src/* kuberaxpress-prod/src/
```

```bash
cd kuberaxpress-prod/
```

```bash
bin/copytocontainer app/code/Webkul
```

Run Following Command via terminal
-----------------------------------
```bash
bin/magento setup:upgrade 
bin/magento setup:di:compile
bin/magento setup:static-content:deploy
bin/magento queue:consumers:start admin.news.published &
bin/magento queue:consumers:start seller.product.lowstock &
```

Flush the cache and reindex all.
```bash
bin/magento indexer:reindex && bin/magento cache:clean && bin/magento cache:flush
```


# Possible errors:

# docs
https://webkul.com/blog/magento2-multi-vendor-marketplace/
https://webkul.com/blog/magento2-marketplace-seller-central/
https://marketplace.webkul.com/knowledgebase/assign-products-to-the-seller/#:~:text=Select%20the%20seller%20from%20the,list%20and%20save%20the%20configuration.

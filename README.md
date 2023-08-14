# Magento 2 installation guide
My own version of setting up Magento 2 to local machine.

> In this guide, we will be installing the Magento 2 community edition - version 2.4.6-p2 (but this setup also works with 2.4.x)

## Versions
* Magento 2.4.6-p2
* Elasticsearch 7.17.0
* MySQL/MariaDB 10.x

1. Go to -> https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/composer.html
2. Complete the Prerequisites
     * Complete all [prerequisite tasks](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/system-requirements.html?lang=en).
     * [Install Composer](https://getcomposer.org/download/)
     * Get [authentication keys](https://experienceleague.adobe.com/docs/commerce-operations/installation-guide/prerequisites/authentication-keys.html?lang=en) to the Adobe Commerce and Magento Open Source Composer repository.
3. Get the meta package using this command: `composer create-project --repository-url=https://repo.magento.com/ magento/project-community-edition <install-directory-name>`
4. Install Elasticsearch locally using docker. Follow this [guide](https://www.elastic.co/guide/en/elasticsearch/reference/current/run-elasticsearch-locally.html#run-elasticsearch-locally)
   - make sure to change the Elasticsearch version `8.9.0` to `7.17.0`
5. Run install command:
   ```
   bin/magento setup:install --base-url=http://localhost:4040 --backend-frontname=admin --db-host=127.0.0.1 --db-name=mage --db-user=root --db-password= --admin-firstname=admin --admin-lastname=admin --admin-email=admin@admin.com --admin-user=admin --admin-password=admin123 --language=en_US --currency=USD --timezone=Europe/Amsterdam --use-rewrites=1 --search-engine=elasticsearch7 --elasticsearch-host=127.0.0.1 --elasticsearch-port=9200
   ```
6. Done 🎉🎉🎉
7. Bonus
   - Install sample data using the command below
   - ```bin/magento sampledata:deploy```
   - Note: you might encounter memory limit error, just prepend this to the command above: ```php -d memory_limit=-1``` so the final command looks like this: ```php -d memory_limit=-1 bin/magento sampledata:deploy```
  
8. Run upgrade command
   - ```bin/magento setup:upgrade``` * again when memory limit error comes up just use the above command
  
<br/>
 

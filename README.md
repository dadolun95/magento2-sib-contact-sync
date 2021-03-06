# Sendinblue Magento2 Module

### Dadolun_SibContactSync

## Features
Contact Syncronization functionality for Sendinblue - Magento2 integration.

This module sync all your Magento2 subscribers to Sendinblue.

These are the default built in contact attributes:
- FIRSTNAME
- LASTNAME
- MAGENTO_LANG
- CLIENT (subscribed customer only)
- COMPANY (subscribed customer only)
- CITY (subscribed customer only)
- COUNTRY_ID (subscribed customer only)
- POSTCODE (subscribed customer only)
- STREET (subscribed customer only)
- REGION (subscribed customer only)
- STORE_ID (subscribed customer only)


Double optin and email confirmation are demanded to Magento2 (Different behavior from the official module).


## Installation
You can install this module adding it on app/code folder or with composer.
##### COMPOSER
###### REPMAN.IO (Preferred)
Add Dadolun_Sib repman organization access token on composer:
```
composer config --global --auth http-basic.dadolun_sib.repo.repman.io token e8d9440ca95f7a67c6c70cce55a2352322b89e2fc8c1c7391cd9052578aa6e77
```
Add a "repositories" node on your composer.json:
```
{
    "type": "composer", 
    "url": "https://dadolun_sib.repo.repman.io"
}
```
Execute this command:
```
composer require dadolun95/magento2-sib-order-sync
```
###### VCS 
Same result specifing VCS type nodes on repositories section:
```
{
    "type": "vcs",
    "url":  "git@github.com:dadolun95/magento2-sib-core.git"
},
{
    "type": "vcs",
    "url":  "git@github.com:dadolun95/magento2-sib-contact-sync.git"
},
{
    "type": "vcs",
    "url":  "git@github.com:dadolun95/magento2-sib-order-sync.git"
}
```
```
composer require dadolun95/magento2-sib-order-sync
```
##### MAGENTO
Then you'll need to enable the module and update your database:
```
php bin/magento module:enable Dadolun_SibCore
php bin/magento module:enable Dadolun_SibContactSync
php bin/magento module:enable Dadolun_SibOrderSync
php bin/magento setup:upgrade
php bin/magento setup:di:compile
```

##### CONFIGURATION
You must enable the contact sync from "Stores > Configurations > Dadolun > Sendinblue > Contact Sync" section.
The module provides a "Sync contact" CTA on adminhtml that move all existing contacts to Sendinblue (only new subscribers are synced on runtime).
Since sync functionality is enabled two Sendinblue lists are created:
- [Magento Optin Form] > Temp - DOUBLE OPTIN (contacts that need confirmation are moved here temporarely)
- [magento] > subscriptions

## Contributing
Contributions are very welcome. In order to contribute, please fork this repository and submit a [pull request](https://docs.github.com/en/free-pro-team@latest/github/collaborating-with-issues-and-pull-requests/creating-a-pull-request).

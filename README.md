# Lelo Content Migration System

Lelo content migration system is a system to migrate the content upstream (e.g. from test to production). It is a Drupal 8 configuration system.

Since there are often a lot of landing pages or product pages that are needed to be build on a dev/test environment, a lot of time is used by the content editors.This module would help the content editor team by saving hours of rework.
 
## Installation

* Install composer 

```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
php -r "if (hash_file('sha384', 'composer-setup.php') === '756890a4488ce9024fc62c56153228907f1545c228516cbf63f885e036d37e9a59d27d63f46af1d4d07ee0f76181c7d3') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
php composer-setup.php
php -r "unlink('composer-setup.php');"
```
* Download the files from this repo and put them in a directory. 
```
git clone https://github.com/devrushi/lelo_dev_test_rushikesh.git master
cd master
composer install
````
* Local Test server and local Live client creation.

I have used Acquia Dev Desktop as it is the quickest way to configure and run Drupal for local development.

### Local Live client setup
1. Download the acquia dev desktop https://dev.acquia.com/downloads and install the application.
1. Select an option ```Start with an existing Drupal site located on my computer``` from the dialog box.
1. A new dialog box will open where you can select the project folder and navigate to the ```master/web``` folder inside the main project directory and click on open.
1. By default the local site name will be web (as the folder name we selected) but users can change it as per preference.
1. Select the database option ```Create a new database``` for the first installation and it will be named similar local site name (step 4).
1. Click okay and the main screen of the application will be displayed and click on the local site link provided which will be redirected to the browser and the Drupal setup will start.


* Drupal interactive installer

1. Select the language option.
1. Select the profile (```standard``` profile has the commonly used features pre-configured).
1. This is automated as we have already specified the database configuration in Acquia dev application.
1. After installation process is successfully completed the next step is the site configuration step where the user needs to add the site name and email id for notification regarding the site status, username and password to access the drupal site. Lastly the regional settings and notification settings and click on save and continue.

The user will be redirected to the newly created drupal website.

* Database dump

Go to Acquia dev desktop application and click on the local database link which will be redirected to the ```phpMyAdmin``` on localhost and follow the below instructions.
1. Select the database name from the list on the left hand side.
1. Verify once the selected database is correct and navigate to the ```Export``` section and click on the 'Go' button and a ```databaseName.sql``` dump file will be downloaded(this will be needed for the local test server).    

### Local test server setup

* Download the files from this repo and put them in a directory. 
```
git clone https://github.com/devrushi/lelo_dev_test_rushikesh.git master
cd master
composer install
```

 Repeat 2nd, 3rd and the 4th step.

5.Select the database option ```Start with MySQL database dump file``` and it will provide an option to browse select the dump ```databaseName.sql``` file (the dump file generated from phpMyAdmin).

6.Click okay and the main screen of the application will be displayed and click on the local site link provided which will be redirected to the browser and the Drupal setup will start.

* Drupal interactive installer will automaticaly set the new site and the ``` user login details ``` are same for the sites.

## Module Configuration
### Entity Share Module.

* Module installation for ```Local Live Client```  
  1. In the cloned directory search for ```entity_share-8.x-2.0-alpha12.tar.gz``` file.
  1. Login to the ```Local Live Client``` site and navigate to ```Extend``` tab on the top of the site.
  1. On the ```Extend``` page click on ```+ Install new module``` button.
  1. On the ```Install new module``` page click on ```Choose file``` button inside the text box and select the ```entity_share-8.x-2.0-alpha12.tar.gz``` file.
  1. On successfull installation of the module navigate to the  ```Extend``` page ```WEB SERVICES``` section. To activate the module there are two options
      * UI option -  click on the selection box of  ```Entity share``` and ```Entity share client``` (as this is a client site).
      * Drush option - Open the project directory in the ```Terminal``` and run  ```drush en entity_share_client``` command (as this is a client site).    
  
* Module configuration for ```Local Live Client```  
  1. In the ```Local Live Client``` site navigate to ```Configuration``` tab on the top of the site.
  1. On the ```Configuration``` page navigate to the ```WEB SERVICES``` section and click on ```Entity share```.
  1. On the ```Entity share``` page click on ```Remote websites``` link.
  1. On the ```Remote``` page click on ```+ Add new website``` button.
  1. On the ```Add remote``` page enter following details
      * ```Label``` - enter descriptive label for the remote website e.g ```Server -> Client``` as it directs the data flow.
      * ```URL``` - enter the server site e.g ```http://local-test-server.dd:8083/```  or ```http://localhost:8888/```.
      * ```BASIC AUTH``` - enter the ```Username``` and ```Password``` credentials.
    and click on ```Save``` button.  
  1. On successfull addition of the remote website details the ```Remote``` page will display the newly added item with preiviously added sites (if any added). 

* Module Installation for ```Local Test Server```  
  1. Login to the ```Local Test Server``` site and navigate to ```Extend``` tab on the top of the site.
  1. On the ```Extend``` page click on ```+ Install new module``` button.
  1. On the ```Install new module``` page click on ```Choose file``` button inside the text box and select the ```entity_share-8.x-2.0-alpha12.tar.gz``` file.
  1. On successfull installation of the module navigate to the  ```Extend``` page ```WEB SERVICES``` section. To activate the module there are two options
      * ```UI option``` -  click on the selection box of  ```Entity share``` and ```Entity share server``` (as this is a server site).
      * ```Drush option``` - Open the project directory in the ```Terminal``` and run  ```drush en entity_share_server``` command (as this is a server site).   
  
* Module configuration for ```Local Test Server```  
  1. In the ```Local Test Server``` site navigate to ```Configuration``` tab on the top of the site.
  1. On the ```Configuration``` page navigate to the ```WEB SERVICES``` section and click on ```Entity share```.
  1. On the ```Entity share``` page click on ```Channels``` link.
  1. On the ```Channel``` page click on ```+ Add Channel``` button.
  1. On the ```Add channel``` page enter following details
      * ```Label``` - enter descriptive label for the channel e.g ```Basic page channel``` as it instructs the use of the channel.
      * ```Entity type``` - select from the list of entity types e.g ```Content```, ```Product```, ```Media```, etc.
      * ```Bundle``` - list is generated on selection of entity types.
      * ```Authorized users``` - list of users will be displayed for selection (this is important field as it needs authorized user for data migration).
    and click on ```Save``` button.  
  1. On successfull addition of the channel details the ```Channel``` page will display the newly added item with preiviously added channels (if any added). 
  
  Repeat the 5th step to add channels as per requirement.
  
### Commerce Module.
* Module installation for both ```Local Live Client``` and  ```Local Test Server```
  1. Login to the site and navigate to ```Extend``` tab on the top of the site.
  1. On the ```Extend``` page navigate to ```Commerce``` section and select all the checkboxes in this section.
    
    and click install.

  
### Media Module.
* Module installation for both ```Local Live Client``` and  ```Local Test Server```
  1. Login to the site and navigate to ```Extend``` tab on the top of the site.
  1. On the ```Extend``` page navigate to ```Core``` section and select the ```Media``` and ```Media Library``` checkboxes.
    
    and click install.

* Module configuration for both ```Local Live Client``` and  ```Local Test Server```
  1. Login to the site and navigate to ```Configuration``` tab on the top of the site.
  1. On the ```Configuration``` page navigate to ```CONTENT AUTHORING``` section and click on the ```Text formats and editors``` link.
  1. On the ```Text formats and editors``` page navigate to ```Basic HTML``` item and click on the ```Configure``` button.
  1. On the ```Basic HTML``` page navigate to ```TOOLBAR CONFIGURATION``` section and drag and drop ```Media icon with sound note``` from ```Available buttons``` to ```Active toolbar```.
  1.On the same page Navigate to ```Enabled filters``` section and select the ```Embed media``` checkbox. 
    
    and click on ```Save configuration```.
    
## Module Usage
 The ```Entity share module``` is a cost effective solution to manage multisite content developed by Drupal orginsation.
 
 So as mentioned at the beginning this module is created to migrate the content upstream which means the data flows from Test Server site to Live Client site.
 
 Following are the instructions of the module usage
 * ```Local Test Server``` - Data is created and tested here and sent to Live Client.
 1. Using the Module configuration steps configure channels for ```Article```, ```Basic page```, ```Comments```, ```Product``` and ```Media/Image```.
 1. Next thing is to generate the content for each content type of which channels are created. 
   Repeat the 2nd step for creation of new content or updation of old content.
   
  * ```Local Live Server``` - Tested data is received from the Test Server
 1. In the ```Local Live Client``` site navigate to ```Content``` tab on the top of the site. 
 1. On the ```Content``` page navigate to ```Entity share``` tab located below the page header.
 1. On the ```Entity share``` section the ```Remote webiste``` option is already selected as it is already configured.
 1. Next option is to select the ```Channel``` from the list which were configured on local Test server.
 1. After seleting the ```Channel``` the live server pulls data through JSON API and displays the list of item for that perticular channel.
 1. The list displays the item with few details of content type, last updated timestamp and status.
    Status for the new ones is ```New entity``` in green background and if the item has been updated from the remote website it will display ```Entities not synchronized``` in red background. 
 3. Final step is to select the desired items and click on ```Synchronize entities``` button and the data will be updated.  
 
 

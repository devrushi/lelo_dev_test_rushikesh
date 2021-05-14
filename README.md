# Lelo Content Migration System

Lelo content migration system is to migrate the content upstream (e.g. from test to production). 
* It is on the Drupal 8 configuration system. 
* It uses the Entity Share module.
* Entity Share module is developed and maintained by Drupal organization and it compatible with Drupal 8 and 9.
* Entity Share module uses JSON:API endpoints to transfer data in a secured way to only authorised users.
* This module helps clients to achieve a workflow where they can share a piece of content across multi sites without disrupting the workflow.
* It also provides a UI for data synchronization and status tracking.

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 1.0 Data flow in the module

This module is created to migrate the content upstream which means the data flows from Test Server site to Live Client site through various content type channels.
Since there are often a lot of landing pages or product pages that are needed to be built on a dev/test environment, a lot of time is used by the content editors.This module would help the content editor team by saving hours of rework and due to this it is very cost effective.


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
1. Download the acquia dev desktop https://dev.acquia.com/downloads and install the application and select an option ```Start with an existing Drupal site located on my computer``` from the dialog box.

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 2.0 Welcome screen of Acquia Dev Desktop

2. A new dialog box will open where you can select the local project folder and navigate to the ```master/web``` folder inside the main project directory and click on open.

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 3.0 Import local folder screen

3. By default the local site name will be web (as the folder name we selected) but users can change it as per preference.

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 4.0 Local site name

4. Select the database option ```Create a new database``` for the first installation and it will be named with a similar local site name.

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 5.0 Database selection

5. Click okay and the main screen of the application will be displayed and click on the local site link provided which will be redirected to the browser and the Drupal setup will start.

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 6.0 Local site link

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 6.1 Drupal setup screen


* Drupal interactive installer

1. Select the language option (refer Fig 6.1 ).
2. Select the profile (```standard``` profile has the commonly used features pre-configured).

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 7.0 Profile selection screen

3. This is automated as we have already specified the database configuration in Acquia dev application.

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 8.0 Database set up and installation

4. After the installation process is successfully completed the next step is the site configuration step where the user needs to add the site name and email id for notification regarding the site status, username and password to access the drupal site. Lastly the regional settings and notification settings and click on save and continue.

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 9.0 Site Configuration screen

The user will be redirected to the newly created drupal website.

* Database dump

Go to Acquia dev desktop application and click on the local database link which will be redirected to the ```phpMyAdmin``` on localhost and follow the below instructions.

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 10.0 Local database manager link
1.Select the database name from the list on the left hand side.

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 11.0 Correct database selection.

2.Verify once the selected database is correct and navigate to the ```Export``` section and click on the 'Go' button and a ```databaseName.sql``` dump file will be downloaded(this will be needed for the local test server). 

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 12.0 Database export process

### Local test server setup

* Download the files from this repo and put them in a directory. 
```
git clone https://github.com/devrushi/lelo_dev_test_rushikesh.git master
cd master
composer install
```

 Repeat 2nd, 3rd and the 4th step.

5.Select the database option ```Start with MySQL database dump file``` and it will provide an option to browse select the dump ```databaseName.sql``` file (the dump file generated from phpMyAdmin).

![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

Fig 13.0 Selection of dump database file


6.Click okay and the main screen of the application will be displayed and click on the local site link provided which will be redirected to the browser and the Drupal setup will start.


* Drupal interactive installer will automaticaly set the new site and the ``` user login details ``` are same for the sites.

## Module Configuration

### Entity Share Module.

* Module installation for ```Local Live Client```.  
  1. In the cloned directory search for ```entity_share-8.x-2.0-alpha12.tar.gz``` file.
  
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)

  Fig 14.0 Entity Share module .gz file location
  
  2. Login to the ```Local Live Client``` site and navigate to ```Extend``` tab on the top of the site.
  
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  
  Fig 15.0 Extend tab 

  4. On the ```Extend``` page click on ```+ Install new module``` button.
  
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  
  Fig 16.0 Install new module
  
  6. On the ```Install new module``` page click on ```Choose file``` button inside the text box and select the ```entity_share-8.x-2.0-alpha12.tar.gz``` file.
  
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  Fig 17.0 Entity Share file selection
  
  8. On successfull installation of the module navigate to the  ```Extend``` page ```WEB SERVICES``` section. To activate the module there are two options
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  Fig 18.0 Successful installation
  
      * UI option -  click on the selection box of  ```Entity share``` and ```Entity share client``` (as this is a client site).
     ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
      Fig 18.1 UI option (a)
      
      * Drush option - Open the project directory in the ```Terminal``` and run  ```drush en entity_share_client``` command (as this is a client site).  
     ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
      Fig 18.2 Terminal Drush option (b) 
  
* Module configuration for ```Local Live Client```  
  1. In the ```Local Live Client``` site navigate to ```Configuration``` tab on the top of the site.
  2. On the ```Configuration``` page navigate to the ```WEB SERVICES``` section and click on ```Entity share```.
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  Fig 19.0 Configuration page


  3. On the ```Entity share``` page click on ```Remote websites``` link.
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  Fig 20.0 Entity share page
  
  4. On the ```Remote``` page click on ```+ Add remote website``` button.
 ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  Fig 21.0 Add remote website
  
  5. On the ```Add remote``` page enter following details
      * ```Label``` - enter descriptive label for the remote website e.g ```Server -> Client``` as it directs the data flow.
      * ```URL``` - enter the server site e.g ```http://local-test-server.dd:8083/```  or ```http://localhost:8888/```.
      * ```BASIC AUTH``` - enter the ```Username``` and ```Password``` credentials.
      
     ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
     
    Fig 22.0 Remote website details (a),(b) and(c)
    
    and click on ```Save``` button.  
    
  6. On successfull addition of the remote website details the ```Remote``` page will display the newly added item with preiviously added sites (if any added). 
   
   
![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 23.0 List of added sites

* Module Installation for ```Local Test Server```  
  1. Login to the ```Local Test Server``` site and navigate to ```Extend``` tab on the top of the site.( refer to Fig 15.0 )
  1. On the ```Extend``` page click on ```+ Install new module``` button.( refer to Fig 16.0 )
  1. On the ```Install new module``` page click on ```Choose file``` button inside the text box and select the ```entity_share-8.x-2.0-alpha12.tar.gz``` file.( refer to Fig 17.0 )
  1. On successfull installation of the module navigate to the  ```Extend``` page ```WEB SERVICES``` section. To activate the module there are two options
      * ```UI option``` -  click on the selection box of  ```Entity share``` and ```Entity share server``` (as this is a server site).
      ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
      Fig 24.0 UI option (a)
      * ```Drush option``` - Open the project directory in the ```Terminal``` and run  ```drush en entity_share_server``` command (as this is a server site).   
      ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
      Fig 24.1 Terminal Drush option (b) 
  
* Module configuration for ```Local Test Server```  
  1. In the ```Local Test Server``` site navigate to ```Configuration``` tab on the top of the site.
  2. On the ```Configuration``` page navigate to the ```WEB SERVICES``` section and click on ```Entity share``` link.
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
   Fig 25.0 Configuration screen
  3. On the ```Entity share``` page click on ```Channels``` link.
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  Fig 26.0 Entity Share page
  4. On the ```Channel``` page click on ```+ Add Channel``` button.
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  Fig 27.0 Channel page
  5. On the ```Add channel``` page enter following details
      * ```Label``` - enter descriptive label for the channel e.g ```Basic page channel``` as it instructs the use of the channel.
      * ```Entity type``` - select from the list of entity types e.g ```Content```, ```Product```, ```Media```, etc.
      * ```Bundle``` - list is generated on selection of entity types.
      * ```Authorized users``` - list of users will be displayed for selection (this is important field as it needs authorized user for data migration).
   ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
   Fig 28.0 Channel detials (a), (b),(c ) and (d)
    and click on ```Save``` button.  
  6. On successfull addition of the channel details the ```Channel``` page will display the newly added item with preiviously added channels (if any added). 
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  Fig 29.0 List of channels
  Repeat the 5th step to add channels as per requirement.
  
### Commerce Module.
* Module installation for both ```Local Live Client``` and  ```Local Test Server```
  1. Login to the site and navigate to ```Extend``` tab on the top of the site.
  1. On the ```Extend``` page navigate to ```Commerce``` section and select all the checkboxes in this section.
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
   Fig 30.0 Commerce module 
    and click install.

  
### Media Module.
* Module installation for both ```Local Live Client``` and  ```Local Test Server```
  1. Login to the site and navigate to ```Extend``` tab on the top of the site.
  1. On the ```Extend``` page navigate to ```Core``` section and select the ```Media``` and ```Media Library``` checkboxes.
    ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
    Fig 31.0 Media module
    and click install.

* Module configuration for both ```Local Live Client``` and  ```Local Test Server```
  1. Login to the site and navigate to ```Configuration``` tab on the top of the site.
  2. On the ```Configuration``` page navigate to ```CONTENT AUTHORING``` section and click on the ```Text formats and editors``` link.
![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 32.0 Content Authoring section

  3. On the ```Text formats and editors``` page navigate to ```Basic HTML``` item and click on the ```Configure``` button.
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
  Fig 33.0 Basic HTML 
  5. On the ```Basic HTML``` page navigate to ```TOOLBAR CONFIGURATION``` section and drag and drop ```Media icon with sound note``` from ```Available buttons``` to ```Active toolbar```.
  6.On the same page Navigate to ```Enabled filters``` section and select the ```Embed media``` checkbox. 
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
    Fig 34.0 Media configuration
    and click on ```Save configuration```.
    
## Module Usage
 
 Following are the instructions of the module usage
 * ```Local Test Server``` - Data is created and tested here and sent to Live Client.
 1. Using the Module configuration steps configure channels for ```Article```, ```Basic page```, ```Comments```, ```Product``` and ```Media/Image```.
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
 Fig 35.0 List of channels for testing
 2. Next thing is to generate the content for each content type of which channels are created. 
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 36.0 Article channel content
  ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 36.1 Comment channel content
 ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 36.2 Basic channel content
 ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 36.3 Product channel and Image channel content
   Repeat the 2nd step for creation of new content or updation of old content.
   
  * ```Local Live Server``` - Tested data is received from the Test Server
 1. In the ```Local Live Client``` site navigate to ```Content``` tab on the top of the site. 
 2. On the ```Content``` page navigate to ```Entity share``` tab located below the page header.
![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 37.0 Content > Entity Share section

 3. On the ```Entity share``` section the ```Remote webiste``` option is already selected as it is already configured.
![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 38.0 Remote website

 4. Next option is to select the ```Channel``` from the list which were configured on local Test server.
 ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
 Fig 39.0 Channel selection
 5. After seleting the ```Channel``` the live server pulls data through JSON API and displays the list of item for that perticular channel.
![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 40.0 New received data from test server
 6. The list displays the item with few details of content type, last updated timestamp and status.
    Status for the new ones is ```New entity``` in green background and if the item has been updated from the remote website it will display ```Entities not synchronized``` in red background. 
    ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
    Fig 41.0 Synchronized state.
![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 41.1 Not Synchronized state
 7. Final step is to select the desired items and click on ```Synchronize entities``` button and the data will be updated.  
 
 ![alt text](https://github.com/devrushi/lelo_dev_test_rushikesh/blob/master/EntityShareModule.png?raw=true)
Fig 42.0 Processing after clicking the button 

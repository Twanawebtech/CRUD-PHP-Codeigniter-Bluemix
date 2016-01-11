###################
Deploy to Bluemix simple CRUD application using PHP and codeigniter
###################

PHP developers still spend a lot of time configuring systems and servers to get a PHP application up and running. PHP developers usually go through this lifecycle every time starting a project. Luckily, there are services out there that take all this grunt work out of creating web applications, such as IBM Bluemix.

In this tutorial, we’ll create a web application with a simple Create, Read, Update and delete (CRUD) functionality. We will use  PHP as the runtime and codeigniter as our framework, we will then bind the application to the database using the ClearDB MySql service on Bluemix and and deploy it to Bluemix.

By the end of our tutorial, our web app will provide a very basic way toCreate, Read, Update and delete blogs and you will learn how to push a PHP codeigniter application to Bluemix and how to setup the services on IBM Bluemix. You will also learn the changes to make to your application when moving your data from local environment to Bluemix. CRUD application will be looking like this:



###################
Steps involves 
###################

Using the cloud foundry command line, login to Bluemix and navigate to the organization and space you want to push your app too.
-> cf login
-> Enter your Bluemix email and password, then navigate to your org and space which you want
Create the database service on Bluemix, in this example we are using the ClearDB MySql service. 

-> cf create-service cleardb spark myDatabaseCRUD
Download the source code from GitHub and rename the folder to a unique application name in which you want your application to be called. For my example I called my application "CRUD-PHP-Codeigniter-Bluemix".
Edit the "manifest.yml" file to update the application name which in my case is "CRUD-PHP-Codeigniter-Bluemix" and the database service name which in my case been called "myDatabaseCRUD", after that we are good to go to push our application to Bluemix. (The manifest.yml is a file which holds all the Bluemix configurations listing all the services and application setup).
To push your application to bluemix, we need to inside the application directory so navigate to that folder.
-> cd desktop/CRUD-PHP-Codeigniter-Bluemix
Push the applications to Bluemix, to do that use below command
-> cf push CRUD-PHP-Codeigniter-Bluemix -b https://github.com/cloudfoundry/php-buildpack -s cflinuxfs2
Now that our application is pushed to bluemix, we need to one final step for our application to work, we need to create a database in which our PHP application is looking for. To access our MySql database, first we need to get the database details, to do that run this command to get your database details.
-> cf env CRUD-PHP-Codeigniter-Bluemix
Or you can get the database details via Bluemix dashboard, to get the database details via Bluemix dashboard login to your Bluemix and open your applications which we created and click on the "Show Credentials" button under the MySql Database service.


Once you got the database details, use any database management tool to login to the database and create the table and fields, in my case I am using SequelPro to access the database.


To create the database table and fields, run below script to create the database:

CREATE TABLE `bloginfo` (
 `id` int(11) NOT NULL AUTO_INCREMENT,
 `created_date` date DEFAULT NULL,
 `title` varchar(100) DEFAULT NULL,
 `description` text,
 `image` varchar(150) DEFAULT NULL,
 PRIMARY KEY (`id`)
) ENGINE=InnoDB AUTO_INCREMENT=272 DEFAULT CHARSET=latin1;


We should now be in action, access your application staging domain, in my case been: `http://crud-php-codeigniter-bluemix.mybluemix.net/`_ - Enjoy!

If you have any questions or need support then contact me or leave a comment below.


###################
Whats next?
###################

On our next article we will bind a storage service to our application to store images and files.




###################
What is CodeIgniter
###################

CodeIgniter is an Application Development Framework - a toolkit - for people
who build web sites using PHP. Its goal is to enable you to develop projects
much faster than you could if you were writing code from scratch, by providing
a rich set of libraries for commonly needed tasks, as well as a simple
interface and logical structure to access these libraries. CodeIgniter lets
you creatively focus on your project by minimizing the amount of code needed
for a given task.

*******************
Release Information
*******************

This repo contains in-development code for future releases. To download the
latest stable release please visit the `CodeIgniter Downloads
<http://www.codeigniter.com/download>`_ page.

**************************
Changelog and New Features
**************************

You can find a list of all changes for each release in the `user
guide change log <https://github.com/bcit-ci/CodeIgniter/blob/develop/user_guide_src/source/changelog.rst>`_.

*******************
Server Requirements
*******************

PHP version 5.4 or newer is recommended.

It should work on 5.2.4 as well, but we strongly advise you NOT to run
such old versions of PHP, because of potential security and performance
issues, as well as missing features.

************
Installation
************

Please see the `installation section <http://www.codeigniter.com/user_guide/installation/index.html>`_
of the CodeIgniter User Guide.

*******
License
*******

Please see the `license
agreement <https://github.com/bcit-ci/CodeIgniter/blob/develop/user_guide_src/source/license.rst>`_.

*********
Resources
*********

-  `User Guide <http://www.codeigniter.com/docs>`_
-  `Language File Translations <https://github.com/bcit-ci/codeigniter3-translations>`_
-  `Community Forums <http://forum.codeigniter.com/>`_
-  `Community Wiki <https://github.com/bcit-ci/CodeIgniter/wiki>`_
-  `Community IRC <http://www.codeigniter.com/irc>`_ 

Report security issues to our `Security Panel <mailto:security@codeigniter.com>`_, thank you.

***************
Acknowledgement
***************

The CodeIgniter team would like to thank EllisLab, all the
contributors to the CodeIgniter project and you, the CodeIgniter user.

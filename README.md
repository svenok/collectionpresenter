# collectionpresenter
A		***************************
		*   Collection Presenter  *
		*    ----------------     *
		*    THE INSIDE VIEW      *
		***************************
										
This is the manual, configuration guide and installation instruction to The
Collection Presenter -- a collection presentation system for natural history 
collections.

Sven O Kullander
						
2009				 
Version 1.0. revision 19 (2010)
								
Copyright (c) 2007-present  Sven O Kullander.
Permission is granted to copy, distribute and/or modify this document
under the terms of the GNU Free Documentation License, Version 1.2
or any later version published by the Free Software Foundation;
with no Invariant Sections, no Front-Cover Texts, and no Back-Cover Texts.
This manual is distributed with The Web Artedian software, and a copy 
of the License should be included with the distribution. 

=====================================================================
CONTENTS

ISSUES
REVISION HISTORY
COPYRIGHT AND LICENSE 
GENERAL
OPERATING SYSTEM
DATABASE BACKEND 
WEB SERVER  
SCRIPTING
DEPENDENCIES      
CONFIGURATION      
MULTIPLE INSTANCES    
THE CONFIGURATION FILE  
CUSTOMIZE DISPLAY
THE LOCALISATION FILE
GOOGLE MAPS CONFIGURATION
OPTIONAL LANGUAGES MANAGEMENT
THE DATABASE CONNECTION FILE
THE COUNTER
SERVER FILES vs. INCLUDE FILES 
FPDF
RSS FILE	
IMAGES
ICONS					
THE COMMENTS PAGE          
DATABASE PRIVILEGES 
THE TABLES (for version 1.0)
FILE LIST		
=====================================================================		
		
		

***************************
*   Collection Presenter  *
***************************

Current version
v.07beta16

9 February 2010


***************************
*        ISSUES           *
***************************

1. In some multi-image displays, headers do not display correctly

***************************
*   REVISION HISTORY      *
***************************

_v.07beta17 24 April 2010_
Added option to plot only field numbers on Google Maps (implemented for expeditions)
Google Maps now zoom to bounds of markers

_v.07beta16 8 February 2010_
Bugfix: corrected code in wa_kmlfile.inc, to restore Google Earth functionality (this was not properly done in 07beta15)

_v.07beta15 7 February 2010_
Bugfix: changed Swedish language code from se to sv
Bugfix: corrected code in wa_kmlfile.inc, to restore Google Earth functionality

_v.07beta14 16 January 2010_
Bugfix: removed hardcoded acronym from gmaps.php
Restored comments page, now using arithmetic validation
Comments page optional in config file
Removed grtbl_expedition.php from distribution
Removed grtbl_preparation.php from distribution

_v.07beta13 29 April 2009_
Bugfix: maps not working after update
gmapsaq.php eliminated; using gmaps.php

_v.07beta12 28 April 2009_
Bugfix: type selection not working in klm file conversion
Small map on find pages now having same sql as rest of page; and links to other maps corrected accordingly

_v.07beta11_
Changed table structure for waccessions table
Added minor statistics calculations for expeditions, accessions, requests, and quickbrowse pages
This is a very minor revísion

_v.07beta10_
Bugfix: order names did not show in find.php

_v.07beta9 26 February 2008_
Google Maps code improved and language options added

_v.07beta8 25 February 2008_
Fixed references for fulltext searches in map.php
Simplified text output in map.php
Slight improvements in language files

_v.07beta7 20 January 2008_
Conversions from ImageMagick are somewhat slow. stats.php loading time was cut from 5 to 1 second by changing the image handling in wa_fn_convertimage.inc and stats.php. stats.php now looks in \thumbs if there already is an image and only if there is not, it will convert and display one.
Changed caching time for graphs to 24 hours

_v.07beta6 16 January 2008_
Fixed problem with faulty sorting in trackrefs.php

_v.07beta5 27 December 2007_
Corrected find.php - misspellt stateProvince
Corrected index.php - bad html in form
Fixed missing menus in gmaps.php (this file has its own header)
Validated against Safari on OSX 10.5


_v.07beta4 9 December 2007_
Runs on Apache 2.2, MySQL 5.1, and PHP 5.2.5
Moved files from /graphs to main directory
Removed hardcoded file name for logo in jpgraph files
Added text about JPgraph below; enables multiple instance 
access to same jpg-config.inc.php file
Removed references to "gecache"
Fixed some missing translations
$ICON_FILE changed to $FAVICON_FILE
Made language selection and rss feeds of images and references optional

_v.07beta3 4 December 2007_
Translation about done
Several minor fixes

_v.07beta2 26 November 2007_
Added translation option
A few cosmetic fixes

_v.0.7beta1 12 November 2007_
Certified requirements for 0.7
Added filter to trackrequests.php

_v.0.6beta4 30 October 2007_
Added GPL v. 3 license and GFD licence to this document
Added stripslashes and urlencode in numerous places to cater for 
quotes and ampersands in search strings

_v.0.6beta3 28 October 2007_
Added QUICK BROWSE option
Reinstated the Simple search function
Fulltext search did not work with multiple tables output, fixed with urlencode.

_v.0.6 4 December 2006_
Can be customized for collections without Images, Expeditions, and Tracking 
(Publications, Accessions, Requests) by just eliminating those menu items

_v.0.5 26 August 2006_
CHANGES FROM 0.1.8
Added Google Earth functions
Renamed all concerned files not to include "fish"
Cleaned up some code to use variables instead of strings
Database now based on Darwin Core 2, 1.2 concepts wherever possible

Bugfixes:
gmaps.php did not show markers when locality included quotation marks: 
fixed with htmlspecialchars
Non-lethal: xml files mixed with application files: moved all to /gecache

**************************
* COPYRIGHT AND LICENSE  *
**************************
Collection Presenter is Copyright Sven O Kullander 2003-2010.

Collection Presenter is licensed under the GNU General Public Licence (GPL v.3). A copy of the license is included with the distribution and must always accompany any redistribution. Collection Presenter is distributed only as source files. Contained files are listed at the end of this document, and include program code as well as artwork.   

This file is part of Collection Presenter. Collection Presenter is free software: you can redistribute it and/or modify it under the terms of the GNU General Public License as published by the Free Software Foundation, either version 3 of the License, or any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details.

You should have received a copy of the GNU General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.

This file and other documentation for Collection Presenter are released under the GNU Free Documentation License Version 1.2, as specified at the top of this document. You should have received a copy of the GNU Free Documentation License along with this documen. If not, see <http://www.gnu.org/licenses/>. 


**************************
* ROADMAP                *
**************************

v.0.5 for general collection use, DarwinCore 2 concepts, can run multiple instances for different disciplinary databases
v.0.6 modularisation for collections not using accession numbers, request tracking, or images.
v.0.7 style removed from pages, specified in css
v.0.8 ABCD concepts where available and not covered by DwC2
v.0.9 compatibility with Specify and other CMSs than The Artedian; dropped (cannot guarantee compatibility), go straight to 1.0
v.1.0 official release as Open Source application


***************************
* GENERAL
***************************

The Collection Presenter is a package enginge for presenting natural history museum collections on a web server. It was designed to take output from The Artedian, a collection management system, but can be used for any collection straight away or with light tweaking.

Versions up to 0.1.8 are all obsolete and worked specifically for fish only.

Versions 0.6 and higher are entirely independent of systematic group presented.

Some requirements remain for collections:
They must be based on collection databases with catalog numbers and field numbers, and georeferenced using decimal degrees. Any collection database that can be exported to a Darwin Core 2 file will do for basic operations (search objects and localities).

The Collection Presenter handles acquisitions, requests, and images, but if not present, light tweaking can comment out those features.

Best of all: If you do not like the name Collection Presenter, you can rename your instatiation of the application to any decent name of your preference, as long as you leave all documentation intact, and keep the copyright statement and version number.

*************************
*   OPERATING SYSTEM    *
*************************
Windows or Linux, probably any system on which PHP and MySQL run

**************************
*   DATABASE BACKEND     *
**************************
Only MySQL 4 and 5. MySQL 5 is recommended.

In php.ini, make sure both mysql and mysqli extension modules are enabled, section Windows Extensions, and that the corresponding dlls are present in the extensions directory:

	extension=php_mysql.dll
	extension=php_mysqli.dll

The Module settings can be left at default for both mysql and mysqli.

*************************
*     WEB SERVER        *
*************************

Tested only with Apache 2.0.x. and 2.2.x

*************************
* 	SCRIPTING	*
*************************

Written for PHP 5.x, not tested with earlier versions of PHP.
Database access is through the mysqli extension, exceptionally the mysql extension.
PHP should run as a module, not as a cgi script.
PEAR classes are not included (yet).

Some Javascript is included for Google Maps and Nifty Corners.

*************************
*	DEPENDENCIES     *
*************************

The Collection Presenter uses the following script packages or libraries. They need to be downloaded and installed separately, and are not included with the Collection Presenter distribution. If images will not be shown, ImageMagick and Nifty Corners are not necessary. Graphs are constructed on the fly with JPgraph, but can be commented out from the stats.php page. FPDF is a PHP class for constructing pdf output. It can be commented out from the find.php page.

_Magick Wand for PHP_
Install ImageMagick and the corresponding Magick Wand dll

_Nifty Corners_
Add the applet to the java subdirectory and the stylesheet files to the style subdirectory

_JPgraph_
Install as per instruction. You should try to use JPgraph 2.X (for PHP 5).
I suggest placing the jpgraph class and all other files in a a subdirectory /jpgraph anywhere where accessible by the web server (e.g., C:\php\includes\jpgraph). Change the includes reference in php.ini to contain the path to /jpgraph.

Configure JPgraph to create cached files, expiring after a suitable time depending on how often you upgrade and your web traffic.

In jpg-config.inc.php, do the following:

1. Specify a cache directory as follows:
	if (isset($CACHE_DIR)){
	DEFINE ("CACHE_DIR", "$PATH_TO_DIR/$CACHE_DIR/");
	}
This ensures that if you have multiple applications or Collection Presenter instances, the cached graph file will end up within a specific directory.


2. Set caching to true:
DEFINE("USE_CACHE",true);

3. Set jpgraph to check for cached file before attempting to create a file:
DEFINE("READ_CACHE",true);


_FPDF_
Install as per instruction.

_GD2_
The GD package comes with PHP4 and PHP5. You need to enable it by uncommenting the corresponding line in the php.ini file, section Windows Extensions: 
	extension=php_gd2.dll

_Google maps_
You must register with Google and obtain a Google maps key to be able to use the Google Maps API to display maps from your server.
The key value must be stored in the wa_googledata.inc file.


*************************
*    CONFIGURATION      *
*************************
All *.inc files except wa_config.inc may be placed in a separate directory, preferably the includes subdirectory under the php directory. Do not place the wa_db.inc or wa_authority.inc files in a web server directory as they contain user names and passwords, but they must be accessible by the web server at run time.

All *.php files and the wa_config.inc should be placed in a directory under the webserver, e.g., ../htdocs/wartedian/

The following configuration of Collection Presenter web directory and subdirectories is required. Hard coded directory references may be removed in future versions.

htdocs
....
  /wartedian
     /icones [contains logos, the favicon, and other images part of the application]
     /cache [contains temporary files used by Google Maps and Google Earth, and graphs]
     /images [contains images from the database]
     /java [contains java applets]
     /style [contains the stylesheet files]
     /thumbs [contains temporary files used by the image handler]
     /wands [contains temporary files used by the image handler]


Edit the configuration file wa_config_default.inc to reflect your actual webserver configuration and other data and rename it wa_config.inc

Edit the database connector wa_db_default.inc to reflect your database name, user and password. Rename it wa_db.inc. If you use multiple instances of Collection Presenter, each must have its own wa_db.inc file. For example, if you have two instances of Collection Presenter, one for fish and one for herps, rename one wa_db_fish.inc and the other wa_db_herps.inc, and reference these files accordingly in each wa_config.inc (e.g., $DB_CONN = "wa_db_fish.inc"); more details on multiple instances below.

Edit the wa_authority_default.inc to have the preferred username and password and rename it wa_authority.inc. Even if you have several instances of Collection Presenter running, you only need one wa_authority.inc file.

Note: The /graphs subdirectory was removed as of v. 07.beta4

************************
* MULTIPLE INSTANCES   * 
************************	

Several instances of Collection Presenter can be run on the same server but require different directories, and the following changes to file names:

The the db connector file must be duplicated and have different names. 

Example: You have a herpetology and an ichthyology database:

Create a /herps and a /fish subdirectory under the httpd root, and add subdirectories as described above.

Make copies of wa_db_default.inc [default] and name them wa_db_fish.inc and wa_db_herp.inc. 

The wa_config.inc file must be edited to reflect actual conditions ($DB_CONN = "wa_db_fish.inc" and $DB_CONN = "wa_db_herp.inc")

The wa_db_*.inc file must be edited to call the right database.


**************************************
*       THE CONFIGURATION FILE       * 
**************************************

This file is named wa_config.inc in the distribution and is called from most *.php files. Rename as you prefer, and edit the variables as per below. All *.php and some includes files call the configuration file with require("wa_config.inc") and if you rename it, you must edit this line in all of them.

*** Application information
$APP_NAME = "Collection Presenter"; // normally do not change
$APP_VERSION = "0.7"; // do not change!

*** Web administrator information
$ADMIN_EMAIL = "my.name@myinstitution";
$ADMIN_NAME = "My Name";

*** Collection information 
$INST_NAME = "The Name of My Institution"; // e.g., Some Museum of Natural History
$COLL_NAME = "The Name of My Collection"; // e.g., Herpetology Collection
$DB_NAME = "The Name of My Database"; // e.g., Herpetology Database
$COLL_ACRONYM = "ABC";
$COLL_TAXON = "Taxon"; // e.g., Fishes

*** Web page header items
$PAGE_TITLE = "Acronym Discipline search:"; // e.g., ABC Herpetology search
$PAGE_AUTHOR = "Email and name of the person responsible for the web presentation"; // e.g., john.smith@some.edu John Smith
$PAGE_COPYRIGHT = "Email and name of the person responsible for the web presentation"; // e.g., john.smith@some.edu John Smith
$KWSET = "relevant keywords separated by comma"; // e.g., fish, ichthyology, museum

*** Contact email
$COMMENTS_TO1 ="mailto address"
$COMMENTS_TO2 ="mailto address"

** Directory locations
$SERVER_NAME = $_SERVER['SERVER_NAME']; // do not change
$WEBROOT = $_SERVER['DOCUMENT ROOT']; // do not change
$CACHE_DIR = "cache"; //do not change
$HOME_DIR = $SERVER_NAME."/the_name_of_the_directory_where_wartedian_php_files_reside"; // e.g., fishdb
$PATH_TO_DIR = "C:/Program Files/Apache Group/Apache2/htdocs/wartedian/"; //N.B. Example path to your wartedian directory

*** Customizable file names
$DB_CONN = "wa_db_default.inc"; // change to the name of the file opening the database connection
$RSS_FILE = "rss.xml"; // you can change, but keep xml extension 
$CSS_FILE = "wa_style.css"; //do not change
$FAVICON_FILE = "name_of_file.ico"; // Your favicon file name, e.g., abc.ico

*** Display customization
$EXPEDITIONS = "YES"; // alternative is "NO" if you have no expeditions
$IMAGES = "YES"; // alternative is "NO" if you have no images
$TRACKING = "RAP"; // alternative is NONE if you have no requests, acquisition or publications tables
$MULTILANG = "YES"; // alternative is NO if you do not wish to enable different language interfaces
$DEFAULT_LANG = "en" // alternatives are "sv", "es", and/or your custom language files. The corresponding wa_lang_*.inc must be present.

****************************************
* 	  CUSTOMIZE DISPLAY            *
****************************************

A minimum requirement to run the WebArtedian is to have database content corresponding to Darwin Core 2.0 version 1.2. In addition, you can present images, expeditions, references, accessions, and requests in a non-standard way. If you do not have those options, you must turn them off in the configuration file, setting $EXPEDITIONS and $IMAGES to "NO" and $TRACKING to "RAP". You may also wish to edit the about.php file to confirm to your particular settings. Affected files include:
index.php
stats.php
about.php
topmenu.inc

Affected files will not show images, expeditions, references, accessions, or requests as menu items or otherwise, if those items are turned off in the configuration file. You must, however, keep all database tables even though some of them may be empty, e.g., expeditions, requests, etc.


****************************************
*  THE LOCALISATION FILE               *			
****************************************

This file and functionality may be replaced by the language files?

To enhance searches for local names, and for searches for national data, a localisation glossary file is provided, wa_localisation.inc.

It contains only the following items:

$LANG_LANGUAGE = "Svenska"; // or, e.g., danska, norsk, Deutsch, English, Portugues, Italiano ...
$LANG_COUNTRY = "Sverige"; // or, e.g., Danmark, Norge, Deutschland, United Kingdom, Portugal, Italia ...
$LANG_COUNTRY_ENG_UC = "SWEDEN"; The English country name in upper case, must agree with a name in the Wartedian table
$LANG_COUNTRY_ENG = "Sweden";  // The English country name in sentence case
$LANG_COUNTRY_ENG_ADJECTIVE = "Swedish"; // The English country name in the adjective case
$LANG_PROVINCE = "Län"; // The national word for province/state
$LANG_DISTRICT = "Landskap"; // The national word for political division less than province/state
$LANG_COMMONNAME = "Svenskt artnamn"; // The national expression for Common name

Completing the localisation file is mandatory. Some searches will not work otherwise

****************************************
* GOOGLE MAPS CONFIGURATION            *
****************************************

Use of Google(TM) Maps requires a license from Google. Add the license to wa_googledata.inc. In that file you can specify alternative markers for the Google Maps data points ($GM_ICON).

The following marker images are provided:
gmicon_blue.png
gmicon_yellow.png

****************************************
*   OPTIONAL LANGUAGES MANAGEMENT      *
****************************************

To enable different language interfaces, all text is contained in variables. Files named wa_lang_**.inc contain the language specific text equivalents. As of 0.7beta2, the following language files are available:

English: wa_lang_en.inc
Spanish: wa_lang_es.inc
Swedish: wa_lang_se.inc

Other languages can be added by modifying the language selction options in index.php and translating wa_lang_en.inc into a language of choice. Rename it by replacing the "en" with the particular two-letter language ISO code of the new language.

Users select language from a form on the index.php page. 

Language options are managed by a cookie set to expire after one year. The cookie is set by index.php, and checked by a script in wa_counter.inc, which is included in wa_header.inc. If no cookie can be set, the default language is used. The default language is specified in the wa_config.inc file.
 
Updated versions of Collection Presenter will add new terms to the English language file. One must update customized translations accordingly.  If you wish to reduce or increase language options, you must modify the form in the index.php file accordingly. If for some reason you do not wish to use the language option, you can turn it off in wa_config.inc. 

****************************************
*  THE DATABASE CONNECTION FILE	       *
****************************************

This file is named wa_db_default.inc in the distribution. Rename as you prefer (e.g., wa_db_herp.inc) and edit the username, password and database name. Make the corresponding change in wa_config.inc at variable $DB_CONN.

<?php   $dbcnx=mysqli_connect("localhost", "USERNAME", "PASSWORD") or
	die("Could not connect: " . mysqli_error());
	mysqli_select_db($dbcnx,"DATABASENAME"); 				
?>

Normally the host will be localhost, otherwise substitute with the correct server name.

I do not put the database connection information in the wa_config file because not all files/scripts require a database connection; but this may change.


***************************************
* 					THE COUNTER				        *
***************************************

The file wa_counter.inc registers sessions, which correspond to site visits, and cookies relating to the language selection. It is included only in the wa_header.inc file. 

The counter as now stands is a quick-and-dirty fix, it will change in a future version.

***************************************
* 	SERVER FILES vs. INCLUDE FILES    *
***************************************

The server files are all named *.php. Overall they are a mix of html with style and database calls.

The includes files are  all named wa_*.inc and contain either functions or other short procedures not requiring any html. Generally they were meant to reduce the coding of otherwise rather bulky presentation pages. Except for wa_config.inc you can move them to your web directory if you prefer, but it is advised to leave the wa_db_***.inc and wa_authority.inc files outside the web server. 

 
***************************************
* FPDF
***************************************
PDF files are generated using the FPDF class. You must install and configure FPDF yourself; it is not included in the Collection Presenter distribution: http://www.fpdf.org/

The routine in wa_fn_makepdf.inc creates the pdf file. In the distribution it is called wa_fn_makepdf_default.inc. 

You must edit the following two lines at the top of wa_fn_makepdf.inc to reflect your own FPDF setting

	define(FPDF_FONTPATH,'C:/Program Files/Apache Group/Apache2/htdocs/fpdf/font/');

	require("C:\Program Files\Apache Group\Apache2\htdocs\fpdf\fpdf.php");

Add the database connection string to line 168, and rename the file wa_fn_makepdf.inc.

Because the FPDF script is OO, it does not use the wa_db_*.inc db connection and consequently, if you have several implementations of Collection Presenter, you must have a wa_fn_makepdf.inc file for each. Since the output is somewhat ugly, you may as well comment it out from find.php.

The pdf output option will improve in later versions of Collection Presenter.

***************************************
*	RSS FILES								*
***************************************

RSS files are updated running rssfeed.php manually upon database update. It creates up to five RSS 2.0 xml files:
$RSS_FILE (for new objects; you must supply a name in wa_config.inc)
rssreferences.xml (for references citing objects, taken from the wreferences table)
rssimages.xml (for objects, taken from the wimages table)
rssmodified.xml (for modified objects)
rssaccessions.xml (for new accessions, taken from the waccessions table)

The rss files are specified in wa_header.inc. If you do not have the waccessions, wreferences or wimages tables, you should delete or comment out the respective lines in the wa_header.inc file.


***************************************
*	IMAGES									*
***************************************

Images should be jpeg files with the extension *.jpg and be 1000 pixels wide to fit the display size defined in the css file. When called they will resize to smaller width by imageMagick. 

Images must reside in the /images subdirectory.

All images listed as imageCompressed in the wimages and wlocimages tables must be present on the server.

Image handling will need to be improved as follows:
a. should be able to manage more file types (TIFF)
b. should be able to manage any file dimension (smaller and larger than 1000 pixel width)

***************************************
*                ICONS								*
***************************************

Logos, favicons, maps, and other application specific images are contained in the /icones subdirectory.

The institution logo file, as specified by $INST_LOGO in the configuration file, is collection-specific, and you should provide your own. Recommended size is 70*60 pixels or close to that, and the background should be transparent.


***************************************
*          THE COMMENTS PAGE          *
***************************************
The comments.php page provide visitors an option to make comments, stored in the wa_comments table. There are a number of checks to prevent malicious users making damage, and also a web interface option for the administrator to delete inappropriate comments.

To delete a comment using the web interface, call the delcomment.php page which is locked using Apache authorization. The username and password are stored in the wa_authority.inc file.

You have to configue the Apache authorization yourself on each server. You can also use some other access method.

To enter a comment, the user must provide e-mail, name, comment, and the solution to a math operation based on a random number. Data entered are validated, and if validating stored in the comments table.

For the moment I recommend deactivating the comments table, until a spam safe version is available. There is a switch in the wa_config.inc file to turn off the comments page (set $COMMENTSPAGE = "NO";)


***************************************
*        DATABASE PRIVILEGES          *
***************************************
The default user (specified in wa_db_*.inc) must have SELECT privilege to the database.

To update the counter it is necessary also to set UPDATE privilege specifically on this table (wa_counter).

To maintain the comments table, set the ADD and DELETE privileges specifically on this table (wa_comments).

***************************************
* THE TABLES (for version 1.0)
***************************************
The wartedian table is an excerpt of data from object and locality tables, with pointers to images. All fields must be present, but many may be left with NULL data if not available. If expedition data or images are not available, you should disable portions of the application using those fields. If your catalog number is not an integer, you may change the field to varchar. dateCollected is a text representation of the date which is used instead of yearCollected, monthCollected, and dayCollected. dateCollected must be filled from those fields or other date information source.

A number of Darwin Core fields are omitted. The complete Darwin Core representation of your collection should be available from www.gbif.net; no need to duplicate it in Collection Presenter. Reasons for not duplicating Darwin Core is that (a) it is intended for data exchange involving many collections, (b) most collections will have NULL in many of the DarwinCore fields, and (c) Collection Presenter is intended for collection presentation rather than biodiversity informatics. Non-Darwin Core fields such as expedition and nationalName are relevant to include, as well as fields related to image presentation; expedition data, national names and images are important aspects of collection presentation but not covered in Darwin Core.

Your collection database may have different field names, may miss some of the fields, or may have them in a different format. When you export from your collection database, you can use operations to create or adapt fields, e.g., construct scientificName from concatenation of genus and species, or concatenate yearCollected, monthCollected, and dayCollected into a dateCollected text field, etc. If you do not have dateLastModified, you can set it to be the date of the export, etc. When you do the export you will conveniently change your field names into those used in Collection Presenter. There is no provision for mapping fields in Collection Presenter.

IMPORTANT: If you do not have images, or a separate Expeditions, Publications, Requests, or Accession table as present in the Artedian, you should turn off these options in the Menu. You do that in the wa_config_**'.inc file (set $EXPEDITIONS and $IMAGES to "NO" and $TRACKING to "NONE"). It is not necessary to delete the web or includes files relevant for those tables.

Tables namesprefixed "wa_" reside on the server and are fed from the server; table names starting with a simple "w" are data tables that need to be created and updated from the collection database. 

1. wobjects column list:
(* denotes concept not included in DarwinCore 2)
(+ denotes mandatory fields which must have data)
+order varchar 25
+family varchar 25
+catalogNumber int 11 Primary Key
+genus varchar 25
+species varchar 25
+scientificName varchar 255
identifiedBy varchar 25
yearIdentified smallint 6
*nationalName varchar 50
preparationType varchar 16
*size varchar 16
+typeStatus varchar 25
*originalCombination varchar 35
*objectRemarks mediumtext 0
+*dateRecordCreated date
+dateLastModified date
+fieldNumber varchar 16
+continentOcean varchar 25
+country varchar 25
+stateProvince varchar 25
*district varchar 25
county varchar 25
*island varchar 25
*ocean varchar 25
*lakeBasin varchar 30
*riverDrainage varchar 30
+locality varchar 160
+latitude float
+longitude float
+collector varchar 50
*dateCollected varchar 30
yearCollected int
monthCollected int
dayCollected int
*localityRemarks mediumtext
*expedition varchar 75
*objectImageCount int 11
*objectImage varchar 255
*fieldImageCount int 11
*fieldImage varchar 255

CREATE TABLE `wobjects` (
  `order` varchar(25) DEFAULT NULL,
  `family` varchar(25) DEFAULT NULL,
  `catalogNumber` int(11) NOT NULL DEFAULT '0',
  `genus` varchar(25) DEFAULT NULL,
  `species` varchar(25) DEFAULT NULL,
  `scientificName` varchar(255) DEFAULT NULL,
  `identifiedBy` varchar(25) DEFAULT NULL,
  `yearIdentified` smallint(6) DEFAULT NULL,
  `nationalName` varchar(50) DEFAULT NULL,
  `individualCount` int(11) DEFAULT NULL,
  `preparationType` varchar(16) DEFAULT NULL,
  `size` varchar(20) DEFAULT NULL,
  `typeStatus` varchar(25) DEFAULT NULL,
  `originalCombination` varchar(35) DEFAULT NULL,
  `originalAuthor` varchar(50) DEFAULT NULL,
  `objectRemarks` mediumtext,
  `dateRecordCreated` date DEFAULT NULL,
  `dateLastModified` date DEFAULT NULL,
  `fieldNumber` varchar(16) DEFAULT NULL,
  `continentOcean` varchar(25) DEFAULT NULL,
  `country` varchar(40) DEFAULT NULL,
  `stateProvince` varchar(25) DEFAULT NULL,
  `district` varchar(25) DEFAULT NULL,
  `county` varchar(21) DEFAULT NULL,
  `island` varchar(25) DEFAULT NULL,
  `ocean` varchar(25) DEFAULT NULL,
  `lakeBasin` varchar(30) DEFAULT NULL,
  `riverDrainage` varchar(30) DEFAULT NULL,
  `locality` varchar(160) DEFAULT NULL,
  `latitude` float DEFAULT NULL,
  `longitude` float DEFAULT NULL,
  `collector` varchar(50) DEFAULT NULL,
  `dateCollected` varchar(30) DEFAULT NULL,
  `yearCollected` int(4) unsigned zerofill DEFAULT NULL,
  `monthCollected` int(2) unsigned zerofill DEFAULT NULL,
  `dayCollected` int(2) DEFAULT NULL,
  `localityRemarks` mediumtext,
  `expedition` varchar(75) DEFAULT NULL,
  `objectImageCount` int(11) DEFAULT NULL,
  `objectImage` varchar(255) DEFAULT NULL,
  `fieldImageCount` int(11) DEFAULT NULL,
  `fieldImage` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`catalogNumber`),
  UNIQUE KEY `Catalog_number` (`catalogNumber`),
  KEY `NationalName` (`nationalName`),
  KEY `Family` (`family`),
  KEY `Country` (`country`),
  FULLTEXT KEY `wartfull` (`family`,`scientificName`,`nationalName`,`typeStatus`,`fieldNumber`,`originalCombination`,`continentOcean`,`country`,`stateProvince`,`lakeBasin`,`riverDrainage`,`locality`,`collector`,`expedition`),
  FULLTEXT KEY `Field_Number` (`fieldNumber`),
  FULLTEXT KEY `Taxon` (`scientificName`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;



2. wa_comments SQL
CREATE TABLE `wa_comments` (
  `commentsID` int(11) NOT NULL AUTO_INCREMENT,
  `commenterEmail` varchar(30) DEFAULT NULL,
  `commenterName` varchar(30) DEFAULT NULL,
  `itemCategory` varchar(25) DEFAULT NULL,
  `itemNumber` varchar(25) DEFAULT NULL,
  `commentText` varchar(255) DEFAULT NULL,
  `commentDate` datetime DEFAULT NULL,
  PRIMARY KEY (`commentsID`),
  UNIQUE KEY `idxCommentText` (`commentText`,`commenterEmail`,`commenterName`)
) ENGINE=MyISAM AUTO_INCREMENT=122 DEFAULT CHARSET=utf8;

The wa_comments table stores comments from visitors. 

3. wa_counter SQL
CREATE TABLE `wa_counter` (
  `counter` varchar(255) DEFAULT NULL,
  `counterID` tinyint(4) NOT NULL DEFAULT '0',
  `timestamp` timestamp NULL DEFAULT NULL,
  PRIMARY KEY (`counterID`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;

The wa_counter table stores visitor sessions, and is updated by wa_counter.inc
At start, set the timestamp to the date you want to collect visitor sessions
CAUTION: timestamp use not yet implemented, date hard-coded in wa_counter.inc
	
4. wexpeditions SQL
CREATE TABLE `wexpeditions` (
  `expedition` varchar(255) NOT NULL DEFAULT '',
  `yearStart` int(10) DEFAULT NULL,
  `yearEnd` int(10) DEFAULT NULL,
  `duration` varchar(255) DEFAULT NULL,
  `project` varchar(255) DEFAULT NULL,
  `principalInvestigator` varchar(255) DEFAULT NULL,
  `participants` varchar(255) DEFAULT NULL,
  `objective` varchar(255) DEFAULT NULL,
  `country` varchar(255) DEFAULT NULL,
  `region` varchar(255) DEFAULT NULL,
  `route` varchar(255) DEFAULT NULL,
  `documents` varchar(255) DEFAULT NULL,
  `mainRef` varchar(255) DEFAULT NULL,
  `deposited` varchar(255) DEFAULT NULL,
  `expeditionRemarks` blob,
  PRIMARY KEY (`expedition`),
  FULLTEXT KEY `Expfull` (`expedition`,`duration`,`project`,`principalInvestigator`,`participants`,`objective`,`country`,`region`,`route`,`documents`,`mainRef`,`deposited`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;


5. wreferences SQL
CREATE TABLE `wreferences` (
  `referenceID` int(11) DEFAULT NULL,
  `author` varchar(255) DEFAULT NULL,
  `publicationYear` int(11) DEFAULT NULL,
  `title` varchar(255) DEFAULT NULL,
  `journalPublisher` varchar(255) DEFAULT NULL,
  `citedspecimensID` int(11) DEFAULT NULL,
  `catalogNumber` int(11) DEFAULT NULL,
  `scientificName` varchar(50) DEFAULT NULL,
  `pageRef` varchar(25) DEFAULT NULL,
  `figRef` varchar(25) DEFAULT NULL,
  `citedTaxon` varchar(75) DEFAULT NULL,
  `typeStatus` varchar(25) DEFAULT NULL,
  `originalCombination` varchar(35) DEFAULT NULL,
  `originalAuthor` varchar(50) DEFAULT NULL,
  `newSpecies` tinyint(4) DEFAULT NULL,
  `dateRecordCreated` date DEFAULT NULL
) ENGINE=MyISAM DEFAULT CHARSET=utf8;


6. wimages SQL
CREATE TABLE `wimages` (
  `imageNumber` int(11) NOT NULL DEFAULT '0',
  `NotPublic` tinyint(1) DEFAULT NULL,
  `Not_for_web` tinyint(1) DEFAULT NULL,
  `subject` varchar(255) DEFAULT NULL,
  `content` varchar(255) DEFAULT NULL,
  `copyright` varchar(255) DEFAULT NULL,
  `artist` varchar(255) DEFAULT NULL,
  `imageCompressed` varchar(255) DEFAULT NULL,
  `imageDate` varchar(255) DEFAULT NULL,
  `catalogNumber` int(11) DEFAULT NULL,
  `fieldNumber` varchar(255) DEFAULT NULL,
  `family` varchar(255) DEFAULT NULL,
  `genus` varchar(255) DEFAULT NULL,
  `species` varchar(255) DEFAULT NULL,
  `scientificName` varchar(85) DEFAULT NULL,
  `country` varchar(255) DEFAULT NULL,
  `locality` varchar(255) DEFAULT NULL,
  `dateCollected` varchar(255) DEFAULT NULL,
  `typeStatus` varchar(255) DEFAULT NULL,
  `originalCombination` varchar(255) DEFAULT NULL,
  `originalAuthor` varchar(255) DEFAULT NULL,
  `dateRecordCreated` date DEFAULT NULL,
  PRIMARY KEY (`imageNumber`),
  UNIQUE KEY `imageNumber` (`imageNumber`),
  KEY `imageCompressed` (`imageCompressed`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;


7. waccessions SQL
CREATE TABLE `waccessions` (
  `accessionID` int(11) NOT NULL DEFAULT '0',
  `accessionNumber` varchar(8) DEFAULT NULL,
  `accessionYear` int(11) DEFAULT NULL,
  `accessionDate` varchar(20) DEFAULT NULL,
  `accessionDateYMD` date DEFAULT NULL,
  `accessionType` varchar(16) DEFAULT NULL,
  `accessionAcquiredFrom` varchar(25) DEFAULT NULL,
  `expedition` varchar(75) DEFAULT NULL,
  `donor` varchar(25) DEFAULT NULL,
  `context` varchar(25) DEFAULT NULL,
  `conditionTerms` varchar(25) DEFAULT NULL,
  `objectType` varchar(50) DEFAULT NULL,
  `samplesCount` int(11) DEFAULT NULL,
  `individualCount` int(11) DEFAULT NULL,
  `dateRecordCreated` datetime DEFAULT NULL,
  `dateLastModified` datetime DEFAULT NULL,
  `accessionRemarks` longtext,
  PRIMARY KEY (`accessionID`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;


8. wrequests SQL
CREATE TABLE `wrequests` (
  `requestID` int(11) NOT NULL DEFAULT '0',
  `requestDate` datetime DEFAULT NULL,
  `requestedBy` varchar(25) DEFAULT NULL,
  `requestSubject` varchar(100) DEFAULT NULL,
  `inCharge` varchar(25) DEFAULT NULL,
  `dateExecuted` datetime DEFAULT NULL,
  `actionTaken` varchar(50) DEFAULT NULL,
  `archived` tinyint(4) DEFAULT NULL,
  `loanNumber` varchar(10) DEFAULT NULL,
  `requestRemarks` varchar(100) DEFAULT NULL,
  PRIMARY KEY (`requestID`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;

9. wlocimages SQL
CREATE TABLE `wlocimages` (
  `imageNumber` int(10) NOT NULL DEFAULT '0',
  `imageCompressed` varchar(255) DEFAULT NULL,
  `catalogNumber` int(10) DEFAULT NULL,
  `fieldNumber` varchar(255) DEFAULT NULL,
  `subject` varchar(255) DEFAULT NULL,
  `content` varchar(255) DEFAULT NULL,
  `copyright` varchar(255) DEFAULT NULL,
  `artist` varchar(255) DEFAULT NULL,
  `imageDate` varchar(255) DEFAULT NULL,
  `NotPublic` char(5) NOT NULL DEFAULT '',
  `continentOcean` varchar(255) DEFAULT NULL,
  `country` varchar(255) DEFAULT NULL,
  `stateProvince` varchar(255) DEFAULT NULL,
  `riverDrainage` varchar(255) DEFAULT NULL,
  `ocean` varchar(255) DEFAULT NULL,
  `lakeBasin` varchar(255) DEFAULT NULL,
  `locality` varchar(255) DEFAULT NULL,
  `dateCollected` varchar(255) DEFAULT NULL,
  `collector` varchar(255) DEFAULT NULL,
  PRIMARY KEY (`imageNumber`),
  KEY `Image_Number` (`imageNumber`),
  KEY `Image_file_compressed` (`imageCompressed`),
  KEY `Catalog_number` (`catalogNumber`),
  KEY `Field_Number` (`fieldNumber`),
  KEY `Country` (`country`)
) ENGINE=MyISAM DEFAULT CHARSET=utf8;



*******************************
* FILE LIST
*******************************
(*) are not part of Collection Presenter and thus not covered by the GNU GPL.
(**) include code provided by Google(TM) covered by external license

/my web directory
    about.php
    comments.php
    createmap.php
    delcomment.php
    expfind.php
    expmap.php
    expsearch.php
    find.php
    findcited.php
    findcsquares.php
    gd_blackdot.php
    gd_bluedot.php
    gd_greendot.php
    gd_reddot.php
    gd_reddot5.php
    gfd.txt
    gmaps.php (**)
    googleearth.php (**)
    gpl3.txt
    grtbl_country.php
    grtbl_family.php
    grtbl_province.php
    gr_iconobjectscountry.php
    gr_objectscountry.php
    gr_objectsfamily.php
    gr_objectsprovince.php
    gr_objectsyearlog.php
    gr_speciescountry.php
    gr_speciesfamily.php
    gr_speciesprovince.php
    gr_specimenscountry.php
    gr_specimensfamily.php
    gr_specimensprovince.php
    imageinspect.php
    img2find.php
    imgfind.php
    imgsearch.php
    index.php
    makecsv.php
    makepdf.php
    makexcel.php
    makexml.php
    map.php
    qbrowse.php
    README.txt
    rssfeed.php
    search.php
    searchcsquares.php
    stats.php
    timeout.php
    trackaccession.php
    trackrefs.php
    trackrequests.php
    wa_config_default.inc

    
/includes directory
    wa_aliases.inc
    wa_buttons.inc
    wa_counter.inc
    wa_c_squares_server.inc
    wa_date.inc
    wa_db_default.inc
    wa_expsearchform.inc
    wa_fn_changeimage.inc
    wa_fn_convertimage.inc
    wa_fn_countrecs.inc
    wa_fn_getcsquares.inc
    wa_fn_makepdf_default.inc
    wa_footer.inc
    wa_googledata.inc
    wa_header.inc
    wa_imgsearchform.inc
    wa_kmlfile.inc
    wa_lang_de.inc
    wa_lang_en.inc
    wa_lang_es.inc
    wa_lang_sv.inc
    wa_localisation.inc
    wa_minibargraph.inc
    wa_searchform.inc
    wa_standardbargraph.inc
    wa_standardbargraph500X350.inc
    wa_timerend.inc
    wa_timerstart.inc
    wa_topmenu.inc

/style
    wa_style.css
		
/icones
    africaA4.png
    asiaA4.png
    australiaA4.png
    downarrow.png
    europeA4.png
    gmicon_blue.png
    gmicon_yellow.png
    logo_firefox.png (*)
    logo_htmlkit.gif (*)
    logo_mozilla.gif (*)
    logo_mysql.png (*)
    logo_opera.png (*)
    noamA4.png
    instlogo.png 
    rss.gif (*)
    rss.png (*)
    rudicon.ico
    soamA4.png
    swedenA4.png
    uparrow.png
    valid-xhtml10.gif (*) 
    vcss.gif (*)
    vxhtml10.gif (*)
    worldbig.png
    worldmap2.png
		
    Note: replace instlogo.png with your own logo; replace rudicon.ico with your own favicon	

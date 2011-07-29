# WordPress Plugin Update Notifier

This is a simple WordPress plugin update notifier that will provide your plugin Buyers with a notification every time you issue a plugin update.

It's a very simple script that requires and assumes you have an XML file in your own server. This XML file serves as an endpoint for the script to check what the latest version of the plugin is, and compares it with the current version of the plugin installed in the Client's server.

One of the script **requirements** is that the version number are **floats**. Versions like 1.0, 1.1, 2.3 are acceptable and required.

## Installation

Upload the **notifier.xml** file to your own server (the update notifier on the Client sites will check this file for the latest version)

Copy the **update-notifier.php** file to the root of the plugin.

Edit your plugin's **plugin-file-name.php** main file and include the **update-notifier.php** file with the following code:

	require('update-notifier.php');
	
Edit the **update-notifier.php** file and make the appropriate changes to the following constants:
/
/ Constants for the plugin name, folder and remote XML url
define( 'NOTIFIER_PLUGIN_NAME', 'The plugin name' ); // The plugin name
define( 'NOTIFIER_PLUGIN_FOLDER_NAME', 'plugin-directory-name' ); // The plugin folder name
define( 'NOTIFIER_PLUGIN_FILE_NAME', 'plugin-file-name.php' ); // The plugin file name
define( 'NOTIFIER_XML_FILE', 'http://yourURL.tld/notifier.xml' ); // The remote notifier XML file containing the latest version of the plugin and changelog
define( 'NOTIFIER_CACHE_INTERVAL', 3600 ); // The time interval for the remote XML cache in the database (21600 seconds = 6 hours)
	
Everything should be in place now. Every time you submit a plugin update you should edit the XML file in your server and change the following code to the latest version you've updated:

	<latest>1.0</latest>
	
This way, your Clients will see an update notification on the WordPress admin panel informing them that there's a new version available and they should update.

**NOTE:** when you submit plugin updates make sure to update the plugin version number in the **plugin-file-name.php** main file header. This file is in the root of your plugin and the "Version" is the value used for comparison.

## Screenshot

![plugin update notifier](http://html5.pricetables.wordpress.md/wp-content/uploads/2011/07/updatenotifier1.jpg)

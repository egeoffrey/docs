# Examples and Sample Contents

To help you enjoying at best your experience with eGeoffrey, examples and default contents are provided for preventing you to start from scratch when you need to add your sensors, create your rules and develop your custom pages.

Whenever you [install a new package](/configure/packages) from the Marketplace, this can bring pre-built sensors, rules and sample pages whose settings will show up under "**Sensors**", "**Rules**" and "**Pages**" under "**ADMINISTRATION**". 

If the pacakge brings in a fully-featured example page (like some of the services would do), this will show up under "**Examples**", just below the "**Welcome**" entry in the main menu.

Please note, examples and sample contents persist even after the package bringing them in is uninstalled.

## Remove the examples

If you want to get rid of the examples installed by a specific package do the following:

* Connect to the eGeoffrey web interface, as an admin user and go to "**eGeoffrey**", "**Packages**" under "**ADMINISTRATION**"
* Identify the package associated to the examples you want to get rid of
* Click on "Actions", "Delete Examples"
* Once confirmed, all the sensors, rules and pages will be deleted

Please note, when the package or eGeoffrey will be restarted, the examples will be deployed back again hence this process is suitable when you want to uninstall a package and just before doing so you want to remove its examples.
    
## Prevent ANY package from deploying their examples

If you don't want pacakges from deploying examples, do the following (this will prevent any package from deploying examples but will not delete existing sample contents):

* Log into the system where eGeoffrey runs and go into the directory where eGeoffrey is installed
* Edit the `.env` file by adding `EGEOFFREY_CONFIG_ACCEPT_DEFAULTS=0`
* restart eGeoffrey

Please note you need to repeat the process every time `egeoffrey-cli setup` is executed.
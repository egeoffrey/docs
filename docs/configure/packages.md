# Packages

## Definition

A package is defined as one or more modules (e.g. functionalities) packaged together. It may also include sample contents such as sensors, rules or pages. 

Packages are what you can find in the eGeoffrey's Marketplace and it is what you install when you need specific new skills added to your eGeoffrey.

Packages' naming convention is `egeoffrey-<package_type>-<package_name>`.

You can see the installed packages by accessing the web interface as an admin user and going to "*eGeoffrey*", "*Packages*" under "*ADMINISTRATION*".

## Install the relevant packages

After installing, eGeoffrey knows nothing about your house yet. eGeoffrey's customization is really simple and leverages a set of pre-built modular components for integrating with your existing devices. The process is the following:

*  Think about **what you want to do** (e.g. get temperature measures from the Internet, trigger a MySensors relay, etc.) and what you need to integrate to achieve your goal;
* Visit the eGeoffrey [Marketplace](https://marketplace.egeoffrey.com/) or use the CLI (e.g. `sudo egeoffrey-cli package search weather`) to **identify the package providing the capability** you are looking for;
* **Install the relevant package** by running `sudo egeoffrey-cli package install <package_name>` (e.g. `sudo egeoffrey-cli package install egeoffrey-service-openweathermap`). This should be very fast since it will just install the package without starting it yet;
* **Start the newly installed package** by running `sudo egeoffrey-cli house start` from within the directory where eGeoffrey is installed. This command will download any newly installed packages and start the ones not running yet;
* Wait a few seconds for the module provided by the package to be up and running. **Check if running** by executing `sudo egeoffrey-cli house status` that all of them are in a status of "*Up*";
* Connect to the eGeoffrey web interface, as an admin user and go to "*eGeoffrey*", "*Packages*" under "*ADMINISTRATION*". **Ensure the package has been installed succesfully** and take a note of the provided services;

## Uninstall a package

If you want to uninstall a package from eGeoffrey, do the following:

* **Identify the name of the package** you want to uninstall. Run `sudo egeoffrey-cli package installed` from within the directory where eGeoffrey is installed to get a list of the installed packages;
* **Uninstall the package** by running `sudo egeoffrey-cli package uninstall <package_name>` (e.g. `sudo egeoffrey-cli package uninstall egeoffrey-service-openweathermap`). This should be very fast since it will just remove the package from the configuration without stopping it;
* **Apply the newly updated configuration** by running `sudo egeoffrey-cli house start` from within the directory where eGeoffrey is installed. This command will stop any packages uninstalled with the CLI. Please note neither the configuration nor the package itself will be deleted from the disk;
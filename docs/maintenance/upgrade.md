# Keeping eGeoffrey up to date

eGeoffrey, like any other piece of software, evolves over the time with new capabilities added and bugs fixed.

When you login to the web interface, automatically eGeoffrey checks if there is any of the installed packages requiring to be updated and notifies you straight away. If you feel this behaviour to be annoying, go to "*House*", "*Settings*" under "*ADMINISTRATION*", click the "Web Interface" tab and uncheck the box "Check for Updates at Login".

Whenever you want/need to upgrade eGeoffrey, you need to login via SSH to the system hosting eGeoffrey (upgrades are not possible through the web interface) and run:

`sudo egeoffrey-cli update [<package_name>]`

If no package name is provided, all the packages will be updated if a new version is available. Please note the command will just download the updated package. In order to apply the changes, run `sudo egeoffrey-cli start` which will restart any updated package.
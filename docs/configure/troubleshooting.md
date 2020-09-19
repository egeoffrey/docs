# Troubleshooting

## Reviewing the Logs

Something can always go wrong. And usually this is the time to check your logs:

* Logs can be accessed from the **web interface**:

	* Log in as an admin user and go to "*eGeoffrey*", "*Logs*" under "*ADMINISTRATION*"

* Logs are **stored on the local filesystem**:

	* Log in via SSH to the system hiring eGeoffrey
	* Go to the directory where eGeoffrey is installed
	* Open up the file `data/egeoffrey/logs/egeoffrey.log`

* Logs can be **accessed live** while they are generated:

	* Log in via SSH to the system hiring eGeoffrey
	* Go to the directory where eGeoffrey is installed
 	* Run the command `sudo egeoffrey-cli logs [<package_name>]`
    
## Enable debug output

If something is not working as expected in a specific eGeoffrey component, you can turn debug logging on. To do so, go to "**eGeoffrey**", "**Modules**" under "**ADMINISTRATION**", identify the module you want to enable debug on and check the debug checkbox. No need to restart anything, debug will be enabled straigth away. GO back to you logs and you will see the debug entries.
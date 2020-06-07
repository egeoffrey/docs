# Installation troubleshooting

What is something went wrong and you don't see eGeoffrey coming to life? Here are some basic steps you can take to understand what has happened.

### I cannot access the web interface after the installation

* Ensure the system where eGeoffrey has been installed is reachable (e.g. you can ping it)
* Ensure your browser is pointing to the right IP address (the one reported by the installation process is not necessarily the right one)
* Ensure there is no firewall running (`iptables -L` should have not DROP/DENY lines)
* Ensure all eGeoffrey's components are correctly running by executing `egeoffrey-cli status` from within the directory where eGeoffrey has been installed. Ensure all of them are in a "Up" status.
* Check if the GUI service is accessible by running `netstat -tunap |grep 80`, you should see the port open and something listening on it (ensure you are not running other processes using port 80). 
* Have a look at the logs. Those are in `data/egeoffrey/logs/egeoffrey.log`. If the file is empty, you can run `egeoffrey-cli logs` to see live logs from the different components.
* If a specific service only is not in a "Up" status (e.g. "Restarting"), have a look at the logs of the specific component with e.g. `egeoffrey-cli logs egeoffrey-gateway`

### The installation is taking too long

* The installation can take a while while several software packages have been downloaded and installed
* The installer logs everything into `/tmp/egeoffrey-installer.log`, feel free to open a different session and monitor the file

### The installation did not succeed

* Open an issue on [https://github.com/egeoffrey/egeoffrey-installer](https://github.com/egeoffrey/egeoffrey-installer) or alternatively drop a message on [https://forum.egeoffrey.com](https://forum.egeoffrey.com). Do not forget to include the installation log file (`/tmp/egeoffrey-installer.log`)
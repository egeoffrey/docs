# Accessing eGeoffrey remotely

Even when you are outside of your place you can get in touch with eGeoffrey. This can be done via notifications or by fully accessing eGeoffrey web interface.

#### Notifications

The notifications can reach you anywhere, also when you are outside your local network. Visit eGeoffrey's [Marketplace](https://marketplace.egeoffrey.com) to install the package you need for being notified in the way you like the most (Slack, Email, Telegram, etc.). 

Additionally, with eGeoffrey's [Mobile App](/configure/mobile), you can even get notifications in real time on your smartphone or table.

#### Web Interface

You can even access your eGeoffrey's Web Interface remotely without the need to open any port on your home router or setup a custom VPN. 

This service is offered by a component called "Cloud Gateway". Once your local eGeoffrey instance is linked with our Cloud Gateway you can access it wherever you are in the world. Those are the steps to accomplish it:

* First of all, you need to [register an account](/configure/register) with our eGeoffrey Portal. This will allow your local instance to connect to the Cloud Gateway and you to visit your house remotely.
* Configure your local eGeoffrey to interact with our Cloud Gateway. To do so, run `sudo egeoffrey-cli setup` from the directory where you installed eGeoffrey. You will be asked if you want to access it remotely. Select yes and provide email address and password for the account just created.
* Restart eGeoffrey by running `sudo egeoffrey-cli stop` and `sudo egeoffrey-cli start`.
* Get the new connetion information by running `sudo egeoffrey-cli summary` to understand how to access eGeoffrey both from the local network and remotely. For remote access, you will get something like the following:
    * Gateway:
         * Hostname: gateway.egeoffrey.com
         * Port: 443
         * Use SSL: yes
    * House:
         * House ID: [your_email_address]
         * Passcode: [your_password]
    * User:
         * Username: admin or guest
         * Password: admin for the admin user, <empty> for guest
* Connect remotely to your instance by either using eGeoffrey Mobile App or pointing your browser to [http://cloud.egeoffrey.com](http://cloud.egeoffrey.com) 

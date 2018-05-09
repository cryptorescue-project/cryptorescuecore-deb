cryptorescuecore-deb
===========
Packaging system to deploy CryptoRescue Block Explorer
**The current configuration of this repository creates deb packages suited to run on ubuntu, behind Cloudflare(snakeoil ssl only), and are customized for the domain https://network.cryptorescue.org**

Using the build environment 
------------------
````
$sudo apt-get update
$sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
$curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
$sudo apt-get update
$sudo apt-get install -y docker-ce git make
$git clone https://github.com/cryptorescue-project/cryptorescuecore-deb
$cd cryptorescuecore-deb/cpr
$sudo make
````
DEB file will appear in cryptorescuecore-deb/cpr/

Deploying a cryptorescuecore Deb file
------------------------------------
Download your deb to the home directory of your ubuntu instance
````
$sudo apt-get install -y apt-transport-https curl && sudo dpkg -i cryptorescuecore_4.7.3_amd64.deb
$sudo apt-get update && sudo apt-get -f install -y
$cd /etc/nginx/sites-enabled
$sudo ln -s ../sites-available/nginx-cryptorescuecore .
````
at this point the cryptorescuecore service and nginx will automatically launch and run even after reboot

Optional: add a redirect from www.example.com to example.com
----
````$sudo nano /etc/nginx/conf.d/redirect.conf````
and edit the file with:
````
server {
    server_name www.example.com;
    return 301 $scheme://example.com$request_uri;
}
````
Restart NGINX
````$sudo service nginx restart````

Helpful commands to manage your Deb based install:
----
````
$sudo service cryptorescuecore start
$sudo service cryptorescuecore stop
$sudo service cryptorescuecore restart
$sudo service cryptorescuecore status

$sudo service nginx start
$sudo service nginx stop
$sudo service nginx restart
$sudo service nginx status
````
Undeploying a cryptorescuecore Deb file
----
````
$sudo apt-get install -y aptitude
$sudo aptitude purge cryptorescuecore
````
Updating cryptorescuecore version
---------------------------------
* Change version in git checkout in cpr/cryptorescuecore/Makefile
* Create a new entry in cpr/cryptorescuecore/debian/changelog by using 'dch -i'
* Then build as usual

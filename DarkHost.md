# DarkHost
All you need to know to launch a dark service server with ArchLinux.

## Dependencies
#### Install all the dependencies required.

```sudo pacman -Syyu``` #### first we update the system to get the latest dependencies versions.

```sudo pacman -Sy tor ``` #### Install tor infrastructure.

### Installing the web server:

I will be using nginx but you can use apache and have the same steps.

```sudo pacman -Sy nginx```

```sudo pacman -Sy apache```

#### By default the web server will be running on localhost:80 (127.0.0.1:80) d'ont matter the web server you are using.

#### Configure the Tor Service:

```sudo vim /etc/tor/torrc```

#### This lines will generate a directory of information and cryptographic keys for your onion service, and set a virtual ip and 
port. Any traffic incoming to port 80 of your onion service should be redirected to 127.0.0.1:80.

#### HiddenServiceDir /var/lib/tor/my_website/

#### HiddenServicePort 80 127.0.0.1:80

#### If you don't want to be discovered by your local-network, you can configure the server over Unix sockets instead of a TCP socket:

HiddenServiceDir /var/lib/tor/my-website/

HiddenServicePort 80 unix:/var/run/tor-my-website.sock

#### While this done, its time to provide content to the web page, im my case I will have the page content directory to the nginx path:

*/usr/share/nginx/html*

#### Here you will be able to change the html file, and upload the js or css files.

#### As an example i will be using the shared files index.html and /.js/script.js files on the repository.

#### Once this steps done we will start the services:

```sudo systemctl start nginx```

```sudo systemctl start tor```

#### To stop the services:

```sudo systemctl stop nginx```

```sudo systemctl stop tor```

#### To restart the services:

```sudo systemctl restart nginx```

```sudo systemctl restart tor```

#### And thats it.

#### To-do:

#### Server protection

#### https://community.torproject.org/onion-services/advanced/opsec/

#### Onionx scan, a tool that tells you if you are being anonymous:

#### https://onionscan.org/


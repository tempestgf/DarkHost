# Dark Host
#### All needed to know to launch a dark service server with Arch Linux.

## Dependencies
#### Install all the dependencies required.

```
sudo pacman -Syyu
```
#### Update the system to get the latest dependencies versions.

```
sudo pacman -Sy tor
```
#### Install tor infrastructure.

### Installing the web server:

This guide will be using nginx, but it can be used in Apache as well.

```
sudo pacman -Sy nginx
```

```
sudo pacman -Sy apache
```

#### By default the web server will be running on localhost:80 (127.0.0.1:80) don't matter the web server used.

#### Configure the Tor Service:

```
sudo vim /etc/tor/torrc
```

#### This lines will generate a directory of information and cryptographic keys for the onion service, and set a virtual IP and port. Any traffic incoming to port 80 of the onion service should be redirected to 127.0.0.1:80.

#### HiddenServiceDir /var/lib/tor/my_website/

#### HiddenServicePort 80 127.0.0.1:80

#### If it's not desired to be discovered by the local-network, can configure the server over Unix sockets instead of a TCP socket:

HiddenServiceDir /var/lib/tor/my-website/

HiddenServicePort 80 unix:/var/run/tor-my-website.sock

#### While this done, it's time to provide content to the web page, this guide will have the page content directory to the nginx path:

*/usr/share/nginx/html*

#### Here will be able to change the HTML file, and upload the JS or CSS files.

#### As an example, this guide will be using the shared files index.html and /.js/script.js files on the repository.

#### Once this steps done, start the services:

```
sudo systemctl start nginx
```

```
sudo systemctl start tor
```

#### To stop the services:

```
sudo systemctl stop nginx
```

```
sudo systemctl stop tor
```

#### To restart the services:

```
sudo systemctl restart nginx
```

```
sudo systemctl restart tor
```

#### And that's it.

#### To-do:

#### Server protection

#### https://community.torproject.org/onion-services/advanced/opsec/

#### Onionx scan, a tool that tells if are being anonymous:

#### https://onionscan.org/

#### Nyx a program to monitor tor usage. nyx



Corrected with https://www.corrector.co/


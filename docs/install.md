#Installation

LazyLibrarian runs by default on port 5299 at http://localhost:5299

Linux / Mac OS X:

* Install Python 2 v2.6 or higher, or Python 3 v3.5 or higher 
* Git clone/extract LL wherever you like
* Run "python LazyLibrarian.py -d" to start in daemon mode
* Fill in all the config (see [ Wiki](https://github.com/DobyTang/LazyLibrarian/wiki/) for full configuration)

* Start in daemon mode with `python LazyLibrarian.py -daemon`

## Documentation:
* Wiki at https://github.com/DobyTang/LazyLibrarian/wiki   
* Online (new site goes here)

## Support/Issues
* reddit -  https://www.reddit.com/r/LazyLibrarian/   
* github tracker - https://github.com/DobyTang/LazyLibrarian/issues

## Turorials
Docker tutorial  http://sasquatters.com/lazylibrarian-docker/   
Config tutorial  http://sasquatters.com/lazylibrarian-configuration/   
(thanks @mccorkled)   

For more options see the [Wiki](https://github.com/DobyTang/LazyLibrarian/wiki/).

## Updates
Auto updates are available via interface from master for git and source installs

## Packages
rpm deb and snap packages 

- https://github.com/DobyTang/LazyLibrarian/releases  
  - The snap package is confined to users home directory, so all books and downloads need to be accessible from there too.
  - Install the snap package with flags --dangerous --devmode  
- AUR package available here:
  -  https://aur.archlinux.org/packages/lazylibrarian/  
- QNAP LazyLibrarian is now available for the QNAP NAS via sherpa.
  -  https://forum.qnap.com/viewtopic.php?f=320&t=132373v

## Docker packages
- armhf version 
  -  https://hub.docker.com/r/lsioarmhf/lazylibrarian/  
- x64 version 
  -  https://hub.docker.com/r/linuxserver/lazylibrarian/    
  - with calibredb https://hub.docker.com/r/thraxis/lazylibrarian-calibre/


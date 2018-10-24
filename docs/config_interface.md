#Interface
<img src="/assets/screenshots/config_interface.png" width="800">

## Server Details
* ***Hostname -***
Address of the machine LazyLibrarian is running on. Default 0.0.0.0  
You probably don't need to change this.
* ***Port -***
Port to point your browser at for the web interface. Default 5299
eg localhost:5299 be careful changing this if you are running docker. This much match the docker container port.
* ***Web Root -***
Prefix for web. usually used with a proxy frontend
eg /lazylib so you would hit ip:port/lazylib
* ***Enable http proxy -***
Set cherrypy tools.proxy.on True
```
 *** Note this is usually not needed for nginx, or for transparent proxying, 
 and can cause redirects to 127.0.0.1 if set unnecessarily. If it is set,
 and you are NOT using apache2, you will need to set PROXY_LOCAL in your
 config.ini to reflect the header in use. This config option is not available
 in the web interface.***
```
* ***Enable https access to lazylibrarian -***
Allow login only over https

##Logs
* ***Log Dir -***
Where to store log files. We create a rolling log of 10 files, each around 200K
The number of log files and maximum size are configurable in the config.ini file
but not on the web interface. Older log entries are deleted as necessary to stay in these limits.
* ***Log Files -***
This is how many files to rotate.
* ***Log Size -***
This is maximum size of each file.
* ***Log Lines -***
This is how many lines of log to keep in memory for the on-screen display.
Larger screen logs use more memory and are slower to display.
* ***Log Level -***
0=Quiet, 1=Normal, 2=Debug
Values larger than 2 are currently undefined and may change in later versions.
They are used for detailed debugging and produce a lot of output

## Proxy Details
If you are behind a proxy, set these values as appropriate

* ***Proxy Host -***
* ***Proxy Type -***



## Access Control

* ***Enable user accounts -***

Switch on user accounts so each user can have different access rights, and also save their own read/to-read bookmarks, specify their preferred book type etc. See separate wiki page.

* ***Single user bypass login -***

If you have user accounts enabled, but are the only user on your system, this will log you in automatically. Useful if you need user accounts for bookmarks

###If user accounts are NOT enabled...  
User name and password for logging into the web interface

* *** User Name -***
* *** Password -***

###If user accounts ARE enabled...
* ***Contact email for administrator -***
This is the email your users will use to contact you for lost passwords, requests etc.

## Startup
* ***Launch Browser -***
If ticked, launch a browser (or a new tab in a running browser) when LazyLibrarian starts up.
Leave unticked if running LazyLibrarian on a headless server or if you don't want to log in at startup.
* ***Enable API -***
If ticked, allow api access to LazyLibrarian, see wiki api page for details.  
Current api key is displayed, or you can generate a new api key or edit the generated one.

## Appearance

* ***Interface -***
Currently LazyLibrarian ships with it's old default interface (now called "legacy") and a much more modern bookstrap interface which works better with smaller screens than the default. 
It has many different themes available, the bookstrap theme selector is not visible in the default theme.
Several newer features are ONLY available in the bookstrap interface, as some libraries used in the default interface are too old. Development work and new features are likely to be bookstrap only.
* ***Theme -***
Choose the active theme here. Legacy or Bookstrap. Bookstrap is recommended.

* ***CheckBoxes -***
A selection of display features can be turned on and off, disable the parts you don't need for a cleaner interface

  * Show Author Images
  * Show Book Images
  * Show Magazine Images
  * Show Series
  * Show Magazines
  * Show AudioBooks
  * Show column toggles
  * Show titles ignoring definite article (The, A)
  * Show author surname first

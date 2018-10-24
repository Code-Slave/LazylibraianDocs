#rTorrent limitations  
rTorrent does not work well with magnet links, so we try to convert them to torrent files using libtorrent. 
The external library "libtorrent" is not supplied with LazyLibrarian as it is architecture specific. If you don't have the library installed, LazyLibrarian will not be able to convert.  
  
Libtorrent is available in most linux distributions, MacOS, Windows, but is not installed by default on some NAS systems. See [http://www.libtorrent.org/](http://www.libtorrent.org/) for details on building libtorrent. The libtorrent library is also used by Deluge and qBittorrent, so if either of those are installed on your system, there should be a libtorrent file on somewhere your system that we can use, just need to copy it to the right location.  

We are also unable to delete completed torrents from rTorrent, but you can configure rTorrent to do this itself.
Incomplete or stalled torrents can be deleted, just not the completed ones.  

## Connecting to rTorrent
Note that LazyLibrarian talks to rTorrent, not ruTorrent.  
Communication with rTorrent is done through your web browser using SCGI.  
For example using Apache 2.x, in /etc/apache2/apache2.conf put  
SCGIMount /RPC2 127.0.0.1:5000  
and in .rtorrent.rc put scgi_port = 127.0.0.1:5000  
then in lazylibrarian the rTorrent host should be set to localhost (or you could put 127.0.0.1) to use the default location of /RPC2. To use anything else you need to pass this to LazyLibrarian in the hostname.  
If you use SCGIMount /rtorrent 127.0.0.1:5000  you would need to tell lazylibrarian to use localhost/rtorrent  
Don't forget to restart apache2 after any config changes.

For more details or if you use lighttpd or nginx, see  
[https://github.com/rakshasa/rtorrent/wiki/RPC-Setup-XMLRPC](https://github.com/rakshasa/rtorrent/wiki/RPC-Setup-XMLRPC)  
NOTE: The above web page says to use ProxyPass /RPC2 scgi://127.0.0.1:5000 for Apache 2.4 but I couldn't get this to work on Ubuntu 16:10 with Apache 2.4,  SCGIMount /RPC2 127.0.0.1:5000 works fine.

## Testing the connection
From the command line, with rTorrent running, use xmlrpc localhost system.client_version  
This should report the version number of rTorrent  
Once this is working you can try the "test" button in LazyLibrarian. Leave password and username blank for now.

##Securing access
Once the above settings are working, you can add basic auth (user/password) by creating a password file and adding the following lines to your /etc/apache2/apache2.conf  

```
    #rTorrent SCGI 
    <LocationMatch "/RPC2">
        AuthType        Basic
        AuthName        "rtorrentscgi"
        AuthUserFile    /etc/apache2/passwords-enabled/rtorrentscgi
        Require         valid-user
        BrowserMatch    "MSIE"  AuthDigestEnableQueryStringHack=On
        Order           allow,deny
        Allow From      all
    </LocationMatch>
```

Change "/RPC2" if you are not using the default.  
Use htpasswd to create a password file, giving it a user name and a password (which you have to enter twice).
The password file can be called anything, and placed anywhere you like. To create the password file in the example above I used  
htpasswd -c /etc/apache2/passwords-enabled/rtorrentscgi user_name  

To test this, use  
xmlrpc  -u user_name -p user_passwd localhost system.client_version  
Once this is working, put the username and password into the lazylibrarian config file, save the config, and try the "test" button.


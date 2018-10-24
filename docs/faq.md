#FAQ

We will try to keep some known workarounds issues documented here.

## Freenas

There are unresolved issues with lazylibrarians internal upgrade mechanism on freenas systems. If you have problems updating, a debug log of the upgrade process would be _really_ helpful since I don't have a freenas to test on. A workaround for the problem is below (taken from the freenas forums)

```
`service lazylibrarian onestop`

`rm -r /usr/pbi/lazylibrarian-amd64/share/lazylibrarian/LazyLibrarian`

`fetch --no-verify-peer "https://github.com/DobyTang/LazyLibrarian/archive/master.tar.gz"`

`tar xzf master.tar.gz`

`mv LazyLibrarian-master /usr/pbi/lazylibrarian-amd64/share/lazylibrarian/LazyLibrarian`

`chown -R media:media /usr/pbi/lazylibrarian-amd64/share/lazylibrarian/LazyLibrarian`

`rm master.tar.gz`

`service lazylibrarian start`
```

##Running as a Windows Service

* download [](https://nssm.cc/download)

* After you download NSSM, right click on NSSM.exe -> Properties -> UNBLOCK. 

```
_NOTE_:  SOME A/V software will flag NSSM.exe is a virus.  ENSURE to add NSSM.exe to your exclusion list. 
```

* Put nssm.exe in c:\windows\system32 (or put NSSM in a root folder (ex: c:\nssm\nssm.exe) and add that to your PATH)

* Start a command prompt (elevated/admin privileges)

type:  

```
nssm install lazylibrarian
```

* change the following settings:

![lazylibrarian_service](/assets/screenshots/lazylib_service1.png)

* Go to services (Start -> Run -> services.msc) change lazylibrarian to automatic. 

Profit:

![lazylibrarian_service2](/assets/screenshots/lazylib_service.png)

(Thanks to [https://github.com/seanvree](https://github.com/seanvree) for the instructions)


##SSL


### Installation
"You must install pyOpenSSL to use HTTPS"
Installing pyOpenSSL on it's own _may_ not be enough. You may also need to install pycrypto, pyasn1, ndg-httpsclient. Seems some installations automatically pull these in when you install pyOpenSSL and some don't.

### Errors
"SSL: SSLV3_ALERT_HANDSHAKE_FAILURE" when trying to load bookstrap themes
The server you are trying to reach requires (SNI) Server Name Indication and will cause a handshake failure if the client is not using this SNI extension.. Support for SNI was only added with python 2.7.9

You may need to upgrade to a more recent version of python 2.7, and also make sure you have the additional modules mentioned in the previous answer (pycrypto, pyasn1, ndg-httpsclient)

### MAC
Many mac installations of python include an old version of TLS which is no longer supported by git (and pip and lots of other websites). This will stop lazylibrarian upgrading as we can't talk to git. 
LazyLibrarian will report the ssl and tls versions in the startup log, and in the config/system info popup. 
The problem is described here [https://news.ycombinator.com/item?id=13539034](https://news.ycombinator.com/item?id=13539034) with some suggested workarounds. If someone with a mac has got it working, Let us know and we will update the documentation.

### Note
GoodReads has issued a notice that at some future date they will enforce https only access to their api, and at that point lazylibrarian will not be able to use their service without these libraries. 

##Synology

###Magazine covers

Possibly applies to other systems with old or broken ghostscript or imagemagick
 
It assumes your LazyLibrarian installation is in /volume1/@appstore/LazyLibrarian
If not, you will need to adjust the path in step 2

* ssh into your NAS

* Switch to your LazyLibrarian installation directory  
     cd /volume1/@appstore/LazyLibrarian

* Download  a new version of GhostScript from here - 9.18 was the latest version at the time of writing this wiki entry, you can use a later version if one is available  
     wget https://github.com/ArtifexSoftware/ghostpdl-downloads/releases/download/gs918/ghostscript-9.18-linux-x86_64.tgz

* Unpack the archive  
     tar -xvf ghostscript-9.18-linux-x86_64.tgz

* Move the new ghostscript into the LazyLibrarian directory and change the name to gs  
     mv ghostscript-9.18-linux-x86_64/gs-918-linux_x86_64    gs

* Delete the unwanted files  
     rm -rf ghostscript-9.18-linux-x86_64*

* Put /volume1/@appstore/LazyLibrarian/gsconvert.py  
      in the config setting for "Conversion Program"

That way we don't disturb any of the other software on Synology that
might want a different version of gs, we use our own private copy.

###Synology Dockers

Possibly applies to dockers on other systems too.  

If you are running both lazylibrarian and calibre in separate dockers you may hit file permission problems unless one of the dockers has elevated privileges. You need to give elevated privileges either to the calibre one so it will successfully access the files, or to the lazylibrarian one so it can chmod the files.

If you want to chmod the files from the lazylibrarian docker please edit config.ini and change file permissions to 0o666 (default is 0o644) this is so that the calibre docker can read and write (delete) the files as it processes them.  

If you want to use the aptalca docker for calibre, please set EDGE to 1 so it upgrades to latest calibre as the default version in that docker is quite old and seems to have issues talking to newer calibre versions.  

For elevated privileges on synology you have an option when you configure the docker (a simple box to check)  

If you have lazylibrarian in a docker and want to talk to calibre it is HIGHLY recommended that you use the Thraxis docker for lazylibrarian (link is on the lazylibrarian git page). This docker includes calibredb so you can talk to a remote calibre outside the docker, which can be calibre in another docker or a standalone calibre instance, possibly on a different machine.  

Thanks to yongbi85 for the info

##unrar-library and cbr/cbz

cbz magazines should just work. They are zipped collections of jpeg images. Lazylibrarian looks for page 000, or page -00, or cover.jpg   This should cover most cases. If there is another common format that I haven't included, please let me know.

cbr is a little more difficult. These are rar archives, so we need an unrar library. You may already have one on your system (usually called unrar.dll or libunrar.so). Lazylibrarian does not include an unrar library as it is architecture dependant.

You can download UnRAR library sources (and/or binaries) from:
[http://www.rarlab.com/rar_add.htm](http://www.rarlab.com/rar_add.htm)
and compile (you may need to rename the makefile that you want to use according to your OS) and install it from there: Note that for lazylibrarian we need the library sources, [https://www.rarlab.com/rar/unrarsrc-5.6.4.tar.gz](https://www.rarlab.com/rar/unrarsrc-5.6.4.tar.gz)
or a later version, not the binary.  
    $ make lib  
    $ sudo make install-lib  
    $ sudo ldconfig

For Windows you can also download the already compiled library [http://www.rarlab.com/rar/UnRARDLL.exe](http://www.rarlab.com/rar/UnRARDLL.exe).

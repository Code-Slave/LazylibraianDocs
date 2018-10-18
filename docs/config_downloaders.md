All downloaders have a "test" button that does a basic connection test to make sure the settings are correct. 
# Usenet
## Use SABnzbd+
If this is ticked the following options become available
* Host  
If your sabnzbd is running on the same machine as lazylibrarian, put localhost  
Otherwise put the ip address of the sabnzbd machine 
* Port  
Port sabnzbd is listening on
* Username  
Login details for sabnzbd
* Password  
* Category  
Tell sabnzbd to save the books/magazines under this category
* SubDir  
Path to sabnzbd if needed, eg if sabnzbd is host:port/subdir, put the subdir part here.
Leave blank if sabnzbd is just at host:port 
* Retention Max Age  
Ignore nzb results older than this

## Use NZBGet
If this is ticked the following options become available
* Host  
If nzbget is running on the same machine as lazylibrarian, put localhost  
Otherwise put the ip address of the nzbget machine
* Port  
Port NZBGet is listening on 
* Username  
Login details for nzbget
* Password
* Category  
Tell NZBGet to save the books/magazines under this category
* Priority  
NZBGet download priority
  
## Use Synology DownloadStation
If this is ticked the following options become available
* Host  
If lazylibrarian is running on the synology NAS, put localhost  
Otherwise put the ip address of the NAS here
* Port  
Synology defaults are 5000 for http, 5001 for https
* Username  
Login details for the synology NAS
* Password
* Directory  
Usually Multimedia/Download
* Use DownloadStation for usenet  
You can choose to use DownloadStation for usenet, or torrents/magnets, or both
* Use DownloadStation for torrents  
Use for torrents (and magnets)
  
## Use NZB BlackHole
If your nzb downloader monitors a directory for nzb files, tick this 
* NZB Blackhole Directory  
This is the directory your downloader should look in, LazyLibrarian will
put nzb files in here to be collected.

# Torrents
## Use Deluge
Tick this if you use deluge to download torrents.  There are two methods of talking to deluge,  via the daemon,  or via the webui. If you provide a username and password LazyLibrarian will use the daemon, if you just provide a password and leave username blank then LazyLibrarian will use the webui.  
* Host  
If deluge is on the same machine as lazylibrarian, put localhost  
Otherwise put the ip address of the nzbget machine
* Port  
Port that deluge is listening on
* Username  
Only used for deluge daemon
* Password  
Needed for both daemon and webui

## Use Transmission
Tick this to use Transmission to download torrents
* Host  
Address of the transmission daemon.  
If transmission is on the same machine as lazylibrarian, put localhost  
Otherwise put the ip address of the transmission_daemon  
* Port  
Port transmission is listening on  
* Username  
Login details for transmission
* Password

## Use uTorrent
Tick this to use uTorrent to download torrents
* Host  
URL of the uTorrent downloader  
* Port  
Port uTorrent is listening on
* Username  
Login details for uTorrent
* Password  
* Label  
Save books/magazines with this label

## Use qBitTorrent
Tick this to use qBitTorrent to download torrents
* Host  
URL of the qBitTorrent downloader  
* Port  
Port qBitTorrent is listening on
* Username  
Login details for qBitTorrent
* Password  
* Label  
Save books/magazines with this label

## Use rTorrent
Tick this to use rTorrent to download torrents. NOTE: rTorrent does not work well with magnet links, so we try to convert them to torrent files using libtorrent. See notes in the "blackhole" section earlier in this wiki.
* Host  
URL of the rTorrent downloader  
See separate page in this wiki for further details  
* Username  
Login details for rTorrent
* Password  
* Label  
Save books/magazines with this label
* Directory  
Save books/magazines to this directory, or leave blank to use rTorrent defaults

## Use Torrent Blackhole
If your torrent downloader monitors a directory for torrent files, tick this
* Torrent Blackhole Directory  
This is the directory your downloader should look in, LazyLibrarian will
put torrent files in here to be collected.
* Convert magnet links to torrent files
This needs an external library "libtorrent" which is not supplied with LazyLibrarian as it is architecture specific. If you don't have the library installed, LazyLibrarian will ignore the request to convert.  
Libtorrent is available in most linux distributions, MacOS, Windows, but is not installed by default on some NAS systems. See http://www.libtorrent.org/ for details on building libtorrent.

## Minimum Seeders  
Reject torrents if less than this number of seeders
## Keep seeding
What to do after processing the downloaded book/mag  
If ticked, do nothing, keep seeding the files  
If unticked, ask the downloader to delete the torrent
## Directory  
LazyLibrarian expects the downloaders to put books/magazines here

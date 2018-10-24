#Filters
<img src="/assets/screenshots/config_filters.png" width="800">

## Book Reject List
Comma separated list of words to reject:
Search results with any of these words in the title will be ignored
Default: audiobook, mp3
When the downloaders return a list of results, you can filter out ones you don't want using this list. Works by looking for rejected words in the titles returned by the downloaders. Will not reject words that are in the title you asked for, or in the authors name. 
## Magazine Reject List
Global setting, similar to book reject list, applies to all magazines
## AudioBook Reject List
as above
## Extension Reject List (all types)
Results with any of these extensions anywhere in the contents will be rejected. Useful to stop badly named video files being grabbed when you want the book. We scan the list of files in the torrent
(only transmission/deluge/qbittorrent) and reject the whole download if it contains a file with a matching extension. Can't do this for usenet, as there doesn't seem to be a nzb contents list?

## eBook Size Limits
You can restrict downloads by minimum/maximum size (where available). Ebooks are generally way smaller than audiobooks, which helps limit grabbing the wrong type.

## AudioBook Size Limits
You can restrict downloads by minimum/maximum size (where available). AudioBooks are generally way bigger than eBooks, which helps limit grabbing the wrong type.

## Magazine Size Limits
You can restrict downloads by minimum/maximum size (where available). 

## Magazine Reject Lists (per title)
### Reject Words
Each magazine has it's own reject list. Useful where magazine titles are subsets of another title, or where there are international variants of a magazine. Default is blank as most magazines don't need any filtering, just the name.   
Example 1:  
You want to download "Edge" The downloaders return...  
Edge TruePDF-July 2016  
Pacific Edge-April June 2016  
Living Edge TruePDF-May 2016  
In the reject list for Edge you would put Pacific, Living  to prevent these being grabbed  
Example 2:  
You want to download GQ  The downloaders return...  
GQ May 2016  
GQ India May 2016  
GQ USA May 2016  
British GQ May 2016  
In the reject list you would put India, USA, British  
  
If you want to download GQ India, or GQ USA, just put that as the title, no reject list needed.  
  
If you know in advance which words you want to reject, you can pass them as part of the magazine name when you first add it on the "Magazines" page.  Separate title and reject list by a tilde character. To add a new magazine including a reject list, for example 1 above you would put  
Edge ~ Pacific, Living  
into the box marked "Magazine Title" on the top right of the page, and hit the "+ Magazine" button.
### Search Expression
In case you want to call the magazine "UK BBC Radio Times" in your database, but only search for "Radio Times"
### Date Style
Can be useful for filtering out badly named torrents. You can specify which date components must be in the download filename. Normally just leave this blank and we auto-detect.

Issue date components are
M - must contain a month name or number
D - must contain a day number
MM - must contain two month names (bi-monthly issues)
V - must contain a volume number - use I and V if you need both
I - must contain issue number
Y - must contain a year

## Import and Export filter buttons

<img src="/assets/screenshots/config_filters_settings.png" width="400">

To save and load your magazine filter settings if you need to rebuild your database or move to another machine.


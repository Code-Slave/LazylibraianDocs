#Prcessing
<img src="/assets/screenshots/config_processing1.png" width="800">
<img src="/assets/screenshots/config_processing2.png" width="800">
<img src="/assets/screenshots/config_processing3.png" width="800">

##Intervals
Setting an interval to zero will prevent the task from running 

- Book Search Interval (minutes)
- Magazine Search Interval (minutes)
How often to search nzb or tor providers for wanted books/magazines. Does not run if nothing is marked as "Wanted".
- RSS Search (minutes)
How often to search rss feeds for wanted books/magazines. The Goodreads wishlists / Listopia always run, but the RSS feed entries only run if something is marked as "Wanted"  
- Wishlist Search Interval (hours)
How many hours between searches for the wishlist.
- Post-Processing Interval (minutes)
When items have been found and sent to the downloaders, how often should we check the download directory
to see if they have arrived. If there are no items marked as "snatched" this job will not be run.
- Version Check (hours)
How often to check for a new LazyLibrarian version. Setting this to zero will also disable version check at startup.
- Auto Update to new version
Only applies to the automated update check. The manual check will not auto update, it gives you the option.

```
NOTE: Setting a scan interval to zero disables the task
```

##Status

- Missing Book Status  
When you scan the library or add an author, if a book has been removed since the last scan what should we 
set it's status to? Skipped Wanted Have Ignored. "Wanted" will try to re-download the book. "Have" means 
"I've got it, but I've moved it since you last looked"  "Skipped" and "Ignored" can be used to filter books
into ones you don't want (yet) and ones you never want.  
- New Book Status  
When we update an author, what status should we set all the new books to. 
- New AudioBook Status
Same options as for New Book Status
- New Authors eBook Status
When you add a new author, what status should we set their back-catalog. The first time you do a library scan you probably don't want to set "Wanted" as it will try to download every book by every author (except the books you've already got in your library)
- New Authors AudioBook Status
When you add a new author, what status should we set their back-catalog. The first time you do a library scan you probably don't want to set "Wanted" as it will try to download every book by every author (except the books you've already got in your library)
- New Found Status
TODO:
- Include other books by new authors (checkbox)
This will include details for other books by new authors found in wishlists or csv files,
or when manually importing a book by a new author. If unticked we only include the books in the wishlist/csv 
- PreProcessor Program
Path to preprocessor to run before importing books into the library. Examples are included. See [Here](preprocessor.md) for details.

##Calibre

- Calibredb import program  
If you use Calibre and LazyLibrarian on the same machine and they share the same books, put the full pathname of  your calibredb program here, or just calibredb if it's in your system path. LazyLibrarian will not import the books, it will ask calibredb to import the books and then update the LazyLibrarian database to match.
The default method is to give calibredb the location of the book library, however since calibre v3.x calibredb can only access the book library if there is no running calibre, and no running calibre content server. 

The new v3.x method is to talk to calibre (or the content server) and ask them to add/remove/update books for us. 

If calibre-server is started with --enable-local-write  and --listen-on=:: or --listen-on=0.0.0.0 it can be accessed via http://localhost:9000 and http://192.168.0.10:9000 as well as any other IP addresses configured on that machine. That way and for Lazylibrarian purposes, localhost can be accessed without authentication.

If calibre-server is started with a network only address (non loopback/localhost), eg --listen-on=192.168.0.10 then authentication is needed to make changes. The content server needs to be started with --enable-auth or in calibre enable user/passwords in Preferences->Sharing over the net and also set up an account in calibre creating a user and password with write access and put the user/password in lazylibrarian config.

The calibre content server address should look like http://hostname:port/#library (the #library part is optional and will use the default library if not included)

- Calibre Books Auto Add Directory
If you use Calibre on a different machine, or want to maintain separate LazyLibrarian and Calibre libraries, complete this to have LazyLibrarian downloaded books added into the Calibre library. Set Calibre to watch this directory for new books arriving. This should _not_ be used if your LazyLibrarian base destination folder is already an existing Calibre library or you will end up with two copies of each book. In this case use the calibredb option above. Also it should not be used if you are using the content server. You don't need both.

 - Keep a copy of the book in the local library
 - Only add eBook, not opf or jpg
Let Calibre create it's own opf and cover image
 - Add tags included with download to Calibre
TODO:
 - Add wishlist name as tag to Calibre
TODO:

- Calibre Books Auto Add Directory
Same as ebooks but for magazines.
 - Keep a copy of the magazine in the local library
 - Only add magazine, not opf or jpg

##Folders

- Base Destination Folder  
This is where you store your book library. May be an existing shared Calibre Library.
- Alternate Import/Export Folder  
Temporary directory to import new ebooks, one at a time or multiple books if each is in their own subdirectory. LazyLibrarian may delete the directory after importing. Books in this directory should contain embedded metadata, or the directory should contain an .opf file with the same name as the book. Lazylibrarian will try to import the book (and if necessary the author) into the library using the author and title in the metadata. As a last resort LazyLibrarian will try to work out the author and title from the filename by matching it to the naming style in "eBookDestination File", see below.  
Also used as a directory to write a wishlist into (list of wanted books) or to import a wishlist from.
Wishlists are csv files containing author and book_title, optionally isbn or bookID, other fields ignored.

###Name Formatting

- Series Pattern
- Series Name Pattern
- Series Number Pattern
Allows a flexible display of series details in book filenames or foldernames eg (Lord of the Rings Book #1)

- eBook/AudioBook Foldername Pattern  
Naming style when creating new subdirectories in the book library (a.k.a. the base destination folder)
- eBook Filename Pattern  
Naming style for new books in the above folder
- AudioBook Filename Pattern
Naming style for audiobooks as they may be in multiple chapters or parts  

**Variables** - not all are available in all fields  
$Author - author name as stored in the database  
$Title - book title as stored in the database  
$Series - Formatted series name/number  eg (Lord of the Rings #2) if either $SerName or $SerNum are not empty  
$SerName - Series name as supplied by goodreads, or empty string  
$SerNum - Series number as supplied by goodreads, or empty string  
$FmtName - Formatted series name or empty string  eg **Series: Lord of the Rings**  
$FmtNum - Formatted series number or empty string  eg **Book #2** or **- 02 -**  
$PadNum - zero padded series number or empty string  eg **02**  
$PubYear - year of publication of the book (if known) or empty string  
$SerYear - year of publication of the first book in the series (if known) or empty string  
$Abridged - If state known returns **(Abridged)** or **(Unabridged)** or empty string  
$$ - Inserts a space. Only needed on the start or end of a format string if you want spaces inbetween  
NOTE: If series number is not numeric (eg Book Two) it gets added to series name and series number returns empty string  
Example:
$Series `($SerName$FmtNum)`  and $FmtNum `$$#$PadNum`  will produce `(Lord of the Rings #02)`
or if the number isn't known `(Lord of the Rings)` as the space and hash are part of the $FmtNum expression which is empty if there is no series number

- Keep Original Files  
If ticked, books found by the downloaders or placed in the Alternate Import Folder will be
_copied_ into the library. If NOT ticked they will be _moved_ into the library, ie the original
downloaded versions will be deleted. 
- Only import one book format  
If ticked, and an nzb or torrent contains multiple formats of a book, only import one format. LazyLibrarian will import the first matching format from the ebook format list. If unticked, import all formats found in the list.
eg if a download contains the same book as mobi,epub,azw3  and your ebook format list is  epub,mobi  
with the option ticked you will import epub (first match in the ebook format list)  
with the option unticked you will import mobi,epub but not azw3 as that's not in the ebook format list

- Magazine Destination Folder  
Naming style for magazine folders, either inside the book library, or in a separate folder 

- Magazine Destination File  
Naming style for new magazine issues in the above folder  
  
- Magazines Inside Book Folder  
Leave unticked if the magazine folder is a full path to a directory.
Tick if the magazine folder is a sub-folder inside the book library.
Magazine sub-folder names should start with an underscore or a period, or should contain the special file .ll_ignore  so we can identify them as containing magazines rather than books and ignore them on a book scan.

- Quick open single issues of magazines
If only one issue available, open it, otherwise show a page for the magazine title with just the one issue

## Miscellaneous

- Cache Expire After  
Author and book details from googlebooks and goodreads are cached to reduce calls to their servers.
The servers have access limits, both frequency of access and number of hits per day. Caching results means
we should stay well under the limits. 
If our cached entries are older than this number of days, we will reload the details from the servers.
Use 0 to disable caching
  
- Remove Failed Tasks After  
When the postprocessor has completed processing any downloaded books, it will look for any that have not yet arrived in the download folder. If they were requested more than this number of hours ago, assume they are not going to complete. Re-mark the book as "Wanted", mark this download as "Failed", and ask the relevant downloader to delete the incomplete task. The next time the "search" tasks run, they will try to download a different copy.   Use 0 to disable removing failed tasks   

```
NOTE: Removing failed tasks is not supported on versions of 
sabnzbd earlier than 0.8.0
```  

- Search Match Ratio  
When comparing results from torrent and nzb searches, how accurate do we want to match the names.
We need a bit if "wiggle room" to cater for different accents on characters, different spellings of 
author names, eg JRR Tolkien is the same as J. R. R. Tolkien  but if we set this figure too low we will
get matches against the wrong books, so it's configurable. Somewhere around 80% to 90% works well for me.

- Download Match Ratio  
When the downloaders grab a torrent or nzb, we don't have full control over the downloaded filename, so we need some wiggle room here too. Usenet is good, give us the filename we asked for, but torrent names are not always exact. When scanning the download directory for matches, how close should the name match.

- Maximum Search Pages
- Maximum Author Pages
When searching, how many pages of results to grab. Use 0 to select all pages.

- Maximum results on coverwall
When showing covers in a wall layout, how many should we show. Large numbers can take a significant amount of time to draw. We show images "most recent first" so the new books are at the top. Use 0 to show all images

- Git Program  
Full pathname to git if not found in your system path.
Used to check your LazyLibrarian version is up-to-date. If you are running on Windows and don't already have git you can download it from 
[https://git-scm.com/download/win](https://git-scm.com/download/win)

- Conversion Program
When we download a magazine, we can create a cover image from the first page. If you don't want covers,
put _None_ in here. LazyLibrarian will try to use ghostscript for cover creation if it is installed in your system "path", or if a local copy is found in the lazylibrarian folder. If you have Imagemagick installed on your LazyLibrarian machine and your python installation includes either PythonMagick or Wand we can detect and use those interfaces automatically. Some (all?) Synology NAS units have incomplete or old installations of imagemagick and/or ghostscript which imagemagick uses. In this case there is another work-around. See the "Synology Users" wiki entry.

- Full Scan
If this is ticked, when you do a library scan it will check all the books in the library and remove the "Open" status on the database entries for any books that have been deleted since the last scan. 

- Create opf files for magazines
Useful if importing them into calibre

- One Book Per Directory  
If you keep multiple versions of the same book in your library, eg a mobi and an epub of the same book in the same folder, tick this box. LazyLibrarian will then scan faster, as it will only process one book per folder.

- Rename existing books on libraryscan
This renames existing files in your book library to match eBook/AudioBook Filename Patterns. Does not rename if the folder looks like a Calibre foldername, as Calibre would not be able to find the books

- Rename existing magazines on libraryscan
This renames existing files to match Magazine Filename Pattern

- Add Authors  
When scanning the library, if a book is found by an author who isn't already in the database, should 
LazyLibrarian add the author and list all their books in the database. If not ticked, only the book found will be added, not the list of all the authors books, and the author will be marked as Ignored so will not show in the default lists or searches. The book will show in the eBooks page.

- Add Series Info
If you like to arrange your books in series, or collect series, you need to tick this. If you soon't then lazylibrarian will not try to download any series info. Turn it off if you don't need series info, it's faster.

- Search when added
This will auto search for books/mags as soon as you add them to the database. Leave unticked to search for them later on a scheduled task or a manual search.
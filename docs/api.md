# API

Lazylibrarian now has a basic api. To use it...
http://host:port/api?apikey=your_api_key&cmd=help

This will list all available commands and any extra parameters required.  
Simple commands just return OK, more complex commands return results as JSON so you probably want to use json.loads() to read the results.  
Time consuming commands such as library scanning and updating active authors return OK straight away, and then run in the background as a separate thread. If you need to know when they have completed, monitor the log,  or use the optional &wait parameter. Some proxy servers will timeout if the wait is too long. 
  
Parameters passed to the api should be in urllib.quote_plus style, eg name=Tom+Holt, not name="Tom Holt" or name=Tom%20Holt  
and be aware that Goodreads is very fussy about initials, and returns strange/irrelevant/random results if you don't get it right.  
It doesn't like initials followed by spaces, examples below are quote_plus encoded...  
eg "J+R+R+Tolkien" fails, it needs to be "J.+R.+R.+Tolkien" or "J.R.R.Tolkien" or just "Tolkien"  
but it DOES need spaces if not initials eg "Tom.Holt" fails, but "Tom+Holt" works  
  
Also if there are any functions you might like that aren't implemented, post a message on the issues page and I'll see what I can do.

http://host:port/api?apikey=bf892636d3296d9474a3eeba991a90f9&cmd=help

####authorUpdate: 
update the oldest author, if any are overdue
####addAuthorID: 
&id= add author to database by AuthorID, 
####addMagazine: 
&name= add magazine to database by name, 
####calibreList: 
[&toread=] [&read=] get a list of books in calibre library, 
####cleanCache: 
[&wait] Clean unused and expired files from the LazyLibrarian caches, 
####createPlaylist: 
&id Create playlist for an audiobook,
####clearLogs: 
clear current log, 
####dumpMonths: 
Save installed monthnames to file, 
####createMagCovers: 
[&wait] [&refresh] create covers for magazines, optionally refresh existing ones, 
####findBook: 
&name= search goodreads/googlebooks for named book, 
####forceMagSearch: 
[&wait] search for all wanted magazines, 
####forceWishlistSearch:
[&wait] search all entries in wishlists,
####forceRSSSearch: 
[&wait] search all entries in rss feeds,   
####forceBookSearch: 
[&wait] [&type=eBook/AudioBook] search for all wanted books, 
####getLogs: 
show current log, 
####getRSSFeed: 
&feed= [&limit=] show rss feed entries, 
####getModules: 
show installed modules, 
####getSeriesAuthors: 
&id= Get all authors for a series and import them, 
####getIssues: 
&name= list issues of named magazine, 
####getDebug: 
show debug log header, 
####getBookAuthors: 
&id= Get list of authors associated with this book, 
####getWanted: 
list wanted books, 
####grFollowAll: 
Follow all lazylibrarian authors on goodreads, 
####getAuthor: 
&id= get author by AuthorID and list their books, 
####grFollow: 
&id= Follow an author on goodreads, 
####help:
 list available commands. Time consuming commands take an optional &wait parameter if you want to wait for completion, otherwise they return OK straight away and run in the background, 
####includeAlternate: 
[&wait] [&dir=] Include books from named or alternate folder and any subfolders, 
####importAlternate: 
[&wait] [&dir=] Import books from named or alternate folder and any subfolders, 
####ignoreAuthor:
&id= ignore author by AuthorID, 
####importCSVwishlist: 
[&wait] [&dir=] Import a CSV wishlist from named or alternate directory, 
####loadCFG: 
reload config
####listIgnoredAuthors: 
list all authors in the database marked ignored, 
####listIgnoredSeries: 
list all series in the database marked ignored, 
####moveBooks: 
&fromname= &toname= move all books from one author to another by AuthorName, 
####nameVars: 
&id Show the name variables that would be used for a bookid, 
####setWorkPages: 
[&wait] Set the WorkPages links in the database, 
####showMonths: 
List installed monthnames,
####showJobs: 
show status of running jobs, 
####setBookUnlock: 
&id= unlock book details, 
####setAuthorImage: 
&id= &img= set a new image for this author
####setAllBookSeries: 
[&wait] Set the series details from goodreads or librarything workpages, 
####showThreads: 
show threaded processes, 
####setAuthorUnlock: 
&id= unlock author name/image/dates, 
####searchBook: 
&id= [&wait] [&type=eBook/AudioBook] search for one book by BookID, 
####readCFG: 
&name=&group= read value of config variable \name\ in section \group\, 
####refreshAuthor: 
&name= [&refresh] reload author (and their books) by name, optionally refresh cache, 
####renameAudio: 
&id Rename an audiobook using configured pattern, 
####restart: 
restart lazylibrarian, 
####removeMagazine:
&name= remove magazine and all of its issues from database by name, 
####removeAuthor: 
&id= remove author from database by AuthorID, 


####addBook: 
&id= add book details to the database, 
####deleteEmptySeries: 
Delete any book series that have no members, 
####getMagazines: 
list magazines, 
####listIgnoredBooks: 
list all books in the database marked ignored, 
####moveBook: 
&id= &toid= move one book to new author by BookID and AuthorID, 
####restartJobs: 
restart background jobs, getRead: list read books for current user, exportCSVwishlist: [&wait] [&dir=] Export a CSV wishlist to named or alternate directory, 
####setWorkID: 
[&wait] [&bookids] Set WorkID for all books that dont have one, or bookids, 
####saveTable: 
&table= Save a database table to a file, 

####getBookCover: 
&id= [&src=] fetch cover link from cache/cover/librarything/goodreads/google for BookID,
####logMessage: 
&level= &text= send a message to lazylibrarian logger, 
####getVersion: 
show lazylibrarian current/git version, 
####showCaps: 
&provider= get a list of capabilities from a provider, 
####getToRead: 
list to-read books for current user, 
####listMissingWorkpages: 
list all books with errorpage or no workpage, 
####syncCalibreList: 
[&toread=] [&read=] sync list of read/toread books with calibre, 
####findAuthor: 
&name= search goodreads/googlebooks for named author, 
####grSync: 
&status= &shelf= [&library=] Sync books with given status to a goodreads shelf,
####getSnatched: 
list snatched books, 
####forceActiveAuthorsUpdate: 
[&wait] [&refresh] reload all active authors and book data, refresh cache, 
####pauseAuthor: 
&id= pause author by AuthorID, 
####getHistory: 
list history, 
####writeAllOPF: 
[&refresh] write out opf files for all books, optionally overwrite existing opf, 
####setBookImage: 
&id= &img= set a new image for this book, 
####queueBook: &id= 
[&type=eBook/AudioBook] mark book as Wanted, default eBook, 
####getSeriesMembers:
 &id= Get list of series members using SeriesID, 
####checkRunningJobs: 
ensure all needed jobs are running, 
####forceLibraryScan: 
[&wait] [&remove] [&dir=] [&id=] rescan whole or part book library, 
####getBookCovers: 
[&wait] Check all books for cached cover and download one if missing, 
####shutdown: 
stop lazylibrarian, 
####forceAudioBookScan: 
[&wait] [&remove] [&dir=] [&id=] rescan whole or part audiobook library, 
####getAllBooks: 
list all books in the database, 
####addAuthor: 
&name= add author to database by name, 
####getAuthorImages: 
[&wait] get images for all authors without one, 
####writeOPF: 
&id= [&refresh] write out an opf file for a bookid, optionally overwrite existing opf, 
####resumeAuthor: 
&id= resume author by AuthorID, 
####setAllBookAuthors: 
[&wait] Set all authors for all books from book workpages, 
####setBookLock: 
&id= lock book details, 
####listNoISBN: 
list all books in the database with no isbn, 
####getIndex: 
list all authors, 
####forceProcess: 
[&dir] [ignorekeepseeding] process books/mags in download or named dir, 
####getAuthorImage: 
&id= get an image for this author, 
####listNoLang: 
list all books in the database with unknown language, 
####setAuthorLock: 
&id= lock author name/image/dates, 
####checkModules: 
Check using lazylibrarian library modules, 
####getWorkSeries: 
&id= Get series from Librarything BookWork using BookID or GoodReads using WorkID, 
####getWorkPage: 
&id= Get url of Librarything BookWork using BookID, 
####grUnfollow: 
&id= Unfollow an author on goodreads, 
####createMagCover: 
&file= [&refresh] [&page=] create cover for magazine issue, optional page number, 

####searchItem: 
&item= get search results for an item (author, title, isbn), 




####update: 
update lazylibrarian, 
####unqueueBook: 
&id= [&type=eBook/AudioBook] mark book as Skipped, default eBook, 
####vacuum: 
vacuum the database, 
####writeCFG: 
&name=&group=&value= set config variable \name\ in section \group\ to value,
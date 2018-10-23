#Importing
<img src="/assets/screenshots/config_importing.png" width="800">


## Information Sources
Currently only supports GoodReads, GoogleBooks and LibraryThing
### GoodReads API
Access key for GoodReads

### GoodReads Sync
LazyLibrarian is supplied with a default goodreads api key which is read-only, and gives access to search functions.    
If you want to sync your goodreads bookshelves with lazylibrarian you will need to get your own key and secret from [GoodreadsApi](https://www.goodreads.com/api/keys). Once you have your own key/secret enter them in lazylibrarian config and save the config. You can then obtain your goodreads oAuth token/secret to get write access to your goodreads account.  
You can select whether a book is allowed to be on both shelves. If using the default goodreads to-read/read shelves goodreads will override this and only allow the book on one shelf (you've either read it or you haven't) If using your own shelves they can be used as owned/read instead if you wish, so a book can be on both shelves.  
Press "Request oAuth1". A new goodreads window will open where you can confirm you want to give access to lazylibrarian. Once confirmed, press "Request oAuth2" to read and store the credentials in lazylibrarian config.  
You can now configure the bookshelves to use. You can use existing goodreads shelves or lazylibrarian can create new ones. Lazylibrarian supports two shelves, one for books you want, and another for books you have. You can also define how often the sync should occur.  The "Test Authorisation" button will check your credentials are entered correctly.

### GoogleBooks API
If you have an access key for GoogleBooks, enter it here.
GoogleBooks has a different range of books to GoodReads for some authors.
Try both and see which suits your library best.

### LibraryThing Developer Key
If you have one we can use it as another source for downloading covers. All other librarything functions that we use don't need a developer key.

## File Formats
### eBooks
Comma separated list of file extensions for eBooks. Default epub, mobi, pdf
### AudioBooks
Comma separated list of file extensions for eBooks. Default mp3
You may find m4a is also useful depending on your audiobooks
### Magazines
Comma separated list of file extensions for Magazines. Default pdf  
Most magazines seem to be pdf

## Various settings to do with importing books
* Ignore books with future publication date  
Don't try to download them yet. Authors are rescanned periodically so the book will be un-ignored after the date passes
* Ignore books with unknown publication date  
Goodreads sometimes has incomplete information, you can choose to ignore these books
* Ignore books with no isbn  
If you don't ignore these we will try to look up the isbn elsewhere, which can be slow
* Add ignored books to database  
For any of the above "Ignore" switches, you can add the book to the database marked as Ignored, or not create a database entry at all.
* Try google image search as final option for missing book covers  
If all else fails, try google image. You will get a cover, but it might not be correct. Google always gives you something even if it can't find the book you want. You can always search for a cover manually.
* Delete csv file or wishlist after successful import  
Automatic tidy up. The list will not be deleted if any books in it could not be matched.
* Blacklist failed downloads in history table  
This will allow an automatic retry of a different download. If the failure was a communication problem you might want to retry the same download, but if the failure was a corrupt file or an unwanted format you want to get a different download. Could become automated at a future date.
* Blacklist processed downloads in history table  
If the download succeeded but you don't like the copy, you can mark the book as wanted again. If this box is not ticked you will probably download the same copy. Tick this box to force a different one.

NOTE: The blacklists use the entries in the history table, so if you clear the history the blacklists will not work.

## Language
### Import Languages
Comma separated country shortcodes for languages of books to add to the library:
GoodReads e.g: eng, en-US, spa, ita
GoogleBooks e.g: en, es, it
Default: en, eng, en-US
Try adding "Unknown" to list if GoodReads is missing results, or put "All" if you 
don't want to check for language, but beware you could fill the library with lots of
books in languages you can't read, as some of authors are translated into many languages.
When you add an author to the database, LazyLibrarian uses this list to decide whether 
to include a book or not. Books that say they are in a language that is not in this list
will be ignored (unless language set to All). At the end of a library scan or adding an 
author the log will say how many books were ignored for language reasons. If you have debug 
logging on, each book that is ignored will be listed with the language we think it is.  
GoodReads and GoogleBooks currently seem to have lots of books with "Unknown" language.
Hopefully this will improve over time. LazyLibrarian tries to match as many as possible to
a language using the book ISBN (if we know it) which reduces the unknown ones. We use LibraryThing
for this. www.librarything.com

### Languages for Month Names
Comma separated list of language codes. Default: blank  
Magazine Issues usually have a month in the title, eg "PC Gamer July 2014"  
We use this month name to decide how old the magazine is, and so whether to download it.
English month names are built in. If you want to include French magazines, add fr_FR.utf8
The language name, eg "fr_FR.utf8" needs to exactly match the ones listed in your system locale (try locale -a to get a list of the languages installed on your machine) 
   
Alternatively you can supply a pre-built list of monthnames. Useful if you want magazine monthnames in a locale not available on the machine running lazylibrarian (eg docker containers).  Copy the supplied example.monthnames.json to your lazylibrarian data directory (the one containing your database and config.ini) and name it monthnames.json, edit as required. The example file is English and Spanish and looks like this...  
`[["en_GB.UTF-8", "en_GB.UTF-8", "es_ES.utf8", "es_ES.utf8"], ["january", "jan", "enero", "ene"], ["february", "feb", "febrero", "feb"], ["march", "mar", "marzo", "mar"], ["april", "apr", "abril", "abr"], ["may", "may", "mayo", "may"], ["june", "jun", "junio", "jun"], ["july", "jul", "julio", "jul"], ["august", "aug", "agosto", "ago"], ["september", "sep", "septiembre", "sep"], ["october", "oct", "octubre", "oct"], ["november", "nov", "noviembre", "nov"], ["december", "dec", "diciembre", "dic"]]`  
  
Note that each language is listed twice, once with full month name and again with the "short" name, and all month names are lower-case and un-accented 

## Date Formats
* Format for Added Columns  
Dates when we added a book/magazine to the library
* Format for Issue Date  
How to display magazine issue dates    
Dates are stored internally in a format useful for sorting, but for display you might want to show something more readable. 

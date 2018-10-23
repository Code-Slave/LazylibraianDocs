**Bookstrap interface only.**  
If you enable user accounts in config you can have multiple different users with limited access to lazylibrarian. When you first enable user accounts, your existing WebServer User and WebServer Password are used as the admin account. If you do not currently require webserver login, a default account will be set up with user and password "admin". The WebServer entries can be removed from config once user accounts are active. 

You will need to enter an admin email address which you can monitor for messages from users. This email address is used for registration requests, or if a user with limited access wants something they cannot access themselves. An email will be sent to this address with details of the request.

User admin is accessed via a button in config. 
You can create users with default preset permissions of Admin, Friend, Guest, or use a custom value of your choice.

Admin has full access, Friend has read/write access, Guest is read only.
Friend can alter the status of books and authors (delete books, get books added to your library etc) but Guest can only download what's already there, and needs to ask admin to get missing books.

Create some dummy users with friend/guest permissions to see how they work.

When an admin adds a new user, the user receives an email giving their user name and password.   
The passwords are randomly generated or type your own, and all user names must be unique.  
Admin can change anyone's name/email/password. Non-admin can only change their own.  
Logins are session based using a browser cookie.  
A Logout button is on every page, or close your browser to log out.

Custom permissions are a bitmask, used as follows...
* 1    Admin, access to config page
* 2    access to logs
* 4    access to history
* 8    access to manage page
* 16   access to magazines/issues/pastissues
* 32   access to audiobooks page
* 64   access to ebooks page
* 128  access to series/seriesmembers
* 256  can edit book or author details
* 512  can search goodreads/googlebooks for books/authors
* 1024 can change book status (wanted/skipped etc)
* 2048 can use background tasks (refresh authors/libraryscan/postprocess/searchtasks)
* 4096 can download existing books/mags

Default admin setting is everything enabled  
Default guest setting is ebooks/audiobooks/magazines/series/download  
Default friend is guest plus search/change_status

Each user has their own "sync to calibre" lists where their bookmarks can be synced. Only admin can set these up as the column names need to be unique so one user cannot overwrite anothers bookmarks.

Each user can also specify their preferred download type which is used in preference to the system default type (leftmost entry in the booktypes list). eg if the user has a kindle they can ask for mobi when they click "Open" even if the system default is epub. If their chosen default isn't available, or if they haven't set a preference, they get a popup offering other choices
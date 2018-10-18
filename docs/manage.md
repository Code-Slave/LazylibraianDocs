<img src="https://imgur.com/Hx9tLdc.png" width="800">

The menu bar has four buttons <img src="https://imgur.com/7U0vqBj.png" width="400"><br> 
**[Import Books]** imports books from the "Alternate Directory" defined in config. It will copy/move books into the lazylibrarian library folder, adding authors as necessary. You can control the process using settings in Config->Processing.<br>"Keep original files" will "copy" rather than "move" the files from the alternate folder.<br>"Only import one format" will only copy the "preferred" format (the first one found, counting from the left, in Config->Importing->File Formats) "Add Authors" will allow authors to be added if they are not already in the library. If "Include Other Books By New Authors" is ticked, all the authors books will be listed in the library, not just the ones found in the alternate directory. "New Book/Audiobook Status" sets what status to give the authors other books.

**[Include Books]** is similar, but it does not copy or move the books, just creates links to them in their "Alternate Directory" location. Lazylibrarian stores the full path to the books, so you can change Alternate Directory without losing the books. This allows you to link lazylibrarians database to multiple book locations.

**[Export CSV wishlist]** exports a list of all books marked "Wanted" in your library. Note this is just eBooks. There is currently no equivalent functionality for AudioBooks or Magazines.

**[Import CSV Wishlist]** will re-import a lazylibrarian list, or a csv file from GoodReads or other sources. To be compatible, the CSV file needs to contain columns headed "Title" and "Author", and optionally a bookid and isbn. Any other columns are ignored. Books imported via a wishlist are added as "Wanted", and if their authors are not already in the library they are added using the same settings described for "Import Books" earlier in this page. Note this is also eBook only.

After this are toggles, rows per page and results filter as described in the homepage.

In the table, clicking on the book cover image shows a larger image. Clicking the author name takes you to the authors page. Under the book title are buttons eg **GoodReads  LibraryThing  Manual** (not all books have all options).  Goodreads/GoogleBooks/Librarything  take you to the relevant books page on the provider. Manual takes you to a page where you can edit the book details or perform manual searches. See Pages: Manual later in the wiki.
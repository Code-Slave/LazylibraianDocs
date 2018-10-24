#Providers
<img src="/assets/screenshots/config_providers1.png" width="800">

##Newznab Providers
For each newznab provider, enter the following details. When you fill a provider slot
and save it, a new empty slot appears.

* URL
eg https://api.nzbplanet.net
* API
Your personal api as supplied by the newznab provider  
Newznab and nZEDb use different categories for ebooks and magazines. LazyLibrarian queries them for capabilities, but not all providers give enough info.
If you get errors in the log from newznab searches saying "unknown function" or similar, please read the "filters" section.

##Torznab Providers
Torznab is a method for indexing and searching torrents. See [https://github.com/Jackett/Jackett](https://github.com/Jackett/Jackett)

* URL
URL of the torznab/jackett indexer
* API
Your api key for the torznab/jackett indexer

##RSS/WishList Providers
Only plain rss feeds or rss feeds with embedded credentials are known to work, eg  

http://kat.cr/books/?rss=1  
https://www.usenet-crawler.com/rss?t=7020&dl=1&i=xxxxxx&r=xxxxxxxxxxxxxxxxxxxxxxxx  
Feedback on other sites (working or not) would be appreciated

* URL  
URL of feed, or feed with embedded credentials 

```
 NOTE: Goodreads RSS wishlists or Listopia html pages can also be entered as an 
 RSS provider feed, as can New York Times best-sellers pages, 
 eg https://www.nytimes.com/books/best-sellers/ These will be scanned 
 periodically for changes like a true rss feed, and lazylibrarian will attempt 
 to download all books found in the list. As some listopia lists can be 
 quite long you can limit the number of pages to return



```

<img src="/assets/screenshots/config_providers2.png" width="800">

##Torrent Providers
Currently only the built in sites are known to work.
Feedback on other sites (working or not) would be appreciated.
New sites _may_ be added on request

##Direct Download Providers
Currently only libgen is available. There are two entries for libgen, so you can use the main search and also the foreignfiction search. Note that "foreign" in this context means non-russian

##Priorities
Most providers have an optional Priority setting. If the same download is available from more than one provider we request it from the one with the highest priority, this means you can prefer nzb over torrent, one torrent source over another etc.  

* Downloads are ranked according to how closely they match the required author/title first, priority is the second filter. This means if there are equally good matches at more than one provider the priority is used to decide, otherwise we grab the "best" match ignoring any priority settings.

##Types
Valid types are one or more of (A)udio (E)book (M)agazine  

* We will only search the provider for an ebook if there is an E in the Types entry for the provider. This means you can skip searching providers that aren't relevant, eg libgen doesn't do audiobooks  
* For a wishlist, the types entry is used when searching for entries in the wishlist, eg you can just download the New York Times best sellers as audiobooks if you want.

##Blocked Providers button
If a provider returns an error we block access to it for a limited time. Usually it's a communication error or a daily limit exceeded. The button shows a popup of blocked providers and allows you to unblock them if you wish rather than wait for the timer to expire.

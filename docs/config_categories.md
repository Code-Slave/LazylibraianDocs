You only need to change the settings on this page if auto-detection fails or returns incorrect values. If you make any alterations, tick the lock button to prevent reloading values from the provider. Settings are reloaded according to the main cache expiry setting, or whenever the provider host name changes. To force a reload, edit the provider host name, save, then put the provider host name back. On next book search the values will be reloaded from the provider. Many sites do not correctly report their capabilities to us. Most newznab sites support book search but don't say so, but we try anyway. Most nzedb servers do not support book search, so we don't try on those. If you get a message in the logs saying "unknown parameter" or "incorrect parameter" or "unknown function" it's probably because that provider can't do a book search so edit this field and leave it blank. Do not blank the category numbers for books or magazines as these are also used in some general searches. There is no specific magazine search in either type of provider yet, so leave this blank for now.  

## For each provider

* Tick box to lock settings - prevents reloading on cache expiry time
* General search  - normally just "search"
* Extended search - normally "1"
* Book search - normally "book" on newznab, sometimes "books" on nzedb, most nzedb leave blank as no specific book search on these providers.
* Magazine search - normally blank, no specific magazine search available yet
* Book categories - varies from provider to provider, 7000 range for newznab, 8000 range for nzedb
* Magazine categories - varies, usually a sub-category of books

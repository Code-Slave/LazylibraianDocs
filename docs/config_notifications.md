#Notifications
<img src="/assets/screenshots/config_notifications.png" width="800">

For all the notifiers, Notify on Snatch sends a message whenever a book/magazine is sent to one of the
downloaders. Notify on Download sends a message when a snatched book/magazine has been successfully
downloaded and added to the library. Some notifiers have the ability to send a test message to check the notifications work. For notifiers that can send to multiple devices, the test message will return a list of valid device IDs.

##Enable Twitter Notifications
* Notify on Snatch
* Notify on Download
* Request Authorisation
* Twitter Key
* Verify Key
* Test Twitter

## Enable Boxcar Notifications
* Notify on Snatch
* Notify on Download
* Boxcar Token

## Enable Pushbullet Notifications
* Notify on Snatch
* Notify on Download
* Pushbullet API
* Device ID
* Test Pushbullet

## Enable Pushover Notifications
* Notify on Snatch
* Notify on Download
* Pushover API
* Keys
* Device
* Priority
* Test Pushover

## Enable AndroidPN
* Notify on Snatch
* Notify on Download
* Broadcast
* AndroidPN Notification URL
* Username
* Test AndroidPN

## Enable NotifyMyAndroid
* Notify on Snatch
* Notify on Download
* API key
* Priority
* Test NMA

## Enable Email Notification
* Notify on Snatch
* Notify on Download
* Email From address
* Email To address
* SMTP Server address
* SMTP user and password
* SMTP port
* Use SSL
* Use TLS
* Test Email

## Enable Custom Notification
This is a special notifier, which is a script to run. There are some example scripts with lazylibrarian. You can use it, for example, to notify a system we don't support yet. There is an example script in python and another in bash that shows how the notifiers work. There is also example_ebook_convert.py that can be used as a notifier to make sure you have a copy of both mobi and epub for all new downloads. It uses calibre ebook-convert to create one format from another. Use it as a base for your own notifiers. The notifiers are passed a list of database columns for a book or magazine, and details of the download source. See the examples for full details.

If you create any other notifiers that you think might be useful to others, please upload them!
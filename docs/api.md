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
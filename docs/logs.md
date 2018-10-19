Very simple table, nothing to alter, just info.

##Menu

The menu bar has two or three buttons

<img src="https://imgur.com/nbhdzlE.png" width="300">

- **[Clear Log]** clears the on screen log and also the log files.  
- **[Start Debug Log]**
- **[Stop Debug Log]** turn debug logging on/off. You can also do this by setting loglevel in config, but the buttons are useful for getting focused debug logs to help tracking down problems.

When debug logging is ON you get a third button **[Save Debug Log]** This will save an anonymised debug log working backwards from when you press "save debug log" until the most recent "start debug log" message. Details of your lazylibrarian installation will be included in the log (operating system, installation type, python version, interface used) and the log lines will have all passwords and api keys removed. The log is saved as "debug.zip" in the lazylibrarian log folder (location is also shown on screen in the log page). You can unzip and inspect the log, or upload it with a bug report.
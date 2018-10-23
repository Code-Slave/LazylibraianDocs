
##Config MenuBar

Most of these are pretty selfexplanatory.

<img src="/assets/screenshots/config_menus.png" width="800">

- **[Shutdown]** Shuts The system Down
- **[Restart]** Restarts LazyLibrarian
- **[System Info]** Gives some version and system info. Helpful for debugging.

```
Startup cmd: ['/usr/bin/python', '/app/lazylibrarian/LazyLibrarian.py', '--datadir', '/config', '--nolaunch']
Interface: bookstrap
Loglevel: 3
Sys_Encoding: UTF-8
git_repo: lazylibrarian
git_user: dobytang
git_branch: master
latest_version: a4fd6e6241cb9cb8427ffd732fa53a6abd13a68b
git_updated: Mon Oct 22 19:49:21 2018
current_version: a4fd6e6241cb9cb8427ffd732fa53a6abd13a68b
commits_behind: 0
install_type: git
auto_update: 1
Python version: ['2.7.15 (default, Aug 16 2018, 14:17:09) ', '[GCC 6.4.0]']
Distribution: ('', '', '')
System: Linux
Machine: x86_64
Platform: Linux-4.18.8-unRAID-x86_64-with
uname: ('Linux', '23c4ed4cd40f', '4.18.8-unRAID', '#1 SMP Sat Sep 15 09:15:50 PDT 2018', 'x86_64', '')
version: #1 SMP Sat Sep 15 09:15:50 PDT 2018
mac_ver: ('', ('', '', ''), '')
urllib3: 1.24
requests: 2.20.0
tls: TLS 1.2
cherrypy: 3.6.0
sqlite3: 3.24.0
unrar: DLL version 8
openssl: LibreSSL 2.7.4
pyOpenSSL: 18.0.0
cryptography: 2.3.1
magic: missing
```

- **[Job Status]** Shows status of all jobs. Has Obtions to stop current running jobs and restart jobs

<img src="/assets/screenshots/job_status.png" width="800"> 

- **[Check Version]** Check to be sure LazyLibrarian is running latest version. if not it asks if you want to upgrade.
- **[UserAdmin](config_users.md)**
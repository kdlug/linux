# Linux malware and rootkit tools
## chrootkit
chkrootkit is a rootkit scanner. Read more http://www.chkrootkit.org/.  
Installation od Debian:
`apt-get install chkrootkit`  
Run: `chrootkit`
```sh
ROOTDIR is `/'
Checking `amd'...                                           not found
Checking `basename'...                                      not infected
Checking `biff'...                                          not found
Checking `chfn'...                                          not infected
Checking `chsh'...                                          not infected
Checking `cron'...                                          not infected
Checking `crontab'...                                       not infected
Checking `date'...                                          not infected
Checking `du'...                                            not infected
Checking `dirname'...                                       not infected
```
## rkhunter
A tool for scanning system for suspicous rootkits, backdoors and exploits.   
Installation on Debian:
`apt-get install rkhunter`  
First we have to check for updates:
`rkhunter --update`
```sh
[ Rootkit Hunter version 1.4.2 ]

Checking rkhunter data files...
  Checking file mirrors.dat                                  [ No update ]
  Checking file programs_bad.dat                             [ No update ]
  Checking file backdoorports.dat                            [ No update ]
  Checking file suspscan.dat                                 [ No update ]
  Checking file i18n/cn                                      [ No update ]
  Checking file i18n/de                                      [ No update ]
  Checking file i18n/en                                      [ No update ]
  Checking file i18n/tr                                      [ No update ]
  Checking file i18n/tr.utf8                                 [ No update ]
  Checking file i18n/zh                                      [ No update ]
  Checking file i18n/zh.utf8                                 [ No update ]
```
To update databases run: `rkhunter --propupd`
```sh
[ Rootkit Hunter version 1.4.2 ]
File updated: searched for 176 files, found 146
```

To run scanning process: `rkhunter -c -sk`
```sh
Checking the local host...

  Performing system boot checks
    Checking for local host name                             [ Found ]
    Checking for system startup files                        [ Found ]
    Checking system startup files for malware                [ None found ]

  Performing group and account checks
    Checking for passwd file                                 [ Found ]
    Checking for root equivalent (UID 0) accounts            [ None found ]
    Checking for passwordless accounts                       [ None found ]
    Checking for passwd file changes                         [ None found ]
    Checking for group file changes                          [ None found ]
    Checking root account shell history files                [ OK ]

  Performing system configuration file checks
    Checking for an SSH configuration file                   [ Found ]
    Checking if SSH root access is allowed                   [ Warning ]
    Checking if SSH protocol v1 is allowed                   [ Not allowed ]
    Checking for a running system logging daemon             [ Found ]
    Checking for a system logging configuration file         [ Found ]
    Checking if syslog remote logging is allowed             [ Not allowed ]

  Performing filesystem checks
    Checking /dev for suspicious file types                  [ None found ]
    Checking for hidden files and directories                [ None found ]


System checks summary
=====================

File properties checks...
    Files checked: 146
    Suspect files: 0

Rootkit checks...
    Rootkits checked : 379
    Possible rootkits: 0

Applications checks...
    All checks skipped

The system checks took: 35 seconds

All results have been written to the log file: /var/log/rkhunter.log

One or more warnings have been found while checking the system.
Please check the log file (/var/log/rkhunter.log)

```
If you want to disable some warnings, f.ex.  
```sh
Checking if SSH root access is allowed                   [ Warning ]
```
You have to edit config file `vi /etc/rkhunter.conf` and change (uncomment) the value `ALLOW_SSH_ROOT_USER=no` to `ALLOW_SSH_ROOT_USER=yes`.



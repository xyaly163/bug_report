BUG_Author: Xue Yue

Vulnerability url: /music_player/save_music.php

post form-data parameter 'filename' exists arbitrary file upload

Steps to reproduce

1.Click on + Add

2.Upload the picture Trojan horse,and append the file suffix .php through BurpSuite

![image](https://github.com/xyaly163/bug_report/blob/main/upload.png)

3.Access to upload picture Trojan links,you can execute any command.

For example,whoami command.

![image](https://github.com/xyaly163/bug_report/blob/main/upload2.png)

# `wget`

## 1. Intro
GNU Wget is a free software package for retrieving files using HTTP, HTTPS, FTP and FTPS the most widely-used Internet protocols. It is a non-interactive commandline tool, so it may easily be called from scripts, cron jobs, terminals without X-Windows support, etc. 

## 2. [Basic Usage](https://www.jianshu.com/p/59bb131bc2ab)
* `wget src_address`: download a file and save in current directory
* `wget -o alias.ext src_address`: download and save file with a specified name and extension name (wget默认会以最后一个符合”/”的后面的字符来命令，对于动态链接的下载通常文件名会不正确。)
* `wget -c src_address`: continue corrupted download

## 3. Download a single file from GitHub using `wget`
`wget -o alias.ext raw_file_address`
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MzUwNjg3MjddfQ==
-->
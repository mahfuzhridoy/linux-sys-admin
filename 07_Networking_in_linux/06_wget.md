# Downloading with wget
`wget` is a command lone tool for downloading files from http, https, and ftp servers. This comes with features like downloading multiple files, resume download, mirror a website and many things. This is by default installed in many linux distros. If its not then can be installed with `sudo apt install wget`.

#### Downloading file
To download a file, simple command structure: `wget [file url]`. To specify a download directory `-P` option can be used. Example command: `wget -P directory/ [file url]`. Other useful options include:

* `--limit-rate=100k` this will limit the download speed to 100 kb. the bandwidth can be changed to any speed like 100 m or g.

* `-c` resumes the download. By default when a download gets cancelled and download again, the download starts from the start again. But using -c option resumes the download from where it got cancelled.

* `-i` lets download multiple files at once. Example command: `wget -i url-list.txt`. Here url-list.txt contains the url list of files to be downloaded.

* `-b` puts the download in the background. and `nohup` can be combined with this to continue download even if the terminal gets closed. This is useful when downloading large files. Example command: `nohup wget -b http://example.com`. The status of download can be checked in the `wget-log` with `tail -f wget-log`.

#### Mirroring a website
Mirroring a website meand downloading it as it is for viewing the website when offline. This can be done using `wget --mirror --convert-links --adjust-extension --page-requisites --no-parent http://example.com`.
**Meaning of each options:**

- `--mirror` makes the download recursive.

- `--convert-links` will convert the links to a relative path that are included inside a web-page e.g. style.css, script.js for helping in offline view.

- `--adjust-extension` will add suitable extensions to the file names like css or html based on their content. 

- `--page-requisites` will download style sheets or images to propery display the website offline.

- `--no-parent` is necessary for not to ascend to parent directories. This restricts the download to only a part of the website. 

There is a shorter version of this command which is: `wget -mkEpnp`


Prior to Zen Cart v2, downloads had to be placed in the folder pointed to by the `DIR_FS_DOWNLOAD` define in `admin/includes/configure.php`.  Now downloads may be hosted externally.  The following options are provided: 

- AWS Hosting: Use `aws:bucketname/filename.ext` as the filename in attributes controller, with expiring links to prevent theft

- Dropbox: Change the URL parameter `dl=0` to `dl=1` on the "sharing link" that Dropbox gives you



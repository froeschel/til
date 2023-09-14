# CORS setup

In our case we store asset files on Azure Blob Storage and serve them through Azure CDN. This works fine, but there is one issue with fonts. Font files will be blocked with a CORS error. To solve this one needs to add the sites which access the files to the bolob storage CORS rules. 

When testing the setup it is important to purge the files from the CDN after changes to the CORS rules have been made. This way we make sure the new rules are applied to the cached files.  
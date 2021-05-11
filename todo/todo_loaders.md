Loaders
=======

Origin
 
- store resource in matter (ipfs) and 'symlink' from original URL
    - https://thatsme.plus/wp-content/uploads/2020/12/logo.png
    - https://fonts.googleapis.com/icon?family=Material+Icons
    - https://fonts.gstatic.com/s/materialicons/v85/flUhRq6tzZclQEJ-Vdg-IuiaDsNcIhQ8tQ.woff2
    - be extremly restictive! This is a tracking source!

- allow fetch with whitelist (regex)
    - see puls.mjs -> ALLOWED_WEB_REQUESTS
    - Move hardcoded links to settings (file or resource)
    - implement better check (method, ...) if it can be redirected
    - be extremly restictive! This is a tracking source!

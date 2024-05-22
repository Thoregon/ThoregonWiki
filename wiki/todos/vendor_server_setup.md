# todo

refactor resource service
- second service in docker-compose
- url -> vendor
- service/port -> docker-compose  
- dir -> docker-compose volume mapping to www/upayme/res/${vendorid}

use caddy API
- https://caddyserver.com/docs/api

# caddy


## vendor config

replacements
- ${vendorid} 
- ${vendorport}

```
# -------------------------------
# ${vendorid}
# -------------------------------

${vendorid}.upay.me {
    # root for all requests
    root * /www/upaymeui

    # point to the vendor's ${vendorid} config
    uri replace /etc/ /.etc/${vendorid}/ # config for vendor

    # resources supplied by vendor
    @post_res {
        method POST
        path /res/*
    }
    reverse_proxy @post_res upaymeresource${vendorid}:${vendorport}
    uri replace /res/ /res/${vendorid}/ # resources for vendor (images, pdf, ...)
    
    # rewrites and redirects to JS modules (defined in config/common)
    import modules
    
    # proxy upayme services
    reverse_proxy /redir/* upayme${vendorid}:${vendorport}   # port to the vendors service agent
    reverse_proxy /content/* upayme${vendorid}:${vendorport}   # port to the vendors service agent
    reverse_proxy /checkout/* upayme${vendorid}:${vendorport}   # port to the vendors service agent
    
    # now provide all resource  
    file_server
    
    # display a vendor specific splash screen if not found
    handle_errors {
        rewrite * /upayme-${vendorid}-splash.html
        file_server
    }
}
```

# container

directories:
- container/${vendorid}
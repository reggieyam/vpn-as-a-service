# vpn-as-a-service


# Overview

![Flowchart](flowchart.png)

# Using API

Mockup API: ```http(s)://5b3ec26ac3c3fb00147427f6.mockapi.io/api/v1/:endpoint```

## Endpoint vpn user ##

   * `get /vpnuser/:id`: return object of vpnuser with specific id
   
       | Name            | Value            | Description                           |
       |-----------------|------------------|---------------------------------------|
       | id              | uuid             | userId                          |
       | createdAt       | unixtime         | timestamp at which object was created |
       | username        | string | username for ikv2 vpn service        |
       | password        | string                 | password for ikv2 vpn service         |
       | secret                | string                 | secret for ikv2 vpn service   |
       | email                |  email                | registered email         |
       | enable                |  Boolean                | status of user         |
       
   * `post /vpnuser`: create vpnuser, body in json format

       | Name            | Value            | Description                           |
       |-----------------|------------------|---------------------------------------|
       | id              | uuid             | userId                          |
       | createdAt       | unixtime         | timestamp at which object was created |
       | username        | string | username for ikv2 vpn service        |
       | password        | string                 | password for ikv2 vpn service         |
       | secret                | string                 | secret for ikv2 vpn service   |
       | email                |  email                | registered email         |
       | enable                |  Boolean                | status of user         |

   * `put /vpnuser`: updated object vpnuser
   * `delete /vpnuser`: deleted object vpnuser
   
## Endpoint vpn server ##
   * `get /vpnserver`: return array of vpn servers 
   * `get /vpnuser/:geo`: return object of vpn server by geo id

       | Name            | Value            | Description                           |
       |-----------------|------------------|---------------------------------------|
       | hostname              | string             | hostname of vpn server, resolveable via public DNS                          |
       | geo       | ISO 3166 Country Codes         | The country codes can be represented either as a two-letter code (alpha-2) |
   


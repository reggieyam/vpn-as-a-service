# vpn-as-a-service

# Using API

Mockup API: ```http(s)://5b3ec26ac3c3fb00147427f6.mockapi.io/api/v1/:endpoint```

## Endpoint vpnserver ##
   * `get /vpnuser`: return array of vpnusers
   * `get /vpnuser/:id`: return object of vpnuser with specific id
   * `post /vpnuser`: created object vpnuser
   * `put /vpnuser`: updated object vpnuser
   * `delete /vpnuser`: deleted object vpnuser

   * `post /vpnuser/`: create vpnuser, body in json format


       | Name            | Value            | Description                           |
       |-----------------|------------------|---------------------------------------|
       | id              | uuid             | auth0 userId                          |
       | createdAt       | unixtime         | timestamp at which object was created |
       | username        | string | username for ikv2 vpn service        |
       | password        | string                 | password for ikv2 vpn service         |
       | secret                | string                 | secret for ikv2 vpn service   |
       | email                |  email                | registered email         |
       | enable                |  Boolean                | status of user         |

   



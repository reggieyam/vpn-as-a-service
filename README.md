# vpn-as-a-service


# Overview

![Flowchart](flowchart.png)

# Using API

Mockup API: ```http://cb.atspeeds.com:8080/:endpoint```

## Endpoint vpn user ##

   * `get /clients`: GET all clients
   
   * `get /clients/:id`: GET client with specific id (phone)
   
       | Name            | Value            | Description                           |
       |-----------------|------------------|---------------------------------------|
       | id              | uuid             | phone number                          |
       | username        | string | username for ikv2 vpn service        |
       | password        | string                 | password for ikv2 vpn service         |
       
   * `post /clients`: CREATE client, body in json format
      
      Example of Request body JSON
        
       `{ 
	      "userId": "33vpn.com|13600000003",
        "ip": "47.75.166.162"
       }`

       | Name            | Value            | Description                           |
       |-----------------|------------------|---------------------------------------|
       | userId              | string             | domain + phone number (mandatory)                          |
       | ip       | string         | ip address of client (optional) |
       
      Example of Response
      `{
    "domain": "33vpn.com",
    "userId": "13600000001",
    "username": "13600000001",
    "password": "KxUvhF",
    "server": "vpn.atspeeds.com",
    "protocol": "IKEv2",
    "secret": "atspeeds"
      }`
            
       | Name            | Value            | Description                           |
       |-----------------|------------------|---------------------------------------|
       | domain              | string             | extract from userId                         |
       | userId       | string         | phone number |
       | username        | string | username for ikv2 vpn service        |
       | password        | string                 | password for ikv2 vpn service         |
       | secret                | string                 | secret for ikv2 vpn service   |
   
   * `put /clients/:phone`: Update vpn client by phone
   
   * `delete /clients/:phone`: Delete VPN client by phone
 
   


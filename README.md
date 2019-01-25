# vpn-as-a-service

# Using APIv2

API: ```https://api.atspeeds.com/v2/:endpoint```

## Endpoint vpn user
* `POST /v2/sendsmscode?apikey=<apikey>`: Send SMS verification code

   | Name            | Type             | Description                           |
   |-----------------|------------------|---------------------------------------|
   | countryCode     | string           | The phone's country code.             |
   | phoneNumber     | string           | The phone number to send the verification code.              |
   | domain          | String           | Domain name                           |

   Example of Request body json
    ```JSON
    {
      "countryCode": "86",
      "phoneNumber": "13600000000",
      "domain": "33vpn.com",
    }
    ```

* `POST /v2/signup?apikey=<apikey>`: User Signup

  | Name            | Type             | Description                           |
  |-----------------|------------------|---------------------------------------|
  | countryCode     | string           | The phone's country code.             |
  | phoneNumber     | string           | The phone number to send the verification code.|
  | userPass        | BASE64           | Password for customer login           |
  | domain          | String           | Domain name                           |
  | verificationCode| String           | The verification code from the user that is being validated.  |

  Please approach administrator for apikey

  Example of Request body JSON

   ```json
   {
	"countryCode": "86",
	"phoneNumber": "13600000000",
  "userPass": "c3RhY2thYnVzZS5jb20=",
	"domain": "33vpn.com",
  "verificationCode": "668688"
   }
   ```

  Example of Respons body

   ```json
   {
	"credential": {
		"domain": "33vpn.com",
		"userId": "86136000000008",
		"userPass": "c3RhY2thYnVzZS5jb20=",
		"username": "8613600000008",
		"password": "f2wq6A"
	},
	"results": "success"
   }
   ```

  | Name            | Type             | Description                           |
  |-----------------|------------------|---------------------------------------|
  | results         | string           | success or failed                     |
  | userId          | string           | Username for customer login           |
  | userPass        | BASE64           | Password for customer login           |
  | username        | string           | Username for vpn login                |
  | password        | string           | Password for vpn login                |


* `POST /v2/login`: User login

  Request Body

  | Name            | Type             | Description                           |
  |-----------------|------------------|---------------------------------------|
  | userId          | string           | Username for customer login           |
  | userPass        | BASE64           | user Password in BASE64               |
  | domain          | String           | Domain name                           |


  Example of Request body JSON


    ```json
       {
	      "userId": "8613600000003",
	      "userPass": "c3RhY2thYnVzZS5jb20=",
        "domain": "33vpn.com"
       }
    ```


  Example of Respons body


    ```json
       {
              "result": "success",
              "credential": {
              "username": "8613600000008",
              "password": "f2wq6A",
              "active": 0,
              "protocol": "IKEv2",
              "vpn_remote_id": "vpn.atspeeds.com",
              "server_address_url": "https://api.atspeeds.com/servers"
               },
              "jwt":"<jwt_token>"
         }
   ```


  | Name            | Type             | Description                           |
  |-----------------|------------------|---------------------------------------|
  | results         | string           | success or failed                        |
  | credential      | Object           | Object of user credential   |
  | username        | string | username for ikv2 vpn service        |
  | password        | string           | password for ikv2 vpn service         |
  | active          | Boolean          | user status for billing usage         |  
  | protocol        | String           | VPN protocol         |  
  | vpn_remote_id   | String           | VPN remote_id         |  
  | server_address_url        | URL    | A url to get the list of VPN servers         |  
  | JWT             | JWT token        | JWT token for further usage         |  



* `GET /v2/servers`: Return list of VPN servers

  Example response

   ```json
   {
         "servers": [
             "hk.node.atspeeds.com",
	     "jp.node.atspeeds.com"
             ]

   }
   ```


* `GET /v2/clients?jwt=<jwt_token>`: GET client credential after login (with JWT token)

  JWT is generated in login. Example of Response

   ```json
   {
           "result": "success",
            "credential": {
               "domain": "33vpn.com",
               "userId": "8613600000008",
               "username": "13600000008",
               "password": "f2wq6A",
               "active": 0,
               "protocol": "IKEv2",
               "vpn_remote_id": "vpn.atspeeds.com",
               "server_address_url": "https://api.atspeeds.com/servers"
              }
    }
   ```


* `PUT /v2/clients?jwt=<jwt_token>`: Update user status and login password

  Example of Request body JSON

   ```json
   {
	      "userId": "8613600000003",
              "domain": "33vpn.com",
	      "userPass": "<newpasswordinbase64>",
	      "active": 1,
    }
   ```


    | Name            | Value            | Description                           |
    |-----------------|------------------|---------------------------------------|
    | doamin          | string           | domain name (mandatory)
    | userId              | string             | phone number (mandatory)               |
    | userPass | BASE64             | user Password in BASE64 (semi-optional)                        |
    | active       | Boolean         | Billing status (semi-optional) |



  Example of Response


   ```json
      {
              "result": "success"
      }
   ```


* `delete /v2/clients?jwt=<jwt_token>`: Delete VPN client by phone

  Example of Request body JSON


   ```json
    {
	      "userId": "8613600000003",
              "domain": "33vpn.com"
    }
   ```


   | Name            | Value            | Description                           |
   |-----------------|------------------|---------------------------------------|
   | doamin          | string           | domain name (mandatory)
   | userId              | string             | phone number (mandatory)               |


  Example of Response

   ```json
   {
              "result": "success"
   }
   ```


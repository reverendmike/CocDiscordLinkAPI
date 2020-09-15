# CocDiscordLinkAPI

## About
CocDiscordLinkAPI is a service created for Clash of Clans Discord bot developers. The purpose is to be a central repository for links between Clash of Clans player accounts and their Discord account. 

The is a REST-based service, hosted in Microsoft Azure. It requires a username/password to use. To request a login, join my support server and send a message in #coc-discord-link-api. Click here to join: https://discord.gg/kPqEmxR

## Using the Service
The base URL for the server is: https://cocdiscordlink.azurewebsites.net/api/. Authentication is done using JWT, which expire every 2 hours after being issued.

### Authentication
POST - https://cocdiscordlink.azurewebsites.net/api/login
Payload:
```
{
    "username": "accountname", 
    "password": "accountpassword"
}
```

If successful, you will receive a 200 OK message, with your token
```
{
    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VybmFtZSI6InJldmVyZW5kbWlrZSIsImV4cCI6MTYwMDEyNzAxMn0.Dx28nHQv7VLuXukrCSMhWcbKVdRY2zbRZoyah2FldEY"
}
```

### Retrieving a Link by Player Tag
GET - https://cocdiscordlink.azurewebsites.net/api/links/{tag}

*Note: You do not need to include the # in the query, but if you do, be sure to encode it to %23*

Example(s):
```
https://cocdiscordlink.azurewebsites.net/api/links/RQ33GCCG (no #)
https://cocdiscordlink.azurewebsites.net/api/links/%23RQ33GCCG (# is encoded)
```
Returns:
```
[
    {
        "playerTag": "#RQ33GCCG",
        "discordId": "658256846652301451"
    }
]
```


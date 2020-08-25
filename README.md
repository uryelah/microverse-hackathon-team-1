## Chromies-API

The back-end for a chrome extension that allows for multimedia note taking(screenshots, text, and video-recording) of the current web-page or video allowing the saving of notes as a modal on the web-page, which can then be used for future reference.

## Models
### - User
- Has one (2) unique fields: **:name, :notes**
- Has one (1) non-unique field: **:date** (automatically populated with the date and time created)
- Has string validations required for **:name** must have a value, must be unique
- **:notes** field is an Array of all note objects created by this user

### - Note
- Has two (6) non-unique fields: **:pageLink, :body, :videoTimeStamp, :videoLink, :imgLink, :userID, :date**
- Has string validations required for **:pageLink, :body, :videoTimeStamp, :videoLink, :imgLink**
- **:userID** field is a reference to the User object that created this note
- **:date** field is automatically populated with the date and time this note was created

## Routes
### User Routes
## GET /users

Once the GET request has successfully gone through, an array of all users currently in the database will be returned

**JSON data returned**:

**200**: ```[{"notes":[{}],"_id":"","name":"","date":""}]```

## POST /users/register

Once the POST request has successfully gone through, the newly created user will be returned

Query string parameters accepted:  
{  
  "**name**" required*  
  Specify the name of the User
  ```
  type: 'string'
  ```
}

Example query using a JSON body request: ```{ "name": "aaron" }```

**JSON data returned**:

**200**: ```{ "notes":[{}], "_id":"128329fuvfn", "name":"aaron", "date":"2020-08-25T03:25:41.582Z" }```  
**400**: ```"Username already taken"```

## POST /users/login

Once the POST request has successfully gone through, the user object with the queried name if returned

Query string parameters accepted:  
{  
  "**name**" required*  
  Specify the name of the User
  ```
  type: 'string'
  ```
}

Example query using a JSON body request: ```{ "name": "aaron" }```

**JSON data returned**:

**200**: ```{ "notes":[{}], "_id":"128329fuvfn", "name":"aaron", "date":"2020-08-25T03:25:41.582Z" }```  
**400**: ```"Error: User doesn't exist!"```

### Note Routes
## GET /notes

Once the GET request has successfully gone through, an array of all notes queried by the pageLink field value is returned

Example query using a JSON body request: ```{ "pageLink": "https://yabadabbadoo.com" }```

**JSON data returned**:

**200**: ```[
    {
        "videoLink": "",
        "imgLink": "",
        "_id": "5f4484b5dc20d34f50875bd2",
        "pageLink": "https://yabadabbadoo.com",
        "body": "Just a test note",
        "userID": "5f44791f0f13301f4480c4f9",
        "date": "2020-08-25T03:25:41.582Z",
    }
]```  
**400**: ```"Error: related error message"```


## Built With

- Node Package Manager
- "cloudinary": "^1.22.0",
- "cors": "^2.8.5",
- "express": "^4.17.1",
- "mongoose": "^5.10.0",
- "multer": "^1.4.2"

## Setting up your own Local Environment

### Installation

* Download repository to your local machine, then run `npm install`.

## Author

👤 **Aaron Rory**

- Github: [@Aaron-RN](https://github.com/Aaron-RN)
- Twitter: [@ARNewbold](https://twitter.com/ARNewbold)
- Linkedin: [Aaron Newbold](https://www.linkedin.com/in/aaron-newbold-1b9233187/)

👤 **Adebola**

- Github: [@githubhandle](https://github.com/onedebos)
- Twitter: [@twitterhandle](https://twitter.com/debosthefirst)
- Linkedin: [linkedin](https://www.linkedin.com/in/adebola-niran/)

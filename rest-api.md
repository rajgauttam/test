**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [REST api documentation](#rest-api-documentation)
	- [Apis for contest adminstration](#apis-for-contest-adminstration)
		- [Get list of contests](#get-list-of-contests)
		- [Search contests by keyword](#search-contests-by-keyword)
		- [Get details about a specific](#get-details-about-a-specific)
		- [Create a new contest](#create-a-new-contest)
		- [Delete a contest](#delete-a-contest)
		- [Update a specific contest](#update-a-specific-contest)
		- [Get All contests, in which user has participated](#get-all-contests-in-which-user-has-participated)
		- [Publish a contest](#publish-a-contest)
		- [Delete a publish contest](#delete-a-publish-contest)
		- [Feature a contest](#feature-a-contest)
		- [Defeature a contest](#defeature-a-contest)
		- [Ban a user for a contest](#ban-a-user-for-a-contest)
		- [Unban a user for a contest](#unban-a-user-for-a-contest)
		- [Promote a user to admin for a contest](#promote-a-user-to-admin-for-a-contest)
		- [Rend roll admin from a user for a contest](#rend-roll-admin-from-a-user-for-a-contest)
		- [Update score for a user who is a member of given contest](#update-score-for-a-user-who-is-a-member-of-given-contest)
	- [Apis for members of a contest](#apis-for-members-of-a-contest)
		- [Get list of members for a specific contest ](#get-list-of-members-for-a-specific-contest)
		- [Get detail for a specific member ](#get-detail-for-a-specific-member)
		- [Get leaderboard ](#get-leaderboard)
		- [Get admins for a contest ](#get-admins-for-a-contest)
		- [Join a user in a contest](#join-a-user-in-a-contest)
		- [Leave a user from a contest](#leave-a-user-from-a-contest)
		- [Send mail to all member of a specific contest](#send-mail-to-all-member-of-a-specific-contest)
	- [Apis for contest documentation](#apis-for-contest-documentation)
		- [Get list of documents for a specific contest](#get-list-of-documents-for-a-specific-contest)
		- [Get details about a specific document](#get-details-about-a-specific-document)
		- [Create a new document for specific contest](#create-a-new-document-for-specific-contest)
		- [Update a document with upload a file for a specific contest](#update-a-document-with-upload-a-file-for-a-specific-contest)
	- [Apis for contest responses](#apis-for-contest-responses)
		- [Get list of responses for a specific contest](#get-list-of-responses-for-a-specific-contest)
		- [Get details about a specific response](#get-details-about-a-specific-response)
		- [Create a new response for specific contest](#create-a-new-response-for-specific-contest)
		- [Update a response with upload a file for a specific contest](#update-a-response-with-upload-a-file-for-a-specific-contest)
	- [Apis for users](#apis-for-users)
		- [Get list of users](#get-list-of-users)
		- [Get details about a specific user](#get-details-about-a-specific-user)
		- [Get list of recent users](#get-list-of-recent-users)
		- [Get list of followers for a specific user](#get-list-of-followers-for-a-specific-user)
		- [Get list of followers for a current logged in user](#get-list-of-followers-for-a-current-logged-in-user)
		- [Get list of followings for a specific user](#get-list-of-followings-for-a-specific-user)
		- [Get list of followings for a current logged in user](#get-list-of-followings-for-a-current-logged-in-user)
		- [Follow a user](#follow-a-user)
		- [Unfollow a user](#unfollow-a-user)
		- [Get common followers between users](#get-common-followers-between-users)
		- [Get common followers between current logged in user and a specific user](#get-common-followers-between-current-logged-in-user-and-a-specific-user)
		- [Send a mail to user](#send-a-mail-to-user)
	- [Apis for meta data](#apis-for-meta-data)
		- [Get list of user meta data](#get-list-of-user-meta-data)
		- [Get list of contest meta data](#get-list-of-contest-meta-data)

# REST api documentation

## Apis for contest adminstration

### Get list of contests
```GET /api/contests``` 

Optional parameters:
```
page : page number to fetch
size : number of elements per page
```

Response:
```
{
	content: [{"name": "contest1" , "title": "contest1"},
			{"name": "contest2" , "title": "contest2"}],
}
```

### Search contests by keyword
```GET /api/contests/search?keyword=<search keyword>``` 

Optional parameters:
```
page : page number to fetch
size : number of elements per page
```

Response:
```
{
	content: [{"name": "contest1" , "title": "contest1"},
			{"name": "contest2" , "title": "contest2"}],
}
```


### Get details about a specific
```GET /api/contests/:contestIdOrSlug``` 

Response:
```
{"name": "contest1" , "title": "contest1"}
```
Returns status code *404* if the contest with contestId doesn't exists are not accessible


### Create a new contest
```POST /api/contests``` 

Request:
```
{"name": "contest1" , "title": "contest1"}
```

Other mandatory json request fields
```
 category                -string
 function                -string
 description             -string
 startDate               -date
 subdate                 -date
 resDate                 -date
 status                  -string
 ```
 
Optional json request fields
 ```
 firstPrizeNo            -int
 firstPrizeShare         -int
 secondPrizeNo           -int
 secondPrizeShare        -int
 thirdPrizeNo            -int
 thirdPrizeShare         -int
 guidelines              -string
 criteria                -string
 prizes                  -string
 others                  -string
 level                   -string
 vertical                -string
 datatype                -string
 featured (default value is false)
 published (default value is false)
 upcomingMessage (default value is blank string)
 prizeDescJson (default value is {}) 
 hasLeaderboard          -boolean
 autoEvaluate            -boolean
 actualScoresDoc         -long
 notiyDefault            -enum (NO_EMAIL | WEEKLY| DAILY| ALL)
 evaluationMethod        -enum (RMSE|RMSLE|LOG_ERROR|ACCURACY|MIS_CLASSIFICATION_ERROR|CLASSIFICATION_ACCURACY)
 ```

Response:
    ```
    Success: 
	Location: /api/contests/:newContestId
	```


### Delete a contest
```DELETE /api/contests/:contestId``` 


### Update a specific contest
```PUT /api/contests/:contestId``` 

Request:
```
{"name": "contest1" , "title": "contest1"}
```

Response:

```
{"name": "contest1" , "title": "contest1"}
```


### Get All contests, in which user has participated
```GET /api/contests/users/:userId``` 

Optional parameters:
```
page : page number to fetch
size : number of elements per page
```

Response:
```
{
	content: [{"name": "contest1" , "title": "contest1"},
			{"name": "contest2" , "title": "contest2"}],
}
```

	

### Publish a contest
```POST /api/contests/published``` 

Request:
```
{"contestId": 1}
```

Response:
Success: 
	```Location: /api/contests/published/:newContestId```
	
	
### Delete a publish contest

```DELETE /api/contests/published/:contestId``` 


### Feature a contest
```POST /api/contests/featured``` 

Request:
```
{"contestId": 1}
```

Response:
Success: 
	Location: /api/contests/featured/:newContestId
	
	
### Defeature a contest

```DELETE /api/contests/featured/:contestId``` 

	
### Ban a user for a contest
```POST /api/contests/:contestId/banned``` 

Request:
```
{"userId": 1}
```
	
### Unban a user for a contest

```DELETE /api/contests/:contestId/banned/:userId``` 


### Promote a user to admin for a contest
```POST /api/contests/:contestId/admins``` 

Request:
```
{"userId": 1}
```
	
### Rend roll admin from a user for a contest
```DELETE /api/contests/:contestId/admins/:userId``` 
	
### Update score for a user who is a member of given contest
```PUT /api/contests/:contestId/members/:userId/score``` 

Request:
```
{"predictionErr": "predictionErr"}
```


## Apis for members of a contest

### Get list of members for a specific contest 
```GET /api/contests/:contestId/members``` 

Optional parameters:
   ```
   page : page number to fetch
   size : number of elements per page
   ```

Response:
```
{
	content: [{"id": member id, userId":"1,"fullName": "username1"},
                                {"id": member id2, "userId":2,"fullName": "username2"}],
}
```

### Get detail for a specific member 
```GET /api/contests/:contestId/members/:memberId``` 

Response:
```
	{"id": member id, "userId":1,"fullName": "username1"}
```


### Get leaderboard 
```GET /api/contests/:contestId/leaderboard``` 

Optional parameters:
   ```
   page : page number to fetch
   size : number of elements per page
   ```

Response:
```
{
	content: [{"id": member id, "userId":1,"fullName": "username1"},
                                {"id": member id2, "userId":2,"fullName": "username2"}],
}
```

### Get admins for a contest 
```GET /api/contests/:contestId/admins``` 

Optional parameters:
    ```
    page : page number to fetch
    size : number of elements per page
    ```

Response:
```
{
	user: [{"fullName": "displayName1" , "email": "userEmail1"},
			{"fullName": "displayName2" , "email": "userEmail2"}],
}
```


### Join a user in a contest
```POST /api/contests/:contestId/members``` 

Request:
```
{"userId": 1}
```

Optional Json fields-
   ```
   userTitle -string(default empty)
   comments  -string(default empty)
   ```

Response:
    ``` 
    Success: 
	Location: /api/contests/:contestId/newMemberId
	```


### Leave a user from a contest
```DELETE /api/contests/:contestId/members``` 


### Send mail to all member of a specific contest
```POST /api/contests/:contestId/members/message``` 

Request:
```
{"subject": "subject" , "content": "content"}
```


## Apis for contest documentation

### Get list of documents for a specific contest
```GET /api/contests/:conestId/documents``` 

Optional parameters:
    ```
    page : page number to fetch
    size : number of elements per page
    ```

Response:
```
{
	content: [{"name": "document1" , "file": "file1"},
			{"name": "document2" , "file": "file2"}],
}
```


### Get details about a specific document
```GET /api/contests/:contestId/documents/:documentId``` 

Response:
```
{"name": "document1" , "file": "document1"}
```
Returns status code *404* if the contest with contestId doesn't exists are not accessible



### Create a new document for specific contest
```POST /api/contests/:contestId/documents``` 

Request:

   ```
   Post mandatory form data properties
   name -string
   ```

optional form data properties
    ```
    multipartFile  -file using form upload 
    description    -string
    featured       -numeric(short)
    ```

Response:
    ```
    Success: 
	Location: /api/contests/:contestId/documents/:newContestId
    ```

### Update a document with upload a file for a specific contest
```POST /api/contests/:contestId/documents/:documentId``` 

form data properties
     ```
     multipartFile  -file using form upload
     ```

Response:

     ```
     {"id":contestDocument1}
     ```
upload a file using form to given action url.


## Apis for contest responses

### Get list of responses for a specific contest
```GET /api/contests/:conestId/responses``` 

Optional parameters:
    ```
    page : page number to fetch
    size : number of elements per page
    ```

Response:
```
{
	content: [{"name": "response1" , "file": "file1"},
			{"name": "response2" , "file": "file2"}],
} 
```


### Get details about a specific response
```GET /api/contests/:contestId/responses/:responseId``` 

Response:
```
{"name": "response1" , "file": "file1"}
```
Returns status code *404* if the contest with contestId doesn't exists are not accessible


### Create a new response for specific contest
```POST /api/contests/:contestId/responses``` 

Request:
```
{"name": "response1" ,"file": "file1"}
```

Response:
    ```
    Success: 
	Location: /api/contests/:contestId/responses/:newResponseId
	```



### Update a response with upload a file for a specific contest
```POST /api/contests/:contestId/reponses/:responseId``` 

form data properties
     ```
     multipartFile  -file using form upload
     ```

Response:

```
{"id":contestResponse1}
```
upload a file using form to given action url.




## Apis for users


### Get list of users
```GET /api/users``` 

Optional parameters:
     ```
     page : page number to fetch
     size : number of elements per page
     ```

Response:
```
{
	user: [{"fullName": "displayName1" , "email": "userEmail1"},
			{"fullName": "displayName2" , "email": "userEmail2"}],
}
```


### Search users by keyword
```GET /api/users/search?keyword=<search keyword>``` 

Optional parameters:
     ```
     page : page number to fetch
     size : number of elements per page
     ```

Response:
```
{
	user: [{"fullName": "displayName1" , "email": "userEmail1"},
			{"fullName": "displayName2" , "email": "userEmail2"}],
}
```


### Get details about a specific user
```GET /api/users/:userId``` 

Response:
```
{"fullName": "displayName1" , "email": "userEmail1"}
```
Returns status code *404* if the user with userId doesn't exists are not accessible

### Get loggedin user
```GET /api/users/me``` 

Response:
```
{"fullName": "displayName1" , "email": "userEmail1"}
```

### Get list of recent users
```GET /api/users/recent``` 

Optional parameters:
    ```
    page : page number to fetch
    size : number of elements per page
    ```

Response:
```
{
	user: [{"fullName": "displayName1" , "email": "userEmail1"},
			{"fullName": "displayName2" , "email": "userEmail2"}],
}
```
  
### Create a new user
```POST /api/users/``` 

Request:
```
{"username": "raj" , "password": "welcome"}
```

Other mandatory json request fields
    ```
    username     -string
    password -string
    email -string
    ```
 
Optional json request fields
    ```
    fullName -string
    ```

Response:
    ```
    {id:newUserId}
    ```
   
      Success: 
      ```
      Location: /api/users/:newUserId
      ```

### Add a role to user
```POST /api/users/:userId/roles``` 

Request:
```
{"roleId": roleId}
```

Response:
    ```{userId:uId,roleId:rId}```
   
 Success: 
      ```Location: /api/users/:userId/roles/:roleId```

### Remove a role from user
```DELETE /api/users/:userId/roles/roleId``` 


Response:
    ```{userId:uId,roleId:rId}```
   
### Reset password request
```POST /api/users/password_reset``` 

Request:
```
{"usernameOrEmailOrId": "usernameOrEmailOrId"}
```

### Verify reset password request
```GET /api/users/password_reset/token``` 



### Reset password
```PUT /api/users/:userIdOrUsername/password``` 

Request:
```
{"password": "welldone" , "newPassword": "welcome"}
```

Other mandatory json request fields
    ```
    newPassword    -string
    ```
 
Optional json request fields
    ```
    password      -string
    resetToken    -string
    ```

Response:
    ```{id:userId,username:"raj"}```
   

### Get list of followers for a specific user
```GET /api/users/:userId/followers``` 

Optional parameters:
    ```
    page : page number to fetch
    size : number of elements per page
    ```

Response:
```
user: [{"fullName": "displayName1" , "email": "userEmail1"},
			{"fullName": "displayName2" , "email": "userEmail2"}],
```


### Get list of followers for a current logged in user
```GET /api/users/me/followers``` 

Optional parameters:
     ```
     page : page number to fetch
     size : number of elements per page
     ```

Response:
```
user: [{"fullName": "displayName1" , "email": "userEmail1"},
			{"fullName": "displayName2" , "email": "userEmail2"}],
```


### Get list of followings for a specific user
```GET /api/users/:userId/following``` 

Optional parameters:
    ```
    page : page number to fetch
    size : number of elements per page
    ```

Response:
```
user: [{"fullName": "displayName1" , "email": "userEmail1"},
			{"fullName": "displayName2" , "email": "userEmail2"}],
```


### Get list of followings for a current logged in user
```GET /api/users/me/following``` 

Optional parameters:
     ```
     page : page number to fetch
     size : number of elements per page
     ```

Response:
```
user: [{"fullName": "displayName1" , "email": "userEmail1"},
			{"fullName": "displayName2" , "email": "userEmail2"}],
```


### Follow a user
```POST /api/users/following``` 

Request:
```
{"userId": uId1 }
```


### Unfollow a user
```DELETE /api/users/me/following/:userId``` 


### Get common followers between users
```GET /api/users/:userId/common/followers/:userId2``` 

Optional parameters:
    ```
    page : page number to fetch
    size : number of elements per page
    ```

Response:
```
user: [{"fullName": "displayName1" , "email": "userEmail1"},
			{"fullName": "displayName2" , "email": "userEmail2"}],
```


### Get common followers between current logged in user and a specific user
```GET /api/users/me/common/userId/followers``` 

Optional parameters:
     ```
     page : page number to fetch
     size : number of elements per page
     ```

Response:
```
user: [{"fullName": "displayName1" , "email": "userEmail1"},
			{"fullName": "displayName2" , "email": "userEmail2"}],
```

### Send a mail to user
```POST /api/users/:userId/messages``` 

Request:
```
{"subject": "subject","content":"content" }
```


## Apis for user documentation

### Get list of documents for a specific user
```GET /api/users/:userId/documents``` 

Optional parameters:
    ```
    page : page number to fetch
    size : number of elements per page
    ```

Response:
```
{
	content: [{"name": "document1" , "file": "file1"},
			{"name": "document2" , "file": "file2"}],
}
```


### Get details about a specific document
```GET /api/users/:userId/documents/:documentId``` 

Response:
```
{"name": "document1" , "file": "document1"}
```
Returns status code *404* if the contest with contestId doesn't exists are not accessible



### Create new multiple documents for specific user
```POST /api/users/:userId/documents``` 

Request:

   ```
   ?userDocumentDatas[0].multiPartFile=@/home/raj/Downloads/logo2.png 
         &userDocumentDatas[0].file=abc 
         &userDocumentDatas[0].name=file1 
         &userDocumentDatas[0].description=filetest1 
    ```
post data using form to given action url.

Response:

   ```
   {"userDocumentIds":[1,16,17]}
   ```

### Add new document for specific user
```POST /api/users/:userId/documents/add``` 

Request:

    ```
    ?multiPartFile=@/home/raj/Downloads/logo2.png 
         &file=abc 
         &name=file1 
         &description=filetest1 
    ```
post data using form to given action url.

Response:

   ```
   {"id":newDocId}
   ```

### remove document for specific user
```DELETE /api/users/:userId/documents/:documentId``` 

Response:

   ```
   {"id":deletedDocId}
   ```

### update document file for specific document
```POST /api/users/:userId/documents/:documentId``` 

Request:

    ```
    Form upload a file with property
    file   -(file upload)
    ```

Response:

   ```
   {"id":deleteDocId}
   ```

## Apis for meta data


### Get list of user meta data
```GET /api/users/:userId/metadata```

Response:
```
{
	userMetaData: [{"metaKey": "metaKey1","metaValue":"metavalue1"},
			{"metaKey": "metaKey2","metaValue":"metavalue2"}],
}
```


### Get list of contest meta data
```GET /api/contests/:contestId/metadata``` 

Response:
```
{
	contestMetaData: [{"metaKey": "metaKey1","metaValue":"metavalue1"},
			{"metaKey": "metaKey2","metaValue":"metavalue2"}],
}
```


## Apis for forum


### Get list of forum topic
```GET /api/forums/topics``` 

Optional parameters:
    ```
    page : page number to fetch
    size : number of elements per page
    ```
Response:
```
{
	user: [{"title": "title1" , "content": "content1"},
			{"title": "title2" , "content": "content2"}],
}
```


### Get details about a specific forum topic
```GET /api/forums/topics/:topicId``` 

Response:
```
{"title": "title1" , "content": "content1"}
```
Returns status code *404* if the topic with topicId doesn't exists are not accessible


### Create a new forum topic
```POST /api/forums/topics``` 

Request:
```
{"title": "title1" , "content": "content1"}
```

Response:
     ```
	{"id": "newTopicId" }
	```
    Success: 
	```
	Location: /api/forums/topics/:newTopicId
	```
		
	
### Post a forum topic
```POST /api/forums/topics/:topicId/posts``` 

Request:
```{"title": "title1" , "description": "description1"}```

Response:
    ```
	{"id": "newPostId" }
	```
	
   Success: 
   ```
   Location: /api/forums/topics/:topicId/posts/:newPostId
   ```
	

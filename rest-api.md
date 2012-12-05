**Table of Contents**  *generated with [DocToc](http://doctoc.herokuapp.com/)*

- [REST api documentation](#rest-api-documentation)
	- [Apis for contest adminstration](#apis-for-contest-adminstration)
		- [Get list of contests](#get-list-of-contests)
		- [Get details about a specific](#get-details-about-a-specific)
		- [Create a new contest](#create-a-new-contest)
		- [Update a specific contest](#update-a-specific-contest)
		- [Publish a contest](#publish-a-contest)
        - [Delete a publish contest](#delete-a-publish-contest)
    - [Apis for members of a contest](#apis-for-members-of-a-contest)
        - [Get list of members for a specific contest](#get-list-of-members-for-a-specific-contest)
        - [Get leaderboard](#get-leaderboard)
        - [Join a user in a contest](#join-a-user-in-a-contest)
    - [Apis for contest documentation](#apis-for-contest-documentation)
        - [Get list of documents for a specific contest](#get-list-of-documents-for-a-specific-contest)
        - [Get details about a specific document](#get-details-about-a-specific-document)
        - [Create a new document for specific contest](#create-a-new-document-for-specific-contest)
    - [Apis for contest responses](#apis-for-contest-responses)
        - [Get list of responses for a specific contest](#get-list-of-responses-for-a-specific-contest)
        - [Get details about a specific response](#get-details-about-a-specific-response)
        - [Create a new response for specific contest](#create-a-new-response-for-specific-contest)
     
     
        
# REST api documentation

## Apis for contest adminstration

### Get list of contests
```GET /api/contests/``` 

Optional parameters:
page : page number to fetch
size : number of elements per page

Response:
```
{
	content: [{"name": "contest1" , "title": "contest1"},
			{"name": "contest2" , "title": "contest2"}],
}
```


### Get details about a specific
```GET /api/contests/:contestId/``` 

Response:
```
{"name": "contest1" , "title": "contest1"}
```
Returns status code *404* if the contest with contestId doesn't exists are not accessible


### Create a new contest
```POST /api/contests/``` 

Request:
{"name": "contest1" , "title": "contest1"}

Response:
Success: 
	Location: /api/contests/:newContestId/



### Update a specific contest
```PUT /api/contests/:contestId/``` 

Request:
```{"name": "contest1" , "title": "contest1"}```

Response:
```
{"name": "contest1" , "title": "contest1"}
```
	

### Publish a contest
```POST /api/contests/published/``` 

Request:
```
{"contestId": "contest1"}
```

Response:
Success: 
	Location: /api/contests/published/:newContestId/
	
### Delete a publish contest

```DELETE /api/contests/published/:contestId/``` 

Request:
```
{"contestId": "contest1"}
```
	
### Ban a user for a contest
```POST /api/contests/:contestId/banned/``` 

Request:
```
{"userId": "userId1"}
```
	
### Unban a user for a contest

```DELETE /api/contests/:contestId/banned/``` 

Request:
```
{"userId": "userId1"}
```

### Promote a user to admin for a contest
```POST /api/contests/:contestId/admins/``` 

Request:
```
{"userId": "userId1"}
```
	
### rend roll admin from a user for a contest
```DELETE /api/contests/:contestId/admins/:userId/``` 
	
### Update score for a user who is a member of given contest
```PUT /api/contests/:contestId/members/:userId/score/``` 

Request:
```
{"predictionErr": "predictionErr"}
```

## Apis for members of a contest

### Get list of members for a specific contest 
```GET /api/contests/:contestId/members/``` 

Optional parameters:
page : page number to fetch
size : number of elements per page

Response:
```
{
	content: [{"id": "member id", "userId":"1","userDisplayName": "username1"},
                                {"id": "member id", "userId":"2","userDisplayName": "username2"}],
}
```
### Get leaderboard 
```GET /api/contests/:contestId/leaderboard/``` 

Optional parameters:
page : page number to fetch
size : number of elements per page

Response:
```
{
	content: [{"id": "member id", "userId":"1","userDisplayName": "username1"},
                                {"id": "member id", "userId":"2","userDisplayName": "username2"}],
}
```


### Join a user in a contest
```POST /api/contests/:contestId/members/``` 

Request:
```
{"userId": "userId1" , "userDisplayName": "User1"}
```
Response:
Success: 
	Location: /api/contests/:contestId/newMemberId/



## Apis for contest documentation

### Get list of documents for a specific contest
```GET /api/contests/:conestId/documents/``` 

Optional parameters:
page : page number to fetch
size : number of elements per page

Response:
```
{
	content: [{"name": "document1" , "file": "file1"},
			{"name": "document2" , "file": "file2"}],
}
```


### Get details about a specific document
```GET /api/contests/:contestId/documents/:documentId/``` 

Response:
```
{"name": "document1" , "file": "document1"}
```
Returns status code *404* if the contest with contestId doesn't exists are not accessible


### Create a new document for specific contest
```POST /api/contests/:contestId/documents/``` 

Request:
```
{"name": "document1" , "title": "document1"}
```
Response:
Success: 
	Location: /api/contests/:contestId/documents/:newContestId/



## Apis for contest responses

### Get list of responses for a specific contest
```GET /api/contests/:conestId/responses/``` 

Optional parameters:
page : page number to fetch
size : number of elements per page

Response:
```
{
	content: [{"name": "response1" , "file": "file1"},
			{"name": "response2" , "file": "file2"}],
}
```


### Get details about a specific response
```GET /api/contests/:contestId/responses/:responseId/``` 

Response:
```
{"name": "response1" , "file": "file1"}
```
Returns status code *404* if the contest with contestId doesn't exists are not accessible


### Create a new response for specific contest
```POST /api/contests/:contestId/responses/``` 

Request:
```
{"name": "response1" ,"file": "file1"}
```
Response:
Success: 
	Location: /api/contests/:contestId/responses/:newResponseId/


# Documentation for HF APIs

## Index
- [Documentation for HF APIs](#documentation-for-hf-apis)
  - [Index](#index)
  - [Basic request for the API](#basic-request-for-the-api)
  - [Key](#key)
  - [HFid](#hfid)
      - [Login](#login)
      - [Sign In](#sign-in)
      - [Verify](#verify)
      - [Get info](#get-info)

## Basic request for the API


>{  
>    "key" : "[KEY]",  
>    [...]  
>}


## Key

To request a Key: <a href = "mailto:francofantomius@gmail.com"> francofantomius@gmail.com </a>.  
Every key can have access only to specific APIs, so be sure to write in the email what you want to have access.  


## HFid

#### Login
URL = https://hfapis.herokuapp.com/hfid/login

request:

>{  
>    "key" : "[KEY]",  
>    "email" : "example@example.com",  
>    "password" : "123456"  
>}  

Possible responses:

1) Everything is right and a unique id will be returned  
>{  
>    "response" : {  
>        "HFid" : "[HFid]"  
>    }  
>}  

2) The key you have does not have the permission to access this API  
>{  
>    "response" : {  
>        "error_n" : 1,  
>        "error" : "The key given does not have access to this API"  
>    }  
>}  

3) The email or password given are
>{  
>    "response" : {  
>        "error_n" : 2,  
>        "error" : "The email or password are wrong"  
>    }  
>}  

#### Sign In
URL = https://hfapis.herokuapp.com/hfid/signin

request:

>{  
>    "key" : "[KEY]",  
>    "email" : "example@example.com",  
>    "password" : "123456",  
>    "name" : "Bob",  
>    "birth" : "01/01/00"  
>}  

Possible responses:

1) Everything is right and a unique id will be returned  
>{  
>    "response" : {  
>        "HFid" : "[HFid]"  
>    }  
>} 

2) The key you have does not have the permission to access this API  
>{  
>    "response" : {  
>        "error_n" : 1,  
>        "error" : "The key given does not have access to this API"  
>    }  
>}

3) The *email / password / name / birth* are not acceptable, the requirements are:
   - email : contain "@" and after ".";
   - password : at least 6 characters;
   - name : not empty;
   - birth : contain a real date (31th of February is not a real date)  
>{  
>    "response" : {  
>        "error_n" : 3,  
>        "error" : "The email, password, name or birth are wrong"  
>    }  
>}  

#### Verify
URL = https://hfapis.herokuapp.com/hfid/verify

request:

>{  
>    "key" : "[KEY]",  
>    "HFid" : "[HFid]"  
>}  

Possible responses:
1) The user logged within 3 hrs
>{  
>    "response" : {  
>        "HFid" : "[HFid]"  
>    }  
>} 

2) The key you have does not have the permission to access this API
>{  
>    "response" : {  
>        "error_n" : 1,  
>        "error" : "The key given does not have access to this API"  
>    }  
>}

3) The HFid does not exist or it passed more than 3 hrs from the last log in
>{  
>    "response" : {  
>        "error_n" : 4,  
>        "error" : "More than 3 hrs from the last log in or user does not exist"  
>    }  
>}  

#### Get info
URL = https://hfapis.herokuapp.com/hfid/info

request:

>{  
>    "key" : "[KEY]",  
>    "HFid" : "[HFid]"  
>}  

Possible responses:
1) Everything is right and all the info will be returned
>{  
>    "response" : {  
>        "HFid" : [HFid],  
>        "email" : [email],  
>        "name" : [name],  
>        "birth" : [birth]  
>    }  
>}  

2) The key you have does not have the permission to access this API
>{  
>    "response" : {  
>        "error_n" : 1,  
>        "error" : "The key given does not have access to this API"  
>    }  
>}

3) The HFid does not exist
>{  
>    "response" : {  
>        "error_n" : 5,  
>        "error" : "User not found"   
>    }  
>}  

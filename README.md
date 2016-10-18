# Basics

All API calls are a POST request to be made to yourdatingframeworkwebsite.com/api 

Certain API calls donot require an *access_token*

When the user is authenticated. The client will receive an *access_token* , all further API calls that needs to be performed must have the access_token and the authenticated user_id


# Authentication

## Registration

## Login

* api/login *

** URL Parameters **

1. username => required|email|max:100
2. password => required|min:8

** Success Response **

``` javascript

/* Success Response */

			{
				"status": "success",
				"success_data": {
					"user_id": "6",
					"name": "Tester",
					"username": "saikatdutta1991@gmail.com",
					"access_token": "$2y$10$hHAilU1RamonedkGg1bQlu0EEPKW0M6itIXrQEXx6fUiWHCcVth1S",
					"last_request_timestamp": "2016-06-16 13:47:21"
				}
			}



```


** Error Response : Login Validation failed **

``` javascript

/* Validation Error Response */

      			{
				"status": "error",
				"error_data": {
					"username": "The Email Address field is required.",
					"password": "The Password field is required.",
					"error_text": "Login Validation failed.",
				}
			}

```

** Error Response : Wrong Password **

``` javascript

/* Validation Error Response */

			{
			
			"status": "error"
				"error_data": {
					"error_text": "Password not matched."
				}
			}

```

** Error Response : User not registered **

``` javascript

/* Validation Error Response */

			{
				"status": "error"
				"error_data": {
					"error_text": "User not registered."
				}
			}

```


** Error Response : Account Not Activated **

``` javascript

/* Validation Error Response */

			{
				"status": "error"
				"error_data": {
					"error_text": "User account not activated"
				}
			}

```



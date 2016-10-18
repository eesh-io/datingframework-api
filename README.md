# Basics

All API calls are a POST request to be made to yourdatingframeworkwebsite.com/api 

Certain API calls donot require an *access_token*

When the user is authenticated. The client will receive an *access_token* , all further API calls that needs to be performed must have the access_token and the authenticated user_id



# Authentication

## Registration


*api/register*

** URL Parameters **

1. name => required|max:100
2. dob  => required|date_format:d/m/Y|minimum 18 years old
3. username  => required|email|max:100|unique:user,username
4. lat  => required
5. lng  => required
6. city => required
7. country => required
8. gender => required
9. password => required|min:8|max:100
10. password_confirmation' => required|min:8|max:100|match:password

** Success Response **

``` javascript
	{
	"status": "success",
	"success_data": {
		"success_text": "User registered Successfully"
		"email_verify_required": 0
		}
	}

```


## Custom Fields

A User will have Custom Fields. Custom Fields are created by the Administrator. Administrator can make a custom field mandatory in registration. So along with the usual fields the custom fields should also be displayed and sent to the registration API upon post.

*api/get-custom-fields*



## Login

*api/login*

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




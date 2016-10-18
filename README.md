# Basics

All API calls are a POST request to be made to yourdatingframeworkwebsite.com/api 

Certain API calls donot require an *access_token*

When the user is authenticated. The client will receive an *access_token* , all further API calls that needs to be performed must have the access_token and the authenticated user_id


# Authentication




``` javascript
      {
				"status": "error"
				"error_data": {
					"username": "The Email Address field is required."
					"password": "The Password field is required."
					"error_text": "Login Validation failed."
				}
			}

```

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
		"success_text": "User registered Successfully",
		"email_verify_required": 0,
		}
	}

```

** Error Response: Validation Error **

*error_data* will contain a list of all the fields with validation errors and what the error is.

``` javascript
	{
	"status": "error",
	"error_data": {
		"username": "The Email Address has already been taken.",
		"gender": "The Gender field is required.",
		"error_text": "Validation Error"
		}
	}

```

## Custom Fields

A User will have Custom Fields. Custom Fields are created by the Administrator. Administrator can make a custom field mandatory in registration. So along with the usual fields the custom fields should also be displayed and sent to the registration API upon post. Use this API to fill up your User Interface with the Custom Fields.

*api/get-custom-fields*

** URL Parameters **

*none*

The response JSON is structured as:

1. Gender
2. Other Fields

Gender is given special preference as its mandatory in all registration forms and there can be multiple gender types like "couple", "transgender" that can be set by the Admin.

Other Fields is structured as other_fields -> section_name -> fields

Based on type of field. There will be options.

If type is *text* or *textarea*. There wont be options.

But if the type is *dropdown* , then there will be options that you need to fill in your UI Dropdown


** Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"gender": {
	"id": "1"
	"name": "Gender"
	"code": "gender"
	"section_id": "0"
	"type": "dropdown"
	"on_registration": "yes"
	"on_search": "yes"
	"on_search_type": "dropdown"
	"unit": ""
	"created_at": "2016-06-11 13:42:05"
	"updated_at": "2016-06-18 07:51:05"
	"deleted_at": null
	"text": "Gender"
	"options": 
		0:  {
		"id": "1"
		"name": "Male"
		"code": "male"
		"field_id": "1"
		"created_at": "2016-06-11 13:42:05"
		"updated_at": "2016-06-11 13:42:05"
		"deleted_at": null
		"text": "Male"
		}
		1:  {
		"id": "2"
		"name": "Female"
		"code": "female"
		"field_id": "1"
		"created_at": "2016-06-11 13:42:06"
		"updated_at": "2016-06-11 13:42:06"
		"deleted_at": null
		"text": "Female"
		}
	
	}
	"other_fields": 
	0:  {
		"id": "1"
		"name": "Personal Information"
		"code": "personalinformation"
		"created_at": "2016-06-11 13:42:29"
		"updated_at": "2016-06-11 13:42:29"
		"deleted_at": null
		"text": "custom_profile.personalinformation"
		"fields": [6]
				0:  {
				"id": "2"
				"name": "Height"
				"code": "height"
				"section_id": "1"
				"type": "dropdown"
				"on_registration": "yes"
				"on_search": "yes"
				"on_search_type": "range"
				"unit": "FT"
				"created_at": "2016-06-11 13:42:55"
				"updated_at": "2016-06-19 16:03:57"
				"deleted_at": null
				"text": "custom_profile.height"
				"options": [7]
					0:  {
					"id": "3"
					"name": "5"
					"code": "5ft"
					"field_id": "2"
					"created_at": "2016-06-11 13:43:38"
					"updated_at": "2016-06-11 13:43:38"
					"deleted_at": null
					"text": "custom_profile.5ft"
					}
					1:  {
					"id": "4"
					"name": "5.5"
					"code": "55ft"
					"field_id": "2"
					"created_at": "2016-06-11 13:43:44"
					"updated_at": "2016-06-11 13:43:44"
					"deleted_at": null
					"text": "custom_profile.55ft"
					}
					2:  {
					"id": "5"
					"name": "5.7"
					"code": "57ft"
					"field_id": "2"
					"created_at": "2016-06-11 13:43:50"
					"updated_at": "2016-06-11 13:43:50"
					"deleted_at": null
					"text": "custom_profile.57ft"
					}-
					3:  {
					"id": "6"
					"name": "5.8"
					"code": "58ft"
					"field_id": "2"
					"created_at": "2016-06-11 13:43:57"
					"updated_at": "2016-06-11 13:43:57"
					"deleted_at": null
					"text": "custom_profile.58ft"
					}-
					4:  {
					"id": "7"
					"name": "6"
					"code": "6ft"
					"field_id": "2"
					"created_at": "2016-06-11 13:44:02"
					"updated_at": "2016-06-11 13:44:02"
					"deleted_at": null
					"text": "custom_profile.6ft"
					}-
					5:  {
					"id": "8"
					"name": "6.2"
					"code": "62ft"
					"field_id": "2"
					"created_at": "2016-06-11 13:44:07"
					"updated_at": "2016-06-11 13:44:07"
					"deleted_at": null
					"text": "custom_profile.62ft"
					}-
					6:  {
					"id": "9"
					"name": "6.3"
					"code": "63ft"
					"field_id": "2"
					"created_at": "2016-06-11 13:44:15"
					"updated_at": "2016-06-11 13:44:15"
					"deleted_at": null
					"text": "custom_profile.63ft"
					}-
					-
					}-
				1:  {
				"id": "3"
				"name": "Weight"
				"code": "weight"
				"section_id": "1"
				"type": "dropdown"
				"on_registration": "no"
				"on_search": "yes"
				"on_search_type": "range"
				"unit": "KG"
				"created_at": "2016-06-11 13:43:09"
				"updated_at": "2016-06-11 13:43:09"
				"deleted_at": null
				"text": "custom_profile.weight"
				"options": [13]
					0:  {
					"id": "10"
					"name": "50"
					"code": "50kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:44:22"
					"updated_at": "2016-06-11 13:44:22"
					"deleted_at": null
					"text": "custom_profile.50kg"
					}-
					1:  {
					"id": "11"
					"name": "52"
					"code": "52kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:44:28"
					"updated_at": "2016-06-11 13:44:28"
					"deleted_at": null
					"text": "custom_profile.52kg"
					}-
					2:  {
					"id": "12"
					"name": "53"
					"code": "53kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:44:33"
					"updated_at": "2016-06-11 13:44:33"
					"deleted_at": null
					"text": "custom_profile.53kg"
					}-
					3:  {
					"id": "13"
					"name": "58"
					"code": "58kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:44:41"
					"updated_at": "2016-06-11 13:44:41"
					"deleted_at": null
					"text": "custom_profile.58kg"
					}-
					4:  {
					"id": "14"
					"name": "60"
					"code": "60kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:44:48"
					"updated_at": "2016-06-11 13:44:48"
					"deleted_at": null
					"text": "custom_profile.60kg"
					}-
					5:  {
					"id": "15"
					"name": "62"
					"code": "62kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:44:54"
					"updated_at": "2016-06-11 13:44:54"
					"deleted_at": null
					"text": "custom_profile.62kg"
					}-
					6:  {
					"id": "16"
					"name": "64"
					"code": "64kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:45:03"
					"updated_at": "2016-06-11 13:45:03"
					"deleted_at": null
					"text": "custom_profile.64kg"
					}-
					7:  {
					"id": "17"
					"name": "68"
					"code": "68kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:45:12"
					"updated_at": "2016-06-11 13:45:12"
					"deleted_at": null
					"text": "custom_profile.68kg"
					}-
					8:  {
					"id": "18"
					"name": "70"
					"code": "70kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:45:18"
					"updated_at": "2016-06-11 13:45:18"
					"deleted_at": null
					"text": "custom_profile.70kg"
					}-
					9:  {
					"id": "19"
					"name": "72"
					"code": "72kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:45:26"
					"updated_at": "2016-06-11 13:45:26"
					"deleted_at": null
					"text": "custom_profile.72kg"
					}-
					10:  {
					"id": "20"
					"name": "74"
					"code": "74kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:45:35"
					"updated_at": "2016-06-11 13:45:35"
					"deleted_at": null
					"text": "custom_profile.74kg"
					}-
					11:  {
					"id": "21"
					"name": "78"
					"code": "78kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:45:43"
					"updated_at": "2016-06-11 13:45:43"
					"deleted_at": null
					"text": "custom_profile.78kg"
					}-
					12:  {
					"id": "22"
					"name": "80"
					"code": "80kg"
					"field_id": "3"
					"created_at": "2016-06-11 13:45:48"
					"updated_at": "2016-06-11 13:45:48"
					"deleted_at": null
					"text": "custom_profile.80kg"
					}-

				}-
				2:  {
				"id": "4"
				"name": "Eyecolor"
				"code": "eyecolor"
				"section_id": "1"
				"type": "dropdown"
				"on_registration": "no"
				"on_search": "yes"
				"on_search_type": "dropdown"
				"unit": ""
				"created_at": "2016-06-11 13:43:27"
				"updated_at": "2016-06-11 13:43:27"
				"deleted_at": null
				"text": "custom_profile.eyecolor"
				"options": [3]
					0:  {
					"id": "23"
					"name": "Black"
					"code": "black"
					"field_id": "4"
					"created_at": "2016-06-11 13:45:55"
					"updated_at": "2016-06-11 13:45:55"
					"deleted_at": null
					"text": "custom_profile.black"
					}-
					1:  {
					"id": "24"
					"name": "Brown"
					"code": "brown"
					"field_id": "4"
					"created_at": "2016-06-11 13:46:05"
					"updated_at": "2016-06-11 13:46:05"
					"deleted_at": null
					"text": "custom_profile.brown"
					}-
					2:  {
					"id": "25"
					"name": "Blue"
					"code": "blue"
					"field_id": "4"
					"created_at": "2016-06-11 13:46:12"
					"updated_at": "2016-06-11 13:46:12"
					"deleted_at": null
					"text": "custom_profile.blue"
					}-
					-
					}-
				3:  {
				"id": "5"
				"name": "Here to"
				"code": "hereto"
				"section_id": "1"
				"type": "dropdown"
				"on_registration": "no"
				"on_search": "yes"
				"on_search_type": "dropdown"
				"unit": ""
				"created_at": "2016-06-11 13:46:42"
				"updated_at": "2016-06-11 13:46:42"
				"deleted_at": null
				"text": "custom_profile.hereto"
				"options": [3]
					0:  {
					"id": "26"
					"name": "Dating"
					"code": "dating"
					"field_id": "5"
					"created_at": "2016-06-11 13:46:53"
					"updated_at": "2016-06-11 13:46:53"
					"deleted_at": null
					"text": "custom_profile.dating"
					}-
					1:  {
					"id": "27"
					"name": "Chatting"
					"code": "chatting"
					"field_id": "5"
					"created_at": "2016-06-11 13:47:00"
					"updated_at": "2016-06-11 13:47:00"
					"deleted_at": null
					"text": "custom_profile.chatting"
					}-
					2:  {
					"id": "28"
					"name": "Make New Friends"
					"code": "makenewfriends"
					"field_id": "5"
					"created_at": "2016-06-11 13:47:10"
					"updated_at": "2016-06-11 13:47:10"
					"deleted_at": null
					"text": "custom_profile.makenewfriends"
					}-

					}-
	4:  {
	"id": "6"
	"name": "Text"
	"code": "text"
	"section_id": "1"
	"type": "text"
	"on_registration": "no"
	"on_search": "no"
	"on_search_type": "range"
	"unit": ""
	"created_at": "2016-06-20 09:17:37"
	"updated_at": "2016-06-20 09:17:37"
	"deleted_at": null
	"text": "Text"
	}-
	5:  {
	"id": "7"
	"name": "textarea"
	"code": "textarea"
	"section_id": "1"
	"type": "textarea"
	"on_registration": "no"
	"on_search": "no"
	"on_search_type": "range"
	"unit": ""
	"created_at": "2016-06-20 09:18:23"
	"updated_at": "2016-06-20 09:18:23"
	"deleted_at": null
	"text": "textarea"
	}
	
	}

"success_text": "Custom profile fields retrived successfully."
}
}



```



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


# User Profile

## Display Profile

## Edit Profile


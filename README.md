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

## User Object

This JSON object type contains the basic details of a User.

``` javascript

		{
		"id": "23"
		"username": "saikatdutta1991@gmail.com"
		"gender": "female"
		"name": "saikat"
		"dob": "1991-05-12"
		"city": ""
		"country": ""
		"hereto": ""
		"profile_pic_url": {
		"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/female.jpg"
		"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/female.jpg"
		"other": "http://localhost/liteoxide/public/uploads/others/female.jpg"
		"original": "http://localhost/liteoxide/public/uploads/others/original/female.jpg"
		}-
		"status": ""
		"package_name": null
		"expired_at": null
		"activate_token": ""
		"password_token": ""
		"activate_user": "activated"
		"register_from": "facebook"
		"verified": "verified"
		"latitude": null
		"longitude": null
		"language": ""
		"last_request": "2016-06-20 13:31:05"
		"access_token": "$2y$10$CMQOzxo/DnpLERT8VqfpX.oVS0pAm86CnDguV0RxDdrME/3amNvy."
		"created_at": "2016-06-20 12:24:42"
		"updated_at": "2016-06-20 13:31:05"
		"deleted_at": null
		"gender_text": "Female"
		"age": 25
		"superpower_activated": "false"
		"superpower_days_left": "-9999"
		"invisible": "false"
		"online_status": "true"
		"social_links": [1]
		0:  "facebook"
		-
		"social_verified": "true"
		"profile_picture": "female.jpg"
		}
```

## Display Profile

*api/profile/me*

** URL Parameters **

1. user_id
2. access_token

** Response **

1. photos
2. field_sections -> fields -> fields [options]
3. user_popularity
4. profile_complete_percentage
5. user_score
6. user ( User Object )
7. about_me
8. user_interests
9. profile_visitor_count
10. max_file_upload_size

``` javascript

{
	"status": "success"
	"success_data": {
	"photos": [4]
		0:  {
		"id": "24"
		"userid": "23"
		"source_photo_id": null
		"photo_source": null
		"photo_url": {
		"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails23_5767ed991c4f864225536.jpg"
		"encounter": "http://localhost/liteoxide/public/uploads/others/encounters23_5767ed991c4f864225536.jpg"
		"other": "http://localhost/liteoxide/public/uploads/others/23_5767ed991c4f864225536.jpg"
		"original": "http://localhost/liteoxide/public/uploads/others/original/23_5767ed991c4f864225536.jpg"
		}-
		"created_at": "2016-06-20 13:20:25"
		"updated_at": "2016-06-20 13:20:25"
		"deleted_at": null
		"photo_name": "23_5767ed991c4f864225536.jpg"
		}-
		1:  {
		"id": "25"
		"userid": "23"
		"source_photo_id": null
		"photo_source": null
		"photo_url": {
		"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails23_5767ed9a1f95897130987.jpg"
		"encounter": "http://localhost/liteoxide/public/uploads/others/encounters23_5767ed9a1f95897130987.jpg"
		"other": "http://localhost/liteoxide/public/uploads/others/23_5767ed9a1f95897130987.jpg"
		"original": "http://localhost/liteoxide/public/uploads/others/original/23_5767ed9a1f95897130987.jpg"
		}-
		"created_at": "2016-06-20 13:20:26"
		"updated_at": "2016-06-20 13:20:26"
		"deleted_at": null
		"photo_name": "23_5767ed9a1f95897130987.jpg"
		}-
		2:  {
		"id": "26"
		"userid": "23"
		"source_photo_id": null
		"photo_source": null
		"photo_url": {
		"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails23_5767ed9a6758e54161303.jpg"
		"encounter": "http://localhost/liteoxide/public/uploads/others/encounters23_5767ed9a6758e54161303.jpg"
		"other": "http://localhost/liteoxide/public/uploads/others/23_5767ed9a6758e54161303.jpg"
		"original": "http://localhost/liteoxide/public/uploads/others/original/23_5767ed9a6758e54161303.jpg"
		}-
		"created_at": "2016-06-20 13:20:26"
		"updated_at": "2016-06-20 13:20:26"
		"deleted_at": null
		"photo_name": "23_5767ed9a6758e54161303.jpg"
		}-
		3:  {
		"id": "27"
		"userid": "23"
		"source_photo_id": null
		"photo_source": null
		"photo_url": {
		"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails23_5767ed9a87dd588552797.jpg"
		"encounter": "http://localhost/liteoxide/public/uploads/others/encounters23_5767ed9a87dd588552797.jpg"
		"other": "http://localhost/liteoxide/public/uploads/others/23_5767ed9a87dd588552797.jpg"
		"original": "http://localhost/liteoxide/public/uploads/others/original/23_5767ed9a87dd588552797.jpg"
		}-
		"created_at": "2016-06-20 13:20:26"
		"updated_at": "2016-06-20 13:20:26"
		"deleted_at": null
		"photo_name": "23_5767ed9a87dd588552797.jpg"
		}-

	"field_sections": [1]
		0:  {
		"section_id": "1"
		"text": "custom_profile.personalinformation"
		"fields": [6]
			0:  {
			"field_id": "2"
			"field_type": "dropdown"
			"text": "custom_profile.height"
			"options": [7]
				0:  {
				"option_id": "3"
				"text": "custom_profile.5ft"
				"is_selected": "false"
				}-
				1:  {
				"option_id": "4"
				"text": "custom_profile.55ft"
				"is_selected": "false"
				}-
				2:  {
				"option_id": "5"
				"text": "custom_profile.57ft"
				"is_selected": "false"
				}-
				3:  {
				"option_id": "6"
				"text": "custom_profile.58ft"
				"is_selected": "false"
				}-
				4:  {
				"option_id": "7"
				"text": "custom_profile.6ft"
				"is_selected": "false"
				}-
				5:  {
				"option_id": "8"
				"text": "custom_profile.62ft"
				"is_selected": "false"
				}-
				6:  {
				"option_id": "9"
				"text": "custom_profile.63ft"
				"is_selected": "false"
				}-

			}-
			1:  {
			"field_id": "3"
			"field_type": "dropdown"
			"text": "custom_profile.weight"
			"options": [13]
				0:  {
				"option_id": "10"
				"text": "custom_profile.50kg"
				"is_selected": "false"
				}-
				1:  {
				"option_id": "11"
				"text": "custom_profile.52kg"
				"is_selected": "false"
				}-
				2:  {
				"option_id": "12"
				"text": "custom_profile.53kg"
				"is_selected": "false"
				}-
				3:  {
				"option_id": "13"
				"text": "custom_profile.58kg"
				"is_selected": "false"
				}-
				4:  {
				"option_id": "14"
				"text": "custom_profile.60kg"
				"is_selected": "false"
				}-
				5:  {
				"option_id": "15"
				"text": "custom_profile.62kg"
				"is_selected": "false"
				}-
				6:  {
				"option_id": "16"
				"text": "custom_profile.64kg"
				"is_selected": "false"
				}-
				7:  {
				"option_id": "17"
				"text": "custom_profile.68kg"
				"is_selected": "false"
				}-
				8:  {
				"option_id": "18"
				"text": "custom_profile.70kg"
				"is_selected": "false"
				}-
				9:  {
				"option_id": "19"
				"text": "custom_profile.72kg"
				"is_selected": "false"
				}-
				10:  {
				"option_id": "20"
				"text": "custom_profile.74kg"
				"is_selected": "false"
				}-
				11:  {
				"option_id": "21"
				"text": "custom_profile.78kg"
				"is_selected": "false"
				}-
				12:  {
				"option_id": "22"
				"text": "custom_profile.80kg"
				"is_selected": "false"
				}-

			}-
			2:  {
			"field_id": "4"
			"field_type": "dropdown"
			"text": "custom_profile.eyecolor"
			"options": [3]
				0:  {
				"option_id": "23"
				"text": "custom_profile.black"
				"is_selected": "false"
				}-
				1:  {
				"option_id": "24"
				"text": "custom_profile.brown"
				"is_selected": "false"
				}-
				2:  {
				"option_id": "25"
				"text": "custom_profile.blue"
				"is_selected": "false"
				}-

			}
			3:  {
			"field_id": "5"
			"field_type": "dropdown"
			"text": "custom_profile.hereto"
			"options": [3]
				0:  {
				"option_id": "26"
				"text": "custom_profile.dating"
				"is_selected": "false"
				}-
				1:  {
				"option_id": "27"
				"text": "custom_profile.chatting"
				"is_selected": "false"
				}-
				2:  {
				"option_id": "28"
				"text": "custom_profile.makenewfriends"
				"is_selected": "false"
				}

			}
			4:  {
			"field_id": "6"
			"field_type": "text"
			"text": "Text"
			"value": ""
			}
			5:  {
			"field_id": "7"
			"field_type": "textarea"
			"text": "textarea"
			"value": ""
			}-

		}

		"user_popularity": {
		"popularity": 0
		"popularity_type": "very_very_low"
		}-
		"profile_complete_percentage": 15
		"user_score": {
		"score": 0
		"likes": 0
		"dislikes": 0
		}
		"user": {
		"id": "23"
		"username": "saikatdutta1991@gmail.com"
		"gender": "female"
		"name": "saikat"
		"dob": "1991-05-12"
		"city": ""
		"country": ""
		"hereto": ""
		"profile_pic_url": {
		"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/female.jpg"
		"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/female.jpg"
		"other": "http://localhost/liteoxide/public/uploads/others/female.jpg"
		"original": "http://localhost/liteoxide/public/uploads/others/original/female.jpg"
				}
		"status": ""
		"package_name": null
		"expired_at": null
		"activate_token": ""
		"password_token": ""
		"activate_user": "activated"
		"register_from": "facebook"
		"verified": "verified"
		"latitude": null
		"longitude": null
		"language": ""
		"last_request": "2016-06-20 13:31:05"
		"access_token": "$2y$10$CMQOzxo/DnpLERT8VqfpX.oVS0pAm86CnDguV0RxDdrME/3amNvy."
		"created_at": "2016-06-20 12:24:42"
		"updated_at": "2016-06-20 13:31:05"
		"deleted_at": null
		"gender_text": "Female"
		"age": 25
		"superpower_activated": "false"
		"superpower_days_left": "-9999"
		"invisible": "false"
		"online_status": "true"
		"social_links": [1] {
			0:  "facebook"
			}

		"social_verified": "true"
		"profile_picture": "female.jpg"
		}
		"about_me": ""
		"user_interests": [0]
		"profile_visitor_count": {
				"today": 0
				"this_week": 0
				"this_month": 0
				}
		"profile_visitor_difference": {
		"today_increased": "false"
		"this_week_increased": "false"
		"this_month_increased": "false"
		}
		"max_file_upload_size": {
		"value": "10"
		"unit": "MB"
		}
		"success_text": "Profile Data retrived successfully."
	}
}


```


## Edit Profile


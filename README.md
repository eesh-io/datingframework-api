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

## Get User Settings

*api/settings*

** URL Parameters **

1. user_id, access_token

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"languages": {
	"supported": [9]
	0:  "de"
	1:  "en"
	2:  "es"
	3:  "fr"
	4:  "hu"
	5:  "nl"
	6:  "pl"
	7:  "pt"
	8:  "ru"
	-
	"user_language": ""
	}-
	"notification_settings": {
	"visitor_notification": {
	"browser": 1
	"email": 1
	}-
	"like_notification": {
	"browser": 1
	"email": 1
	}-
	"match_notification": {
	"browser": 1
	"email": 1
	}-
	}-
	"privacy_settings": {
	"show_online_status": 1
	"show_distance": 1
	}-
	"invisible_settings": {
	"hide_profile_visit": 0
	"hide_superpower": 0
	}-
	"user_password_set": "true"
	"auth_user": {
	"id": "31"
	"username": "saikatdutta1991@gmail.com"
	"gender": "male"
	"name": "ʇɐʞıɐs ɐʇʇnp"
	"dob": "1991-12-05"
	"city": "Bangalore"
	"country": "India"
	"hereto": ""
	"profile_pic_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/31_576ba07ca13bb_75023432.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/31_576ba07ca13bb_75023432.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/31_576ba07ca13bb_75023432.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/31_576ba07ca13bb_75023432.jpg"
	}-
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_token": "724064975"
	"password_token": ""
	"activate_user": "activated"
	"register_from": "facebook"
	"verified": "verified"
	"latitude": "12.98"
	"longitude": "77.58"
	"language": ""
	"last_request": "2016-06-23 08:54:16"
	"access_token": "$2y$10$Fept1UrAq7QA.oGCpYlOI.Nxadz1nGto4T4dB1ciWK0wzmDcJagja"
	"created_at": "2016-06-23 08:40:28"
	"updated_at": "2016-06-23 08:54:16"
	"deleted_at": null
	"gender_text": "Male"
	"age": 24
	"superpower_activated": "false"
	"superpower_days_left": "-9999"
	"invisible": "false"
	"online_status": "true"
	"social_links": [1]{
		0:  "facebook"
		}
	"social_verified": "true"
	"profile_picture": "31_576ba07ca13bb_75023432.jpg"
	}
	"success_text": "User settings retrived successfully."
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


## Update Profile


### Update Basic Info

*api/profile/me/update-basic-info*

** URL Parameters **

1. user_id, access_token
2. name : required,
3. dob : require (dd-mm-yyyy format)
4. gender : gender_code

** Success Response **

``` javascript
{
"status": "success"
	"success_data": {
		"name": "Hello World"
		"age": 21
		"gender": "male"
		"profile_picture_url": {
			"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/male575e8fd2b435b36157926.jpg"
			"other": "http://localhost/liteoxide/public/uploads/others/male575e8fd2b435b36157926.jpg"
			"original": "http://localhost/liteoxide/public/uploads/others/original/male575e8fd2b435b36157926.jpg"
			"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/male575e8fd2b435b36157926.jpg"
			"photo_name": "male575e8fd2b435b36157926.jpg"
		}
		"success_text": "Basic information updated."
	}
}

```

** Error Response **

``` javascript
{
"status": "error"
	"error_data": {
		0: "The Name field is required."
		1: "The Gender field is required."
		2: "The Date of Birth field is required."
		"error_text": "Validation Error."
	}
}

```

### Update Custom Profile Fields

*api/profile/me/update-custom-fields*

** URL Parameters **

1. user_id, access_token
2. field_id & option_id ( For Dropdown Type )
3. field_id & value ( For Text & Textarea Type )


** Success response **

``` javascript

{
	"status": "success"
	"success_data": {
	"success_text": "Your details are saved successfully."
	}
}

```

** Error Response **

``` javascript

{
"status": "error"
	"error_data": {
	"error_text": "Choose custom fields options"
	}
}

```

### Update About Me

*api/profile/me/update-aboutme*

** URL Parameters **

1. user_id, access_token
2. about_me =>  required, less than 1000 chars

** Success Response **

``` javascript
{
	"status": "success"
	"success_data": {
	"success_text": "Your about me is saved successfully."
	}
}

```

** Error Response **

``` javascript

/* Field is Required */

{
	"status": "error"
	"error_data": {
	"error_text": "The about_me is field required."
	}
}

/* Field exceeds minimum characters */

{
	"status": "error"
	"error_data": {
	"error_text": "about_me must be within 1000 chars."
	}
}

```


### Update User Location

*api/profile/me/update-location*

** URL Parameters **

1. user_id, access_token
2. city => required
3. country => required
4. lat => required
5. lng => required

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"success_text": "Location updated successfully."
	}
}


```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	0: "The Latitude field is required."
	1: "The long field is required."
	2: "The City field is required."
	3: "The Country field is required."
	"error_text": "Validation Error."
	}
}


```


### Update Profile Picture

*api/profile/me/upload-profile-picture*

** URL Parameters **

1. user_id, access_token
2. profile_picture => raw image data type
3. crop_x , crop_y => float
4. crop_width, crop_height => int

** Success Response **

``` javascript
{
"status": "success"
"success_data": {
"photo_url": {
"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/29_576932237f4ce57066581.jpg"
"other": "http://localhost/liteoxide/public/uploads/others/29_576932237f4ce57066581.jpg"
"original": "http://localhost/liteoxide/public/uploads/others/original/29_576932237f4ce57066581.jpg"
"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/29_576932237f4ce57066581.jpg"
"photo_id": "46"
"photo_name": "29_576932237f4ce57066581.jpg"
}-
"success_text": "Profile picture uploaded successfully."
}
}
```

** Error Response **

``` javascript

{
"status": "error"
"error_data": {
0: "The crop width field is required."
1: "The crop height field is required."
2: "The crop x field is required."
3: "The crop y field is required."
"error_text": "Validation Error"
}
}

```


### Upload Other Photos

*api/profile/me/upload-other-photos*

** URL Parameters **

1. user_id, access_token
2. photos[] => array of raw image data

** Success Response **

``` javascript

{
"status": "success"
	"success_data": {
		"photo_urls": [2]
			0:  {
			"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/29_57693092370d390486704.jpg"
			"other": "http://localhost/liteoxide/public/uploads/others/29_57693092370d390486704.jpg"
			"original": "http://localhost/liteoxide/public/uploads/others/original/29_57693092370d390486704.jpg"
			"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/29_57693092370d390486704.jpg"
			"photo_id": 43
			"photo_name": "29_57693092370d390486704.jpg"
			}-
			1:  {
			"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/29_576930927302191197026.jpg"
			"other": "http://localhost/liteoxide/public/uploads/others/29_576930927302191197026.jpg"
			"original": "http://localhost/liteoxide/public/uploads/others/original/29_576930927302191197026.jpg"
			"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/29_576930927302191197026.jpg"
			"photo_id": 44
			"photo_name": "29_576930927302191197026.jpg"
			}-
	-
	"success_text": "Profile picture uploaded successfully."
	}-
}

```

** Error Response **

``` javascript

/* photos must be an array */

{
"status": "error"
"error_data": {
"error_text": "Photos must be send as array."
}
}

/* photos[] field is required */
{
"status": "error"
"error_data": {
"error_text": "The photos[] field is required."
}-
}

```

### Set Photo as Profile Picture

*api/profile/me/change-photo*

** URL Parameters **

1. user_id, access_token
2. photo_name (eg: 610_57f4d4c174f0273330056.jpg)

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"success_text": "Profile picture changed successfully."
}
}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_type": "PHOTO_NOT_FOUND"
	"error_data": {
	"error_text": "Not photo found with this photo."
	}
}


{
	"status": "error"
	"error_type": "PHOTO_ALREADY_PROFILE_PICTURE_SET"
	"error_data": {
	"error_text": "Photo already set as profie picture."
	}
}


```


### Delete Photo

*api/profile/me/delete-photo*

** URL Parameters **

1. user_id, access_token
2. photo_name

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"success_text": "Photo deleted successfully."
}
}

```

** Error Response **

``` javascript

/* Unable to delete photo. Try again later */
{
"status": "error"
"error_data": {
"error_text": "Unable to delete photo."
}-
}

 /* photo_name field is required */
{
"status": "error"
"error_data": {
"error_text": "The photo_name field is required."
}
}

```

### Get Interest Suggestions

*api/profile/me/get-interest-suggestions*

** URL Parameters **

1. user_id, access_token
2. search_text => required

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"suggestions": [1]
0:  {
"id": "1"
"interest": "Movies"
}

"success_text": "Suggestions retrived succesfully."
}
}

```

** Error Response **

``` javascript

{
"status": "error"
"error_data": {
"error_text": "Interest search text is required."
}
}

```


### Add Interest

*api/profile/me/add-interest*

** URL Parameters **

1. user_id, access_token
2. interest => required | 2-250 chars

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"interest_id": 5
"user_interest": 7
"interest_text": "hello"
"success_text": "Location updated successfully."
}
}

```

** Error Response **

``` javascript

{
"status": "error"
"error_data": {
"error_text": "Interest must be between 2 - 150"
}
}


{
"status": "error"
"error_data": {
"error_text": "Interest is required."
}
}

```

### Delete Interest

*api/profile/me/delete-interest*

** URL Parameters **

1. user_id, access_token
2. user_interest_id => required

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"success_text": "User interest deleted successfully."
}
}

```

** Error Response **

``` javascript

{
"status": "error"
"error_data": {
"error_text": "User interest id is required."
}
}


```

## View Profile By Other Users

*api/profile*

** URL Parameters **

1. user_id, access_token
2. view_user_id ( user_id of the profile to display )

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"commom_interests": "1"
	"photos": [2]
	0:  {
	"id": "8"
	"userid": "7"
	"source_photo_id": null
	"photo_source": null
	"photo_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails7_575e8c3a045a626214259.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters7_575e8c3a045a626214259.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/7_575e8c3a045a626214259.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/7_575e8c3a045a626214259.jpg"
	}-
	"created_at": "2016-06-13 10:34:34"
	"updated_at": "2016-06-13 10:34:34"
	"deleted_at": null
	"photo_name": "7_575e8c3a045a626214259.jpg"
	}-
	1:  {
	"id": "9"
	"userid": "7"
	"source_photo_id": null
	"photo_source": null
	"photo_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails7_575e8c9ab0b5967071323.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters7_575e8c9ab0b5967071323.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/7_575e8c9ab0b5967071323.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/7_575e8c9ab0b5967071323.jpg"
	}-
	"created_at": "2016-06-13 10:36:10"
	"updated_at": "2016-06-13 10:36:10"
	"deleted_at": null
	"photo_name": "7_575e8c9ab0b5967071323.jpg"
	}-
	-
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
	"is_selected": "true"
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
	-
	}-
	1:  {
	"field_id": "3"
	"field_type": "dropdown"
	"text": "custom_profile.weight"
	"options": [13]
	0:  {
	"option_id": "10"
	"text": "custom_profile.50kg"
	"is_selected": "true"
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
	-
	}-
	2:  {
	"field_id": "4"
	"field_type": "dropdown"
	"text": "custom_profile.eyecolor"
	"options": [3]
	0:  {
	"option_id": "23"
	"text": "custom_profile.black"
	"is_selected": "true"
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
	-
	}-
	3:  {
	"field_id": "5"
	"field_type": "dropdown"
	"text": "custom_profile.hereto"
	"options": [3]
	0:  {
	"option_id": "26"
	"text": "custom_profile.dating"
	"is_selected": "true"
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
	}-
	}
	4:  {
	"field_id": "6"
	"field_type": "text"
	"text": "Text"
	"value": "sadf"
	}-
	5:  {
	"field_id": "7"
	"field_type": "textarea"
	"text": "textarea"
	"value": " asfd"
	}-
	-
	}-
	-
	"user_popularity": {
	"popularity": 0
	"popularity_type": "very_very_low"
	}-
	"liked_me": -1
	"i_liked": -1
	"profile_complete_percentage": 100
	"user_score": {
	"score": 0
	"likes": 0
	"dislikes": 0
	}-
	"user": {
	"id": "7"
	"username": "saikat@gmail.com"
	"gender": "female"
	"name": "Saikat Dutta"
	"dob": "1991-02-01"
	"city": "Southegowdanahalli"
	"country": "India"
	"hereto": ""
	"profile_pic_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/7_575e8c3a045a626214259.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/7_575e8c3a045a626214259.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/7_575e8c3a045a626214259.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/7_575e8c3a045a626214259.jpg"
	}-
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_token": "223427215"
	"password_token": ""
	"activate_user": "activated"
	"register_from": "LiteOxide"
	"verified": "unverified"
	"latitude": "13.24"
	"longitude": "77.71"
	"language": "en"
	"last_request": "2016-06-20 14:57:45"
	"access_token": null
	"created_at": "2016-06-13 10:33:36"
	"updated_at": "2016-06-20 14:57:45"
	"deleted_at": null
	"gender_text": "Female"
	"age": 25
	"superpower_activated": "false"
	"superpower_days_left": "-9999"
	"invisible": "false"
	"online_status": "true"
	"social_links": [0]
	"social_verified": "false"
	"profile_picture": "7_575e8c3a045a626214259.jpg"
	}-
	"blocked": "false"
	"blocked_me": "true"
	"about_me": ""
	"distance": {
	"value": 3.3680194444774
	"unit": "Km"
	}-
	"user_interests": [2]
	0:  {
	"id": "2"
	"interest_id": "3"
	"interest_text": "adsdf"
	}-
	1:  {
	"id": "5"
	"interest_id": "1"
	"interest_text": "Movies"
	}-
	-
	"profile_visitor_count": {
	"today": 7
	"this_week": 7
	"this_month": 7
	}-
	"profile_visitor_difference": {
	"today_increased": "true"
	"this_week_increased": "true"
	"this_month_increased": "true"
	}-
	"max_file_upload_size": {
	"value": "10"
	"unit": "MB"
	}-
	"minimum_photos_required": 0
	"user_can_see_all_photos": true
	"success_text": "Profile Data retrived successfully."
	}-
	}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	"error_text": "User not found."
	}
}

```

## Profile Visitor List

*api/visitors*

** URL Parameters **

1. user_id, access_token

** Success Response **

Values for "no_visitor_reason":
CAN_SEE_VISITORS => means visitors are there.
NORMAL_NO_VISITORS => you can see visitors but nobody has visited you yet
SUPERPOWER_NOT_ACTIVATED => you can not see visitors because you have not superpower activated

``` javascript
{
	"status": "success"
	"success_data": {
	"superpower_activated": "true"
	"visitors": [1]
	0:  {
	"id": 366
	"username": "saikat.amca.12@acharya.ac.in"
	"gender": "male"
	"dob": "1992-02-19"
	"city": "Bengaluru"
	"country": "India"
	"hereto": ""
	"status": ""
	"activate_user": "activated"
	"register_from": "google"
	"verified": "verified"
	"latitude": 12.9716
	"longitude": 77.5946
	"created_at": "2016-08-05 08:55:33"
	"updated_at": "2016-08-30 13:00:29"
	"deleted_at": null
	"name": "acharya saikat"
	"language": "en"
	"last_request": "2016-08-30 13:00:28"
	"profile_picture_url": {
	"thumbnail": "http://df-dev.socialoxide.club/uploads/others/thumbnails/366_57a5cfd0b456e54762716.jpg"
	"encounter": "http://df-dev.socialoxide.club/uploads/others/encounters/366_57a5cfd0b456e54762716.jpg"
	"other": "http://df-dev.socialoxide.club/uploads/others/366_57a5cfd0b456e54762716.jpg"
	"original": "http://df-dev.socialoxide.club/uploads/others/original/366_57a5cfd0b456e54762716.jpg"
	}-
	"profile_picture_name": "366_57a5cfd0b456e54762716.jpg"
	"superpower_activated": "true"
	"online_status": "true"
	"age": 24
	"populatiry": {
	"value": "0"
	"type": "very_very_low"
	}-
	}-
	-
	"no_visitor_reason": "CAN_SEE_VISITORS"  *notes
	"paging": {
	"total": 1
	"current_page_url": "http://df-dev.socialoxide.club/api/visitors?page=1"
	"more_pages": "false"
	"prevous_page_url": ""
	"next_page_url": ""
	"last_page_url": "http://df-dev.socialoxide.club/api/visitors?page=1"
	}
	"success_text": "Visitors retrived successfully."
	}
}

```

# Abuse Report & Block

## Report User

*api/report/user*

** URL Parameters **

1. user_id, access_token,
2. reported_user_id => required
3. reason => required

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"success_text": "Report against user done successfully."
	}
}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	"error_text": "Reported user's id is required"
	}
}

{
	"status": "error"
	"error_data": {
	"error_text": "Reason is required"
	}
}

```

## Report Photo

*api/report/photo*

** URL Parameters **

1. user_id, access_token
2. photo_name => required
3. reason => required


** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"success_text": "Report against photo done successfully."
	}
}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	"error_text": "Photo name is required"
	}
}

{
	"status": "error"
	"error_data": {
	"error_text": "Reason is required"
	}
}

```

## Block an User

*api/user/block*

** URL Parameters **

1. user_id, access_token,
2. block_user_id --> required

** Success Response **

``` javascript
{
	"status": "success"
	"success_data": {
	"success_text": "User blocked successfully."
	}
}


```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	"error_text": "User block_user_id is required."
	}
}



{
	"status": "error"
	"error_data": {
	"error_text": "You cant block yourself."
	}
}

```

## Unblock User

*api/user/unblock*

** URL Parameters **

1. user_id, access_token,
2. blocked_user_id --> required

** Success Response **

``` javascript


{
	"status": "success"
	"success_data": {
	"success_text": "User unblocked successfully."
	}
}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	"error_text": "User blocked_user_id is required."
	}
}


{
	"status": "error"
	"error_data": {
	"error_text": "You cant unblock yourself."
	}
}


```

## Get Blocked Users List

*api/user/blocks*

** URL Parameters **

1. user_id, access_token

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"block_users_count": 1
	"block_users": [1]
	0:  {
	"id": "5"
	"username": "saikatdutta@gmail.com"
	"gender": "female"
	"name": "ʇɐʞıɐs ɐʇʇnp"
	"dob": "1991-12-05"
	"city": "Bangalore"
	"country": "India"
	"hereto": ""
	"profile_pic_url": "5_575c1e785d7a2_52889064.jpg"
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_token": ""
	"password_token": ""
	"register_from": "vk"
	"verified": "verified"
	"latitude": "12.97"
	"longitude": "77.59"
	"language": ""
	"last_request": "2016-06-11 15:03:15"
	"access_token": null
	"created_at": "2016-06-11 14:21:44"
	"updated_at": "2016-06-11 15:03:15"
	"deleted_at": null
	"activated": "activated"
	"age": 24
	}
	"success_text": "Blocked users list retrived successfully."
	}
}

```


# User Account

## Change Email

*api/settings/change/email*

** URL Parameters **

1. user_id, access_token
2. email

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"user_account_activated": "true"
"success_text": "Email has changed successfully."
}
}

```

** Error Response **

``` javascript

{
"status": "error"
"error_data": {
"error_text": "The email has already been taken."
}
}



{
"status": "error"
"error_data": {
"error_text": "The email field is required."
}
}

```



## Change Password

*api/settings/change/password*

** URL Parameters **

1. user_id, access_token
2. old_password => required
3. password => required
4. confirm_password => required

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"success_text": "Password has changed successfully."
}
}

```

** Error Response **

``` javascript

{
"status": "error"
"error_data": {
"error_text": "Wrong old password."
}
}

{
"status": "error"
"error_data": {
"error_text": "Confirm password not matched."
}
}


{
"status": "error"
"error_data": {
"error_text": "Password is required"
}
}

```

## Forgot Password

** URL Parameters **

1. username

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"success_text": "Password recovery link has been sent to your registered email id. Please reset your password."
}
}

```

** Error Response **

``` javascript

{
"status": "error"
"error_data": {
"error_text": "Invalid email id."
}
}

{
"status": "error"
"error_data": {
"error_text": "Email not sent. Try again."
}
}

```

## Update Default Language

*api/settings/save/language*

** URL Parameters **

1. user_id, access_token
2. language => required

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"success_text": "User language saved successfully."
}
}


```

** Error Response **

``` javascript

{
"status": "error"
"error_data": {
"error_text": "Language is required."
}
}

```


## Update Notifications  ( TO BE UPDATED )

*api/settings/save/notification*

** URL Parameters **

1. user_id, access_token
2. browser_visitor, email_visitor --> optional(require 1/0) if not then send 0 else 1, 
3. browser_liked, email_liked, --> optional(require 1/0) if not then send 0 else 1, 
4. browser_match, email_match, --> optional(require 1/0) if not then send 0 else 1,

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"success_text": "Notification settings saved successfully."
}
}

```

## Update Privacy

*api/settings/save/privacy*

** URL Parameters **

1. user_id, access_token
2. show_online_status --> optional(require 1/0) if not then send 0 else 1, 
3. show_distance, --> optional(require 1/0) if not then send 0 else 1, 

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"success_text": "Privacy settings saved successfully."
}
}

```

## Update Invisibility Settings

*api/settings/save/invisible*

** URL Parameters **

1. user_id, access_token
2. hide_profile_visit --> optional(require 1/0) if not then send 0 else 1, 
3. hide_superpowers --> optional(require 1/0) if not then send 0 else 1,

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"success_text": "Invisible settings saved successfully."
}
}

```

** Error Response **

``` javascript

{
"status": "error"
"error_data": {
"user_superpower": "false"
"error_text": "User superpower not activated"
}
}

```


## Deactivate Account

*api/settings/user/deactivate*

** URL Parameters **

1. user_id, access_token

** Success Response **

``` javascript

{
"status": "success"
"success_data": {
"success_text": "User deactivated successfully."
}
}

```


## Delete Account

*api/settings/user/delete*

** URL Parameters **

1. user_id, access_token
2. password

** Error Response **

``` javascript
{
"status": "error"
"error_data": {
"error_text": "User password not matched."
}
}

{
"status": "error"
"error_data": {
"error_text": "Authentication Error"
}
}

```


# People Nearby

## Get People Nearby

*api/people-nearby*

** URL Parameters **

1. user_id, access_token

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"riseup_credits": "20"
	"filter_data": {
	"perfered_ages": {
	"min": "18"
	"max": "80"
	}-
	"prefered_genders": [2]
	0:  "male"
	1:  "female"
	-
	"prefered_online_status": "all" or "online"
	"perfered_distance": {
	"value": "100"
	"unit": "km"
	}-
	}-
	"nearby_users": [3]
	0:  {
	"id": "30"
	"username": "saikatdutta1991@gmail.commm"
	"gender": "male"
	"name": "ʇɐʞıɐs ɐʇʇnp"
	"dob": "1991-12-05"
	"city": "Bangalore"
	"country": "India"
	"hereto": ""
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_user": "activated"
	"register_from": "facebook"
	"verified": "verified"
	"latitude": "12.98"
	"longitude": "77.58"
	"language": ""
	"last_request": "2016-06-22 14:45:41"
	"created_at": "2016-06-22 14:39:00"
	"updated_at": "2016-06-22 14:45:41"
	"deleted_at": null
	"profile_picture_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/30_576aa304723c6_42836200.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/30_576aa304723c6_42836200.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/30_576aa304723c6_42836200.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/30_576aa304723c6_42836200.jpg"
	}-
	"profile_picture_name": "30_576aa304723c6_42836200.jpg"
	"superpower_activated": "false"
	"online_status": "false"
	"age": 24
	"raised": "true"
	"populatiry": {
	"value": ""
	"type": "very_very_low"
	}-
	"profile": {
	"id": "30"
	"userid": "30"
	"prefer_gender": "male,female"
	"prefer_age": "18-80"
	"prefer_online_status": null
	"prefer_distance_nearby": "100"
	"popularity": null
	"aboutme": ""
	"latitude": null
	"longitude": null
	"created_at": "2016-06-22 14:39:00"
	"updated_at": "2016-06-22 14:39:00"
	"deleted_at": null
	}-
	}-
	1:  {
	"id": "7"
	"username": "saikat@gmail.com"
	"gender": "female"
	"name": "Saikat Dutta"
	"dob": "1991-02-01"
	"city": "Southegowdanahalli"
	"country": "India"
	"hereto": ""
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_user": "activated"
	"register_from": "LiteOxide"
	"verified": "unverified"
	"latitude": "13.24"
	"longitude": "77.71"
	"language": "en"
	"last_request": "2016-06-23 10:07:59"
	"created_at": "2016-06-13 10:33:36"
	"updated_at": "2016-06-23 10:07:59"
	"deleted_at": null
	"profile_picture_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/7_575e8c3a045a626214259.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/7_575e8c3a045a626214259.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/7_575e8c3a045a626214259.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/7_575e8c3a045a626214259.jpg"
	}-
	"profile_picture_name": "7_575e8c3a045a626214259.jpg"
	"superpower_activated": "false"
	"online_status": "false"
	"age": 25
	"raised": "true"
	"populatiry": {
	"value": ""
	"type": "very_very_low"
	}-
	"profile": {
	"id": "7"
	"userid": "7"
	"prefer_gender": "male,female"
	"prefer_age": "18-80"
	"prefer_online_status": null
	"prefer_distance_nearby": "100"
	"popularity": null
	"aboutme": ""
	"latitude": null
	"longitude": null
	"created_at": "2016-06-13 10:33:36"
	"updated_at": "2016-06-13 10:33:36"
	"deleted_at": null
	}-
	}-
	2:  {
	"id": "5"
	"username": "saikatdutta@gmail.com"
	"gender": "female"
	"name": "ʇɐʞıɐs ɐʇʇnp"
	"dob": "1991-12-05"
	"city": "Bangalore"
	"country": "India"
	"hereto": ""
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_user": "activated"
	"register_from": "vk"
	"verified": "verified"
	"latitude": "12.97"
	"longitude": "77.59"
	"language": ""
	"last_request": "2016-06-11 15:03:15"
	"created_at": "2016-06-11 14:21:44"
	"updated_at": "2016-06-11 15:03:15"
	"deleted_at": null
	"profile_picture_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/5_575c1e785d7a2_52889064.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/5_575c1e785d7a2_52889064.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/5_575c1e785d7a2_52889064.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/5_575c1e785d7a2_52889064.jpg"
	}-
	"profile_picture_name": "5_575c1e785d7a2_52889064.jpg"
	"superpower_activated": "false"
	"online_status": "false"
	"age": 24
	"raised": "false"
	"populatiry": {
	"value": ""
	"type": "very_very_low"
	}
	"credit_balance": "1000"
	}
	"paging": {
	"total": 3
	"current_page_url": "http://localhost/liteoxide/public/api/people-nearby?page=1"
	"more_pages": "false"
	"prevous_page_url": ""
	"next_page_url": ""
	"last_page_url": "http://localhost/liteoxide/public/api/people-nearby?page=1"
	}
	"success_text": "Nearby peoples retrieved successfully."
	}
}

```

## Change Peope Nearby Location

*api/people-nearby/set-profile-location*

** URL Parameters **

1. user_id, access_token
2. city, country, lat, lng => All Required

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"success_text": "Profile location saved successfully."
	}
}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	"error_text": "All fields are required."
	}
}

```

## Show Only Online Users

*api/people-nearby/filter/online-status/save*

** URL Parameters **

1. user_id, access_token
2. preferred_online_status => [all, online]

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"success_text": "Search filter prefered online status saved successfully."
	}
}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	"perfered_online_status": "Must be online or all"
	"error_text": "Validation error"
	}
}

```

## Save Filters

*api/people-nearby/filter/save*

** URL Parameters **

*api/people-nearby/filter/save*

1. user_id, access_token
2. prefered_genders --> require (genders code with coma seperated) eg. male,female
3. prefered_ages --> required (numeric with coma seperated) eg 18-80
4. prefered_distance --> required (numeric)

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"success_text": "Search filter saved successfully."
	}
}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	"perfered_genders": "Check format"
	"error_text": "Validation error"
	}
}


{
	"status": "error"
	"error_data": {
	"perfered_ages": "Check format"
	"error_text": "Validation error"
	}
}

```




# Encounters

## Get Encounters

*api/encounters*

** URL Parameters **

1. user_id, access_token

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"encounters_left": 9999
	"encouters": [1]
	0:  {
	"id": "30"
	"username": "saikatdutta1991@gmail.commm"
	"gender": "male"
	"name": "ʇɐʞıɐs ɐʇʇnp"
	"dob": "1991-12-05"
	"city": "Bangalore"
	"country": "India"
	"hereto": ""
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_user": "activated"
	"register_from": "facebook"
	"verified": "verified"
	"latitude": "12.98"
	"longitude": "77.58"
	"language": ""
	"last_request": "2016-06-22 14:45:41"
	"created_at": "2016-06-22 14:39:00"
	"updated_at": "2016-06-22 14:45:41"
	"deleted_at": null
	"common_interest_count": "0"
	"profile_picture_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/30_576aa304723c6_42836200.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/30_576aa304723c6_42836200.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/30_576aa304723c6_42836200.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/30_576aa304723c6_42836200.jpg"
	}-
	"profile_picture_name": "30_576aa304723c6_42836200.jpg"
	"superpower_activated": "false"
	"online_status": "false"
	"age": 24
	"social_links": [1]{ 
		0:  "facebook"
		}
	"social_verified": "true"
	"photos": {
	"count": 1
	"items": [1]
	0:  {
	"id": "49"
	"photo_name": "30_576aa304723c6_42836200.jpg"
	"encoutner_photo_url": "http://localhost/liteoxide/public/uploads/others/encounters/30_576aa304723c6_42836200.jpg"
	"thumbnail_photo_url": "http://localhost/liteoxide/public/uploads/others/thumbnails/30_576aa304723c6_42836200.jpg"
	"original_photo_url": "http://localhost/liteoxide/public/uploads/others/original/30_576aa304723c6_42836200.jpg"
	"other_photo_url": "http://localhost/liteoxide/public/uploads/others/30_576aa304723c6_42836200.jpg"
	}
	
	}
	"liked_me": "0"
	}

	"success_text": "Encounters retrived successfully."
	}

}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	"encounters_left": "0"
	"error_text": "No encouters"
	}
}

```

## Like/Dislike a User

*api/encounter/user/like*

** URL Parameters **

1. user_id, access_token
2. encounter_id -> required
3. like --> required value are _like or _dislike

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"match_found": "false"
	"success_text": "User encountered successfully."
	}
}

{
"status": "success"
	"success_data": {
	"match_found": "true"
	"success_text": "User encountered successfully."
	}
}


```

** Error Response **

``` javascript

{
"status": "error"
	"error_data": {
	"encounter_id": "User to be liked is not valid."
	"error_text": "Validation error."
	}
}




{
"status": "error"
	"error_data": {
	"like": "Like or dislike is required or format error"
	"error_text": "Validation error."
	}
}


{
"status": "error"
	"error_data": {
	"error_text": "Some error occured or may be already encountered."
	}
}


```

## Get Matched Users

*api/matches*

** URL Parameters **

1. user_id, access_token

** Success Response for Superpower Users **

``` javascript

{
	"status": "success"
	"success_data": {
	"superpower_activated": "false"
	"matched_users": [2]
	0:  {
	"id": "33"
	"username": "ritu29jun@gmail.com"
	"gender": "female"
	"name": "RiSita Ritu Hazra"
	"dob": "1971-01-19"
	"city": "Hyderabad"
	"country": "India"
	"hereto": ""
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_user": "activated"
	"register_from": "facebook"
	"verified": "verified"
	"latitude": "17.39"
	"longitude": "78.49"
	"language": "es"
	"last_request": "2016-06-27 13:27:20"
	"created_at": "2016-06-25 18:08:53"
	"updated_at": "2016-06-27 13:27:20"
	"deleted_at": null
	"profile_picture_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/33_576ec8b56407e_11313141.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/33_576ec8b56407e_11313141.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/33_576ec8b56407e_11313141.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/33_576ec8b56407e_11313141.jpg"
	}-
	"profile_picture_name": "33_576ec8b56407e_11313141.jpg"
	"superpower_activated": "false"
	"online_status": "false"
	"age": 45
	"populatiry": {
	"value": "0"
	"type": "very_very_low"
	}-
	"credit_balance": "990"
	}-
	1:  {
	"id": "7"
	"username": "saikat@gmail.com"
	"gender": "female"
	"name": "Saikat Dutta"
	"dob": "1991-02-01"
	"city": "Southegowdanahalli"
	"country": "India"
	"hereto": ""
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_user": "activated"
	"register_from": "LiteOxide"
	"verified": "unverified"
	"latitude": "13.24"
	"longitude": "77.71"
	"language": "en"
	"last_request": "2016-06-27 09:07:14"
	"created_at": "2016-06-13 10:33:36"
	"updated_at": "2016-06-27 09:07:14"
	"deleted_at": null
	"profile_picture_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/7_576ced051cfa926071522.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/7_576ced051cfa926071522.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/7_576ced051cfa926071522.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/7_576ced051cfa926071522.jpg"
	}
	"profile_picture_name": "7_576ced051cfa926071522.jpg"
	"superpower_activated": "false"
	"online_status": "false"
	"age": 25
	"populatiry": {
	"value": "0"
	"type": "very_very_low"
	}-
	"credit_balance": "960"
	}-
	"paging": {
	"total": 2
	"current_page_url": "http://localhost/liteoxide/public/api/matches?page=1"
	"more_pages": "false"
	"prevous_page_url": ""
	"next_page_url": ""
	"last_page_url": "http://localhost/liteoxide/public/api/matches?page=1"
	}-
	"success_text": "Matched users retrived successfully."
	}
}


```

** Success Response for Non-Superpower Users **

``` javascript

{
	"status": "success"
	"success_data": {
	"superpower_activated": "false"
	"matched_users": [0]
	"paging": {
	"total": 2
	"current_page_url": "http://localhost/liteoxide/public/api/matches?page=1"
	"more_pages": "false"
	"prevous_page_url": ""
	"next_page_url": ""
	"last_page_url": "http://localhost/liteoxide/public/api/matches?page=1"
	}
	"success_text": "Matched users retrived successfully."
	}
}


```


## My Likes

*api/mylikes*

** URL Parameters **

1. user_id, access_token

** Success Response for Superpower Users **

``` javascript

{
	"status": "success"
	"success_data": {
	"superpower_activated": "false"
	"my_liked_users": [0]
	"paging": {
	"total": 2
	"current_page_url": "http://localhost/liteoxide/public/api/mylikes?page=1"
	"more_pages": "false"
	"prevous_page_url": ""
	"next_page_url": ""
	"last_page_url": "http://localhost/liteoxide/public/api/mylikes?page=1"
	}
	"success_text": "My liked users retrived successfully."
	}
}

```

** Success Response for Non-Superpower Users **

``` javascript

	{
	"status": "success"
	"success_data": {
	"superpower_activated": "false"
	"my_liked_users": [2]
	0:  {
	"id": "33"
	"username": "ritu29jun@gmail.com"
	"gender": "female"
	"name": "RiSita Ritu Hazra"
	"dob": "1971-01-19"
	"city": "Hyderabad"
	"country": "India"
	"hereto": ""
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_user": "activated"
	"register_from": "facebook"
	"verified": "verified"
	"latitude": "17.39"
	"longitude": "78.49"
	"language": "es"
	"last_request": "2016-06-27 13:27:20"
	"created_at": "2016-06-25 18:08:53"
	"updated_at": "2016-06-27 13:27:20"
	"deleted_at": null
	"profile_picture_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/33_576ec8b56407e_11313141.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/33_576ec8b56407e_11313141.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/33_576ec8b56407e_11313141.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/33_576ec8b56407e_11313141.jpg"
	}-
	"profile_picture_name": "33_576ec8b56407e_11313141.jpg"
	"superpower_activated": "false"
	"online_status": "false"
	"age": 45
	"populatiry": {
	"value": "0"
	"type": "very_very_low"
	}-
	"credit_balance": "990"
	}-
	1:  {
	"id": "7"
	"username": "saikat@gmail.com"
	"gender": "female"
	"name": "Saikat Dutta"
	"dob": "1991-02-01"
	"city": "Southegowdanahalli"
	"country": "India"
	"hereto": ""
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_user": "activated"
	"register_from": "LiteOxide"
	"verified": "unverified"
	"latitude": "13.24"
	"longitude": "77.71"
	"language": "en"
	"last_request": "2016-06-27 09:07:14"
	"created_at": "2016-06-13 10:33:36"
	"updated_at": "2016-06-27 09:07:14"
	"deleted_at": null
	"profile_picture_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/7_576ced051cfa926071522.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/7_576ced051cfa926071522.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/7_576ced051cfa926071522.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/7_576ced051cfa926071522.jpg"
	}-
	"profile_picture_name": "7_576ced051cfa926071522.jpg"
	"superpower_activated": "false"
	"online_status": "false"
	"age": 25
	"populatiry": {
	"value": "0"
	"type": "very_very_low"
	}-
	"credit_balance": "960"
	}-
	"paging": {
	"total": 2
	"current_page_url": "http://localhost/liteoxide/public/api/mylikes?page=1"
	"more_pages": "false"
	"prevous_page_url": ""
	"next_page_url": ""
	"last_page_url": "http://localhost/liteoxide/public/api/mylikes?page=1"
	}
	"success_text": "My liked users retrived successfully."
	}
}


```

## Who Liked Me

*api/likes*

** URL Parameters **

1. user_id, access_token

** Success Response for Superpower Users ** 

``` javascript

{
	"status": "success"
	"success_data": {
	"superpower_activated": "false"
	"users_liked_me": [1]
	0:  {
	"id": "33"
	"username": "ritu29jun@gmail.com"
	"gender": "female"
	"name": "RiSita Ritu Hazra"
	"dob": "1971-01-19"
	"city": "Hyderabad"
	"country": "India"
	"hereto": ""
	"status": ""
	"package_name": null
	"expired_at": null
	"activate_user": "activated"
	"register_from": "facebook"
	"verified": "verified"
	"latitude": "17.39"
	"longitude": "78.49"
	"language": "es"
	"last_request": "2016-06-27 13:27:20"
	"created_at": "2016-06-25 18:08:53"
	"updated_at": "2016-06-27 13:27:20"
	"deleted_at": null
	"profile_picture_url": {
	"thumbnail": "http://localhost/liteoxide/public/uploads/others/thumbnails/33_576ec8b56407e_11313141.jpg"
	"encounter": "http://localhost/liteoxide/public/uploads/others/encounters/33_576ec8b56407e_11313141.jpg"
	"other": "http://localhost/liteoxide/public/uploads/others/33_576ec8b56407e_11313141.jpg"
	"original": "http://localhost/liteoxide/public/uploads/others/original/33_576ec8b56407e_11313141.jpg"
	}-
	"profile_picture_name": "33_576ec8b56407e_11313141.jpg"
	"superpower_activated": "false"
	"online_status": "false"
	"age": 45
	"populatiry": {
	"value": "0"
	"type": "very_very_low"
	}-
	"credit_balance": "990"
	}-
	-
	"paging": {
	"total": 2
	"current_page_url": "http://localhost/liteoxide/public/api/likes?page=1"
	"more_pages": "true"
	"prevous_page_url": ""
	"next_page_url": "http://localhost/liteoxide/public/api/likes?page=2"
	"last_page_url": "http://localhost/liteoxide/public/api/likes?page=2"
	}-
	"success_text": "Users liked me retrived successfully."
	}
}


```


** Success Response for Non-Superpower User **

``` javascript

{
	"status": "success"
	"success_data": {
	"superpower_activated": "false"
	"users_liked_me": [0]
	"paging": {
	"total": 2
	"current_page_url": "http://localhost/liteoxide/public/api/likes?page=1"
	"more_pages": "false"
	"prevous_page_url": ""
	"next_page_url": ""
	"last_page_url": "http://localhost/liteoxide/public/api/likes?page=1"
	}-
	"success_text": "Users liked me retrived successfully."
	}
}


```




# Social Logins

## Google

### Get Google App ID

*api/google/get-app-id*

** URL Parameters **

No Parameters

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"facebook_app_id": "29058361293-qbkner1sb2ivp2itcsm1ertmtgjmutkt.apps.googleusercontent.com"
	"success_text": "Google Api Key retrived successfully."
	}
}

```
 


### Google Sign In

You need to use the Google SDK to sign in the user and get the user details, and then post those details to this API

*api/google*

** URL Parameters **

1. google_id:required
2. email:required
3. country:optional
4. city:optional
5. latitude:optional
6. longitude:optional
7. avatar_url:required
8. gender:optional
9. name: optional
10. birthday: optional
11. is_default_picture : required


** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"user_id": 29
	"name": ""
	"username": "saikatdutta1991@gmail.com"
	"access_token": "$2y$10$7Rhuta4b47.l9wyULeU8HOg8IK7Q37j36otY.xfQGGY/Ln6qYJ5TO"
	"last_request_timestamp": null
	"data_incomplete": "true"
	"success_text": "User registered successfully."
	}
}



{
	"status": "success"
	"success_data": {
	"user_id": "29"
	"name": ""
	"username": "saikatdutta1991@gmail.com"
	"access_token": "$2y$10$FXqq9/AX.6D.7WqC6Ebpm.BUrZT304Sfvy.NdZwzSOU6OwrkGT3bi"
	"last_request_timestamp": null
	"data_incomplete": "true"
	"success_text": "User logged in successfully."
	}
}

```

** Error Response **

``` javascript

{
"status": "error"
	"error_data": {
	"google_id": "The google_id field is required."
	"avatar_url": "The avatar_url field is required."
	"email": "The email field is required."
	"is_default_picture": "The is_default_picture field is required."
	}
}


```


## Facebook

### Get Facebook ID

*api/facebook/get-app-id*

** URL Parameters **

No Parameters

** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"facebook_app_id": "902618216496515"
	"success_text": "Facebook Api Key retrived successfully."
	}
}

```

### Sign in With Facebook

Sign in using the Facebook SDK and pass the returned values to this API:

*api/facebook*

** URL Parameters **

1. facebook_id: required
2. email: optional
3. country; optional
4. city: optional
5. latitude: optional
6. longitude: optional
7. avatar_url: required
8. gender: optional
9. name: required
10. birthday: optional
11. is_default_picture: required


** Success Response **

``` javascript

{
	"status": "success"
	"success_data": {
	"user_id": 23
	"name": "saikat"
	"username": "saikatdutta1991@gmail.com"
	"access_token": "$2y$10$efyYAQgaWZakYGP1U8V8Ee9/FuXv9r4Njq9QuKO9ulwAQjyMeThHO"
	"last_request_timestamp": null
	"data_incomplete": "true"
	"success_text": "User registered successfully."
	}
}



{
	"status": "success"
	"success_data": {
	"user_id": "23"
	"name": "saikat"
	"username": "saikatdutta1991@gmail.com"
	"access_token": "$2y$10$ax6FzenL9NWqY7mS7tEKd.GCR0zBtOMWIPBYPAEsaa7zTPPE.FXEq"
	"last_request_timestamp": "2016-06-20 12:35:37"
	"data_incomplete": "true"
	"success_text": "User logged in successfully."
	}
}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_data": {
	"facebook_id": "The facebook_id field is required."
	"avatar_url": "The avatar_url field is required."
	}
}


```

# WebSocket Chat

Your client must be using the Socket.IO Library

## Connecting to Socket

### Get Socket Details

*api/chat/server-details*

** URL Parameters **

No Parameters

** Success Response **

Use the *url* to connect via the Socket.IO Library. After connecting the message "connected" will be emitted from server. This event will contain the *socket_id*

``` javascript

{
		"status": "success"
		"details": {
			"domain": "http://yourdatingframeworkwebsite.club"
			"port": 24532
			"url": "http://yourdatingframeworkwebsite.club:24532" // this is the url to connect
		}
	}

```

### Map Socket with the Logged in User

*api/chat/map-user-socket*

** URL Parameters **

1. user_id, access_token
2. socket_id

** Success Response **

All the images in chat shoudd have the url of *base_chat_image_url*

``` javascript

{
"status": "success"
"success_type": "USER_SOCKET_MAPPED"
"base_chat_images_url": "http://yourdatingframeworkwebsite.club/uploads/chat"
}

```

### Get Chat Contacts List

*api/chat/users*

** URL Parameters **

1. user_id, access_token
2. last_contact_id -> optional

** Success Response **

``` javascript

{
	"status": "success"
	"success_type": "FIRST_20_USERS_RETRIVED"
	"chat_users": [2]
	0:  {
	"user": {
	"id": 546
	"username": "jothikarthik@gmail.com"
	"gender": "Male"
	"dob": "1990-08-30"
	"city": "Chennai"
	"country": "India"
	"hereto": ""
	"profile_pic_url": "546_57c52a2c9143652097543.jpg"
	"status": ""
	"activate_user": "activated"
	"register_from": "SocialOxide"
	"verified": "unverified"
	"latitude": 13.0591
	"longitude": 80.2748
	"created_at": "2016-08-30 06:39:23"
	"updated_at": "2016-09-19 14:04:51"
	"deleted_at": null
	"name": "karthi karthi"
	"slug_name": "karthi-karthi"
	"language": "en"
	"last_request": "2016-08-30 06:42:35"
	"remember_token": null
	"profile_picture": "http://df-dev.socialoxide.club/uploads/others/thumbnails/546_57c52a2c9143652097543.jpg"
	"age": 26
	"isTyping": false
	"last_msg": ""
	"last_msg_type": 0
	"messages": [0]
	"total_messages_count": 0
	"total_unread_messages_count": 0
	"total_photos_count": 1
	"score": 8.75
	"can_init_chat": false
	"init_chat_error_type": "CHAT_INIT_HOURS_EXPIRED"
	}-
	"online": 0
	"matched": 0
	"is_contacted": 1
	"contact_id": 397
	"contacted_timestamp": "2016-10-13 12:49:56"
	}-
	1:  {
	"user": {
	"id": 670
	"username": "saikat.amca.12@acharya.ac.in"
	"gender": "male"
	"dob": "1991-10-13"
	"city": "Bengaluru"
	"country": "India"
	"hereto": ""
	"profile_pic_url": "670_57fe0ccf7c7f070430731.jpg"
	"status": ""
	"activate_user": "activated"
	"register_from": ""
	"verified": "verified"
	"latitude": 12.9716
	"longitude": 77.5946
	"created_at": "2016-10-10 12:55:19"
	"updated_at": "2016-10-14 10:34:34"
	"deleted_at": null
	"name": "Saikat Acharya"
	"slug_name": "saikat-acharya"
	"language": "en"
	"last_request": "2016-10-14 10:34:34"
	"remember_token": "GCkVTrIURu19drjDhPgKikMDgLRBjY5WiAqwkKRbtgFn2KtwzByValIDsSe9"
	"profile_picture": "http://df-dev.socialoxide.club/uploads/others/thumbnails/670_57fe0ccf7c7f070430731.jpg"
	"age": 25
	"isTyping": false
	"last_msg": "676_5800c31d61c2942107357.jpg"
	"last_msg_type": 2
	"messages": [0]
	"total_messages_count": 28
	"total_unread_messages_count": 0
	"can_init_chat": true
	}-
	"online": 0
	"matched": 1
	"is_contacted": 1
	"contact_id": 392
	"contacted_timestamp": "2016-10-12 10:27:24"
	}-
	-
	"total_contacts_count": 2
	"overall_unread_messages_count": 0
}

```

### Get only Contacts Count

*api/chat/contacts-count*

** URL Parameters **

1. user_id, access_token

** Success Response **

``` javascript

{
"status": "success"
"total_contacts_count": 3
}

```

## Add a contact

*api/chat/add-to-contact*

** URL Parameters **

1. user_id, access_token
2. other_user_id

** Success Response **

``` javascript

{
	"status": "success"
	"success_type": "NEW_CONTACT"
	"contact": {
	"user1": 676
	"user2": 120
	"source": 676
	"updated_at": "2016-10-14 11:58:40"
	"created_at": "2016-10-14 11:58:40"
	"id": 400
	}
}

```

** Error Response **

``` javascript

{
	"status": "error"
	"error_type": "ALREADY_CONTACTED"
	"contact": {
	"id": 397
	"user1": 676
	"user2": 546
	"source": "676"
	"created_at": "2016-10-13 12:49:56"
	"updated_at": "2016-10-13 12:49:56"
	"deleted_at": null
	}
}

{
	"status": "error"
	"error_type": "UNKNOWN_ERROR"
	"error_text": "Trying to get property of non-objectfile : /home/username/webapps/datingframework_dev/app/Plugins/WebsocketChatPlugin/repositories/WebsocketChatRepository.phpon line : 127"
}


{
	"status": "error"
	"error_type": "OTHE_USER_ID_INVALID"
	"error_text": "other_user_id is required"
}

```

## Delete Contact

*api/chat/contact/delete*

** URL Parameters **

1. user_id, access_token
2. contact_id

** Success Response **

``` javascript
{
"status": "success"
"success_type": "CONTACT_DELETED"
"success_text": "Contact deleted"
}
```

** Error Response **

``` javascript

{
"status": "error"
"error_type": "NOT_AUTHORISE_TO_DELETE"
"error_text": "Not authorise to delete"
}


```

## Get Messages of a User

*api/chat/messages*

** URL Parameters **

1. user_id, other_user_id, access_token
2. last_message_id --> optional (user to retrive more message before the message id)

** Success Response **

``` javascript

{
	"status": "success"
	"success_type": "LAST_20_MESSAGES_RETRIVED"
	"messages": [20]

	0:  {
	"id": 1232
	"from_user": 676
	"to_user": 670
	"contact_id": 392
	"text": "asdf"
	"type": 0
	"meta": ""
	"status": "read"
	"created_at": "2016-10-13 15:33:29"
	"updated_at": "2016-10-14 10:34:34"
	"deleted_at": null
	}-

	1:  {
	"id": 1249
	"from_user": 676
	"to_user": 670
	"contact_id": 392
	"text": ""
	"type": 2
	"meta": "676_5800c31d61c2942107357.jpg"
	"status": "unread"
	"created_at": "2016-10-14 11:35:57"
	"updated_at": "2016-10-14 11:35:57"
	"deleted_at": null
	"image_url": "http://df-dev.socialoxide.club/uploads/chat/676_5800c31d61c2942107357.jpg"
	}

}


```

** Error Response **

``` javascript

{
"status": "error"
"error_type": "INVALID_OTHER_USER_ID"
"error_text": "other_user_id required"
}

```

## Delete Message

*api/chat/message/delete*

** URL Parameters **

1. user_id, access_token
2. message_id => required

** Success Response **

``` javascript

{
"status": "success"
"success_type": "MESSAGE_DELETED"
"success_text": "Message deleted"
}

```

** Error Response **

``` javascript

{
"status": "error"
"error_type": "FAILED_TO_DELETE_MESSAGE"
"error_text": "Failed to delete message"
}

```

## Mark Messages as Read

*api/chat/messages/mark-read*

** URL Parameters **

1. user_id, access_token
2. other_user_id => (optional) to mark only messages from this user as read
3. read_all => (optional) to mark all unread messages from all users as read for a user.

Either other_user_id or read_all is required

** Success Response **

``` javascript

{
"status": "success"
"success_type": "MARK_READ_ALL_MESSAGES_OF_USER_ID_111"
"success_text": "All messages marked read"
}


{
"status": "success"
"success_type": "MARK_READ_ALL_MESSAGES"
"success_text": "All messages marked read"
}

```

## Upload image for sending to user

*api/chat/upload/image*

** URL Parameters **

1. user_id, access_token
2. image => raw image data

** Success Response **

The response will have *image_url* , that should be emitted in the *new_message* socket event.

``` javascript

{
"status": "success"
"success_type": "IMAGE_UPLOADED"
"image": "676_5800cec02f8db25964936.jpg"
"image_url": "http://yourdatingframeworkwebsite.club/uploads/chat/676_5800cec02f8db25964936.jpg"
}


```

** Error Response **

``` javascript

{
"status": "error"
"error_type": "IMAGE_INVALID"
"error_text": "image param is reqired"
}

{
"status": "error"
"error_type": "INVALID_IMAGE_FILE"
"error_text": "invalid image"
}

```


## WebSocket Events

| connected            | This event will be fired from server when you connected to server with data                                                                       |                           Receive Data: socket_id                           |
|----------------------|---------------------------------------------------------------------------------------------------------------------------------------------------|:---------------------------------------------------------------------------:|
| user_socket_mapped   |                       After connected to socket and socket user mapped api call. This event should be emit from client side                       | No Data                                                                     |
| user_online          | This event will come from server when a user comes online                                                                                         | Receive Data: user_id                                                       |
| new_message          | This event should be emitted from client when sending a new message. There are two message types. 0 for normal text message. 1 for image message. | Send Data: contact_id, from_user, message_text, message_type(0,1),  to_user |
| new_message_received | When a new message is received, this will be emitted from server                                                                                  | Receive Data: Same format as get messages API                               |
| new_message_sent     | A confirmation from server that your message has been sent. Use it to indicate to the user that the message has been received by the other user   | Receive Data: Same as get Messages API                                      |
| typing               | When a user is typing this message will be emitted from server. Client must also emit the same message when the user is typing                    | Receive Data: from_user, to_user Send Data: from_user, to_user              |
| typing_stop          | When a user stops typing this will be emitted from client and server.                                                                             | Receive Data: from_user, to_userSend Data: from_user, to_user               |
| contact_deleted      | this should be emited from client side after deleting user from chat contact and same event will be received by the to_user id                    | Send Data: to_user, contact_id Receive Data: to_user, contact_id            |
| user_blocked         | this event has to be emit when a user is blocking someone and the other user id (to_user) will receive the event message                          | Send Data: blocked_user_id Receive Data: to_user                            |
| user_offline         | emitted from server when a user goes offline                                                                                                      | Receive Data: user_id                                                       |


# Push Notifications

## Register a Device

*api/notifications/push/register-device*

** URL Parameters **

1. user_id, access_token
2. device_id (optional)
3. device_token => Required

** Success Response **

``` javascript

{
"status": "success"
"success_type": "USER_DEVICE_REGISTERED"
"success_text": "User device registered successfully."
}

```

** Error Response **

```

{
"status": "error"
"error_type": "DEVICE_TOKEN_INVALID"
"error_text": "Device token required"
}

```

---
sidebar_position: 1
---

# Authentication

Before you proceed with this tutorial, please ensure you follow this steps.

## **Step 1 - sign up**

- Open a new HTTP request on your preferred api testing platform

<!-- ![Create request](../../static/img/createpost.png) -->

- Select the type of request method - in this case, we will be using post method

<!-- ![Method](../../static/img/methodpost.png) -->

- Add this as your api endpoint `https://api.timbu.com/v2/auth/signup`

<!-- ![Raw field](../../static/img/rawpost.png) -->

<!-- Hope you are all good with the above setup? If not please go back and take your time. -->

<!-- #### The final version should look like this. -->

<!-- ![Json](../../static/img/jsonpost.png) -->

Remember to choose json as content type for the request body.

> **Note** - when sending the request in your application, the request body should be an object.

Next up, design the request body data in this format :point_down:

```
{
"email": "te@gmail.com",
"first_name": "tes",
"last_name": "tes",
"password": "pass199",
"phone_country_code": "+234",
"phone_number": "070348255"
}
```

> ##### Note - There are all in json format.

So click on send button to sign up. Your success response will come in this format:point_down:

```
{
    "data": {
        "email": "te@gmail.com",
        "id": "55f32599549e48d9ad12b3c082012ad1",
        "first_name": "tes",
        "last_name": "tes",
        "phone_number": "070348255",
        "is_active": true,
        "has_password": true,
        "is_verified": true,
        "is_superuser": false,
        "org_user": [],
        "country_code": null,
        "image_url": null,
        "is_deleted": true,
        "device_id": null,
        "country": null,
        "state": null,
        "google_id": null,
        "google_image_url": null,
        "date_created": "2023-08-29T08:30:42",
        "last_updated": "2023-08-29T08:30:42"
    },
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiNTVmMzI1OTk1NDllNDhkOWFkMTJiM2MwODIwMTJhZDEiLCJleHAiOjE2OTMyOTg3NDJ9.fvCDgF4GVsbCIyEZQenMA6NaDbw7-LS9dukBlRvrOAE",
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiNTVmMzI1OTk1NDllNDhkOWFkMTJiM2MwODIwMTJhZDEiLCJleHAiOjE3MDg4NDk4NDN9.le4vUwzU_Plfyqs7pkQYNnh7TJeP5PaQzUHGMUeez_s"
}

```

If you successfully get to this stage, congratulation:dancer: on the first step. Continue to step 2.

## **Step 2 - login**

After the sign up process, make a post request to `https://api.timbu.com/v2/auth/login` with the newly created user's email and password. Just like this :point_down:

```
{
"email": "te@gmail.com",
"password": "pass199"

}

```

Same json format as step 1. This :point_down: will be the success response.

```
{
    "data": {
        "email": "te@gmail.com",
        "id": "55f32599549e48d9ad12b3c082012ad1",
        "first_name": "tes",
        "last_name": "tes",
        "is_deleted": true,
        "is_active": true,
        "is_superuser": false,
        "is_verified": true,
        "has_password": true,
        "phone_number": "070348255",
        "phone_country_code": "+234",
        "image_url": null,
        "device_id": null,
        "google_id": null,
        "google_image_url": null
    },
    "access_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiNTVmMzI1OTk1NDllNDhkOWFkMTJiM2MwODIwMTJhZDEiLCJleHAiOjE2OTMyOTg4NjZ9.5gVMOOtyNOzyK98dtcyugLutKf9tQX3knL4D5MqsGt8",
    "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoiNTVmMzI1OTk1NDllNDhkOWFkMTJiM2MwODIwMTJhZDEiLCJleHAiOjE3MDg4NDk5NjZ9.b8qorG-q0G0QzP1PFFuvx3Ki4kYQBhJKBExHx9NzyBw"
}

```

Congratulation!!! you have successfully created an authentication flow for your application.

## Error

If by any chance you could not get this to work due to error encounter, do this:point_down:

- Check that the api url is correct
- Confirm you selected the correct HTTP method for the request
- Ensure that you have select json as the content type

And pay attention to the values inside **loc** array to know the missing value.

```
{
    "detail": [
        {
            "loc": [
                "body",
                "email"
            ],
            "msg": "field required",
            "type": "value_error.missing"
        }
    ]
}

```

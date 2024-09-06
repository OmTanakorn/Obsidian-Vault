*How to setting field on setting page by tool*
*& How to get CustomField on Document or WorkOrder*

## On Setting Page
#### GET
	API For get all of Custom Field and Default field for setting required or 
	not on tool (RFI - 0, Submittal - 1, Inspaction - 2, WorkOrder - 3)

-**endpoint**: `/api/v1/custom-field/setting`

-**Query Params**

| Key       | Value |
| --------- | ----- |
| project * | int   |
| tool *    | int   |
**detile**
	tool param up to tool_label (6, 7, 8, 9)
	One setting one project 
***Ex***
```cURL
curl --location 'http://localhost:8888/api/v1/custom-field/setting/?project=1&tool=7' \
--header 'x-company: 8af3a36a-1284-48f9-90f6-5a7697128741' \
--header 'Authorization: Bearer xM8ZgNqlEyXPbJmPKouAqhP3IBRYPl' \
--header 'Cookie: sessionid=g62k6uic4qkd3f35v32ebmrwwr066oxo'
```

**Response**
`HTTP_200_OK `

```json
[
   {
      "id":15547,
      "title":"Discipline",
      "key":"discipline",
      "type":4,
      "is_required":true,
      "is_editable":false,
      "field_type":1
   }, 
   %% OtherField %%
   {
      "id":7,
      "title":"Com Name",
      "key":"com_name",
      "type":0,
      "is_required":null,
      "is_editable":true,
      "is_select":false,
      "field_type":2
   },
   {
      "id":8,
      "title":"Number Component",
      "key":"number_component",
      "type":1,
      "is_required":true,
      "is_editable":true,
      "is_select":true,
      "field_type":2
   }
]
```

***form data it mean***
	in tool 7 have Default `id:15547 Discipline and more` and have CustomField  
	`id: 7 com_name` is not ***select*** and `id:8 number_compnent` is ***select*** 
	so if u need to edit `is_required` or `add CustomField`to **Document** just trow it to Put API I'll show your next
_________
#### PUT
**-endpoint:** `/api/v1/custom-field/update-setting/`
**-Query Params**

| key     | value |
| ------- | ----- |
| project | int   |
| tool    | int   |

**payload**
```json
{
   "default_fields":[
      {
         "id":15548,
         "is_required":false
      }
   ],
   "custom_fields":[
      {
         "id":8,
         "is_required":true
      }
   ]
}
```

> [!warning] Warning
> if on custom field you deleted some id it mean you deleted this field on tool like a u have `id:8` and u put payload not have `id:8` field `id:8` will deleted on this tool 
> But don't worry if u need it back just add it to "custom_fields" it will restore field back


**EX.**
```
curl
curl --location --request PUT 'http://localhost:8888/api/v1/custom-field/update-setting/?project=1&tool=7' \
--header 'x-company: 8af3a36a-1284-48f9-90f6-5a7697128741' \
--header 'Content-Type: application/json' \
--header 'Authorization: Bearer xM8ZgNqlEyXPbJmPKouAqhP3IBRYPl' \
--header 'Cookie: sessionid=g62k6uic4qkd3f35v32ebmrwwr066oxo' \
--data '{
    "default_fields": [
        {
            "id": 15548,
            "is_required": false
        }
    ],
    "custom_fields": [
        {
            "id": 8,
            "is_required": true
        }
    ]
}'
```

**Response**
`HPPT_200_OK`
```Json
{
	"message": "Updated successfully"
}
```

--------
> so now u can edit a setting field on tool.
> and this one you need to know when u call document field setting

#### GET 
**-endpoint** `api/v1/custom-field/ative/`
**-Query Params

| key     | value |
| ------- | ----- |
| project | int   |
| tool    | int   |
**EX.**
```curl
curl --location 'http://localhost:8888/api/v1/custom-field/active/?project=1&tool=7' \
--header 'x-company: 8af3a36a-1284-48f9-90f6-5a7697128741' \
--header 'Authorization: Bearer xM8ZgNqlEyXPbJmPKouAqhP3IBRYPl' \
--header 'Cookie: sessionid=g62k6uic4qkd3f35v32ebmrwwr066oxo'
```

**Response**
`HTTP_200_OK`

```Json
[
   {
      "id":8,
      "title":"Number Component",
      "key":"number_component",
      "type":1,
      "setting":{ },
      "is_required":true,
      "is_editable":true,
      "field_type":2
   }
]
```


This API will show you all Custom Field on Tool (document , work order)
you can `post` on create Document add 
```json
"custom_fields":[
   {
      "tool_custom":8,
      "values":100
   }
]
```

and update is same
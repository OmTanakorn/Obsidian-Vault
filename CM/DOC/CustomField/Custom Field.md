Enjoy kup 😢 

##### UX/UI
- Figma : [LINK](https://www.figma.com/design/YN9UUdxoHgp7KdVCpoO5ga/CM-Sitearound--%5B-Improve-Design-%5D?node-id=5990-19108&t=4dgKuzt7cLbapPJm-0)
# Custom Field CRUD
## GET
-**endpoint**: `/api/v1/custom-field/`
-**Query Params**

| Key     | Value |
| ------- | ----- |
| project | int   |
**EX.**

```cURL
curl --location 'http://localhost:8888/api/v1/custom-field/?tool=7&project=1' \
--header 'x-company: 8af3a36a-1284-48f9-90f6-5a7697128741' \
--header 'Cookie: sessionid=g62k6uic4qkd3f35v32ebmrwwr066oxo'
```

**Response**
```JSON
{
   "count":5,
   "results":[
      {
         "id":5,
         "title":"Drop Down",
         "key":"drop_down",
         "type":4,
         "setting":{
            "choice":{
               "0":"A",
               "1":"B",
               "2":"C"
            }
         },
         "updated_by":{
            "id":1,
            "full_name":"Superioradmin Sitearound"
         },
         "updated_at":"2024-08-19T10:32:42.879054Z"
      },
      {
         "id":4,
         "title":"Currency",
         "key":"currency",
         "type":3,
         "setting":{
            
         },
         "updated_by":{
            "id":1,
            "full_name":"Superioradmin Sitearound"
         },
         "updated_at":"2024-08-19T10:25:36.603195Z"
      },
      {
         "id":3,
         "title":"Date",
         "key":"date",
         "type":2,
         "setting":{
            
         },
         "updated_by":{
            "id":1,
            "full_name":"Superioradmin Sitearound"
         },
         "updated_at":"2024-08-19T10:30:03.369646Z"
      },
      {
         "id":2,
         "title":"Number",
         "key":"number",
         "type":1,
         "setting":{
            
         },
         "updated_by":{
            "id":1,
            "full_name":"Superioradmin Sitearound"
         },
         "updated_at":"2024-08-19T10:30:09.230938Z"
      },
      {
         "id":1,
         "title":"Text",
         "key":"text",
         "type":0,
         "setting":{
            
         },
         "updated_by":{
            "id":1,
            "full_name":"Superioradmin Sitearound"
         },
         "updated_at":"2024-08-19T10:30:16.978002Z"
      }
   ]
}
```
________________________________

| ID  | Title  |  Key   | Type |        Updated By        |         Updated At          |
| :-: | :----: | :----: | :--: | :----------------------: | :-------------------------: |
|  1  |  Text  |  text  |  0   | Superioradmin Sitearound | 2024-08-19T10:30:16.978002Z |
|  2  | Number | number |  1   | Superioradmin Sitearound | 2024-08-19T10:30:09.230938Z |

## POST
-**endpoint**: `/api/v1/custom-field/`
-**Query Params**

| Key     | Value |
| ------- | ----- |
| project | int   |
**EX.**
```cURL
curl --location 'http://localhost:8888/api/v1/custom-field/?project=1' \
--header 'x-company: 8af3a36a-1284-48f9-90f6-5a7697128741' \
--header 'Content-Type: application/json' \
--header 'Cookie: sessionid=g62k6uic4qkd3f35v32ebmrwwr066oxo' \
--data '{
    "title": "Number Component",
    "key": "number_component",
    "type": 1
}'
```

**Response**
`HTTP_201_CREATE `

```JSON
{
   "id":8,
   "title":"Number Component",
   "key":"number_component",
   "type":1,
   "setting":{
      
   },
   "updated_by":{
      "id":1,
      "full_name":"Superioradmin Sitearound"
   },
   "updated_at":"2024-08-22T09:12:48.165230Z"
}
```

NOW U Can go next [[Field Setting]]
BUT IF U WAN TO KNOW MORE 
## PATCH


## DEL

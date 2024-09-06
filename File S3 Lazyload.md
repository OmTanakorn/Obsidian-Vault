## About Payload
What best payload ? 
#### payload

> [!NOTE]
> let fontend send id and model too backend and backend have job to query it and make payload by other key fontend need like a Order id work_order

**Request V1**
```JSON
{
	"tool": 'work_order',
	"files":[
	{
		"id":[1, 2, 3, 4, 5, 6],
		"model":"BeforeFile"
	},
	{
		"id":[1, 2, 3, 4, 5, 6],
		"model":"after_file"
	}
	],
	"other choice"
}
```

**Request V2**
```JSON
{
	"tool":"work_order",
	"id":[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
}
```

**Request V3**
```JSON
[
	{
		"id":[1,2,3,4,5],
		"model":"before"
	}
]
```

File = Before_file.objects.filter(id__in=id).group_by('work_order')
#### response
FILE
```JSON
{
    "id": 14,
    "uuid": "efb43dfe-cd4f-40d0-a17d-b0fb89fe002c",
    "title": "tray_large.webp",
    "path": "project/c4fc46f8-6c54-4984-ac5c-43bcc81d1a19/....",
    "url": "https://daqyof94odjgl.cloudfront.net/media/project/...",
    "type": "image/webp",
    "thumbnail": null,
    "markup": null,
    "form": null
  }
```
**Response V1**
```JSON
[
	{
		"id": 1,
		"before":[{file}]
	},
	{
		"id":2,
		"before":[{file}],
		"after":[{file}]
	}
]
```
**Response V2**
```JSON
{
	1:{
		"before":[
			{file},
			{file}
			],
		"after":[
			{file},
			{file}
			]
	},
	2:{
		"before":[
			{file},
			{file}
			],
		"after":[
			{file},
			{file}
			]
	}
}
```
**Response V3**
```JSON
{
	"before":{
		"1":{file},
		"2":{file},
	}
}
OR 
{
	"before":[LIST ALL FILE],
	"after":[LIST ALL FILE]
	
}

```
Response V4
```JSON
{

	"before_file":{
		1:{ "id": 1,
			"uuid": "958cca06-bd74-4e91-a583-758179716afe",
			"title": "พยามกครง.jpg",
			"path": "project/c4fc46f8-6c54-4984-ac5c...",
			"url": "https://daqyof94odjgl.cloudfront.net/med...",
			"type": "",
			"thumbnail": "https://daqyof94odjgl.cloudfront.net...o",
			"markup": null,
			"form": null 
			},
		2:{"id":2,
			...,
			},
	},
	"after_file": {
		1:{
		"id": 1,
		"uuid": "18ba4b82-1aa1-4d4e-af65-9fcf51416fae",
		"title": "received_470250798804455.png",
		"path": "project/c4fc46f8-6...55.png",	
		"url": "https://daqyof94odjgl.cloudfront.net/med...j",
		"type": "",
		"thumbnail": "https://daqyof94odjgl.cloudfront.net/medi..",
		"markup": null,
		"form": null
		}
	}
}
```
### Make Middenwars for File On S3
#### To do Flow
[o]get rady `MODEL_S3_FILE` for every model
[o]payload -> get data
	id    | list |
	model | name |
[o]get `id` for filter
[o]get `model` for queryset
[ ]filter `id__in` list `id`
[ ]return `Data`

> [!warning]
> But Data is not like this. We need to make a new data before send data to Fontend

def data(self)
```flow
for q in queryset:
	file = send q it to FileSilializer 
	add = file append with WorkOrder id (calling Group_BY)
#HAVE LIST NOW SEND IT TO DATA
```

EX.
```JSON
MODEL_S3_FILE = {
	'before_file':{
		'app':'work_order',
		'model':'WorkOrderBeforeFile'
		},
	'after_file':{
		'app':'work_order',
		'model':'WorkOrderAfterFile'
		}
	
}
```

```python
class BaseLoadFile():
	#create Filter file for any model fontend send and to repesend like order 
	s = siliailzer.
```

#### HOW TO GROUP BY

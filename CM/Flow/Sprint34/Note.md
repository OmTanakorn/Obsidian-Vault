	day of work: 1 week
### JOB
- Feature/ Support-ticket
- Fix bug

### Support-Ticket
###### requirement
```markdown
**Description**
1. User input subject (Required) 
2. User select type ; (Required)  
    - Question  
    - Problem  
    - Feature Request  
    - Other
3. User describe the ticket (Optional)
4. User attached file (Optional)

**Additional Condition**
 1. Submit button will be disable if required information is not address.
 2. After submit a ticket, system must check that all information is successfully transit or the error dialogue will be display.
    **Submit Ticket Failed**
    We encountered an issue while submitting this ticket. Please try again later.
```

###### Model
- Support Ticket
	- subject
	- type
- Support Ticket File (m)
	- file
- Support Ticket Message (m)
	- message
	- staff read
	- requester read
- Support Ticket Message File (m)
	- file

**File Path**
- /support-ticket/{support.uuid}/
- /support-ticket/{support.uuid}/support-message/{file.uuid/


**payload message**
```JSON
message
{
[
	{
		"message": "Hi i have somthing to ask. Do you love a cat? ",
		"file":[
			{
			"id": 1,
            "uuid": "3d05512e-c841-4d6a-83c9-ac04725c0b35",
            "title": "guanyou.jpeg",
            "path": "project/c4fc.../guanyou.jpeg",
            "url": "https://daqyof94odjgl.cloudfront.net/...u.jpeg",
            "type": "image/jpeg",
            "thumbnail": "https://daqyof94odjgl.cloudfront.net/...u",
            "markup": null,
            "form": null
	        },
	        {
			"id": 2,
            "uuid": "3d05512e-c841-4d6a-83c9-ac04725c0b35",
            "title": "guanyou.jpeg",
            "path": "project/c4fc.../guanyou.jpeg",
            "url": "https://daqyof94odjgl.cloudfront.net/...u.jpeg",
            "type": "image/jpeg",
            "thumbnail": "https://daqyof94odjgl.cloudfront.net/...u",
            "markup": null,
            "form": null
	        }
	    ]
	},
	{
		"message": "I don't love cat.",
		"file":[]
	}
	
]
}
```

File 
```JSON
"file":[
			{
			"id": 1,
            "uuid": "3d05512e-c841-4d6a-83c9-ac04725c0b35",
            "title": "guanyou.jpeg",
            "path": "project/c4fc.../guanyou.jpeg",
            "url": "https://daqyof94odjgl.cloudfront.net/...u.jpeg",
            "type": "image/jpeg",
            "thumbnail": "https://daqyof94odjgl.cloudfront.net/...u",
            "markup": null,
            "form": null
	        },
	        {
			"id": 2,
            "uuid": "3d05512e-c841-4d6a-83c9-ac04725c0b35",
            "title": "guanyou.jpeg",
            "path": "project/c4fc.../guanyou.jpeg",
            "url": "https://daqyof94odjgl.cloudfront.net/...u.jpeg",
            "type": "image/jpeg",
            "thumbnail": "https://daqyof94odjgl.cloudfront.net/...u",
            "markup": null,
            "form": null
	        }
    ],
```
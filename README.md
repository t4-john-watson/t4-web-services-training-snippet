# TERMINALFOUR Web Services Training Snippets
This file contains plaintext snippets of content used in the Web Services API Training Course. Content can be copied from here with no formatting.
## Postman activities
### Create a new Section
~~~
{
   "name": "my new section",
   "parent": x
}
~~~

### Mirror a Section
~~~
{
   "destination": x,
   "content": "MIRROR"
}
~~~

### List all child sections of a Section
~~~
{
   "read": {
      "section": {
 	  "id": x
      },
      "activeNode": x,
      "openNodes": [x],
      "expandCollapseAllChildren": true
   }
}
~~~

### Create a Contenttype
~~~
{
	"name": "elementsTest",
	"type": 10,
	"contentTypeElements": [
		{
			"name": "Name",
			"type": 1,
			"maxSize": 80
		}
	]
}
~~~
~~~
{
	"name": "content",
	"type": 3,
	"maxSize": 200
}
~~~

### Update a Contenttype
~~~
{
    "name": "Creator",
    "type": 7,
    "maxSize": 80,
    "listId": x
}
~~~

### Create Content
~~~
{
    "contentTypeID": x,
    "language": "en",
    "elements": {
        "Content#": "<p>Some HTML Content</p>",
        "Name#": "TestName"
    }
}
~~~
~~~
{
   "contentIds": [7,8,9]
}
~~~

## node.js Activities




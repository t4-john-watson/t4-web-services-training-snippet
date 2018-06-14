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

### Mirror content to a branch recursively
~~~
const getSections = require("./lib/utilities/get_sections");
~~~
~~~
function executeRequests(options) { 
	getSections(1, options)
		.then( sections => mirrorContentToSections(sections, 242, 12, options, logMessage) 
	); 
}
~~~
~~~
function mirrorContentToSections(sections, source, contentId, options, callback) {
	options.method = "LINK";
	options.path = `${options.pathPrefix}content`;
	sections.forEach((section) => {
		var postData = {
			"source": source,
			"destination":section.id,
			"contents":{
				[contentId]:[] 
			}
		} 
		postData = JSON.stringify(postData);
		options['headers']['Content-Type'] = "Application/json";
		options['headers']['Content-Length'] = Buffer.byteLength(postData);
		Req(options, postData)
			.then(response => callback(response, `mirrored into section ${section.id}`))
			.catch(error => console.log(error));
	});
}
~~~
~~~
function executeRequests(options) {
	getSections(1, options)
		.then(
		   sections => mirrorContentToSections(sections, 242, 12, options, logMessage)
		);
}
~~~

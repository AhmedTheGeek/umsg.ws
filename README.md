# umsg.ws
The way to simplified/extendable standard and unified WebSocket Message Structure.

## _msg.ws

umsg.ws or (underscore)msg.ws is a try to standardize the WebSocket message structure, so we can write tools and libraries that can deal with standard style/structure of a message.

The idea started when I was trying to write a library that can deal with and extend the functionality of normal JS WebSocket object, then I noticed that not everybody is going to to use my message structure, and so my library will not work in all cases, actually won't work at all but my case.

## It's JSON

**_msg.ws** Is JSON object, that way we can customize it and extend it and even parse it and use it on almost any platform. And it would be structured and organized.

## The Basic Form

```
{
	messageType: "epicType",
	_msg:{
		//The Awesome Stuff
	}
}
```

### Message Typing

The message has to be typed since I need to understand what kind of content I'm receiving and what am I supposed to do with it.

For that, we need to provide a **messageType** property on the root object of our message JSON object.

Message Typing will be the core of **_msg.ws** and it will be very important for the extensibility of the structure.


### The _msg

Is the message's main object, It will hold all custom properties and content.

Inside the **_msg** property we will have some mandatory properties and the others will be optional or customizable.

### Content Typing

Previously we talked about **Message Typing** but what about the content of the message, we might have text, audio or video or any other type of content, the receiver gotta get a clue on what they're dealing with, so it's mandatory to provide the mime type of the content as follows:

```
{
	messageType: "epicType",
	_msg:{
		contentType: "text/plain",
		content: "Amazing Things Here, Aa?"
	}
}

```

The example above shows that the sent content is plain text, and it's a mime type so you can understand that on any platform I can think of.

The content type can be provided as a mime type put inside the **contentType** property in the **_msg** object.

### The Content

The content can be anything as long as the type of it matches the **contentType** mime.

So you can put anything from plain text to a binary byte array of a video.

And the content is provided by the **content** property inside the **_msg** object.

### Content Attachments

Sometimes we need to attach another type of contents into the same message as the original content, for example, an image attached to a text message.

To do that we provide the text message inside the main **content** property. The extend the **_msg** object and add new object to it called **attachments**

```
{
	messageType: "epicType",
	_msg:{
		contentType: "text/plain",
		content: "Amazing Things Here, Aa?",
		attachments:{
		  contentType: "image/png",
		  content: "iVBORw0KGgoAAAANSUhEUgAAAPoAAAD6CAIAAAAHjs1qAAAACXBIWXMAAAsTAAALEwEAmpwY..."
		}
	}
}
```

As we can see in the example above, now we have an attachment object that contains **contentType** and **content** properties, and typing rules apply for them as they apply to the main **content** and **contentType**, so they have to match each other.



#To Be Continued
#Contributions are very welcome

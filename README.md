# Week-1-intermediate-javascript

Day 1

PopUps
popups are what we use to show additional documents of a web page to the user.so you run a document inside another document without closing the initial documents
Also, popups are tricky on mobile devices, that don’t show multiple windows simultaneously.
Popups can be blocked if they do not have an event that actually triggers the popup to load. for example:
window.open('https/...') might be blocked and 
button. onclick{
window.open = () => ('https/...')
}
will not be blocked.

Window.open
The syntax to open a popup is: window.open(url, name, params)
params is the sizing of the window.
there are window features where you can use to display or hide things like menubar:
all you have to do is write the window feature then you assign it to yes or no.

minimalising windows
you can minimalize the window to certain height, width and also the position by there are minimum numbers for that.
Accessing pop up from window
you can access the pop up window by using the window.open() inside the brackets you have the url, name and size of the pop up, all classed or separated by the comma and there will be no spaces. you can add text of the new window by using the window.document.write()

closing a popup
to close a popup you use the win.close()
to check if the window is closed you use the win.closed.

Scrolling and resizing
there are resizing events as well as scrolling
examples:
moveBy(x,y) which is when you specify the coordinates to be used to move the window
moveTo(x,y) which is when you specify the coordinates the window should move to
resizeBy(weight,height) is used when you want to increase or decrease a certain window by the given
resizeTo(width,height) is used resize the given window by the given size

Scrolling a window
the scroll event has many other events such as scrollBy() where you mention the interval to be used by the scroll, scrollTo() which you specify the coordinates. scrollIntoView() where you specify the position or angle to be shown
Focus/blur on a window
The onblur is actually used to perform a task when the window or certain element is blur in a web page or when the user moves to a different window or element.

DAY 2

Same origin
Two URLs are said to have the “same origin” if they have the same protocol, domain, and port.
These URLs all share the same origin:
http://site.com
http://site.com/
http://site.com/my/page.html which is site.
These ones do not:
http://www.site.com (another domain: www.matters)
http://site.org (another domain: .orgmatters)
https://site.com (another protocol: https)
http://site.com:8080 (another port: 8080)

In Action:iframe
An <iframe> tag hosts a separate embedded window, with its own separate document and window objects.
We can access them using properties:

iframe.contentWindow to get the window inside the <iframe>.
iframe.contentDocument to get the document inside the <iframe>,

Windows on subdomains: document.domain
By definition, two URLs with different domains have different origins
if windows share the same second level domain the browser can ignore the rest so they can be treated as if they have the same origin

Iframe: wrong document pitfall
if an iframe has the same origin, and we can access its document, there’s a pitfall. It’s not related to cross-domain things, but important to know. Upon its creation, an iframe immediately has a document. But that document is different from the one that loads into it!
So if we do something with the document immediately, that will probably be lost.
We shouldn’t work with the document of a not-yet-loaded iframe, because that’s the wrong document. If we set any event handlers on it, they will be ignored.

Collection: window.frames
when you have multiple winow.frames you can get it by using the name collection.frames:
By number: window.frames[0] – the window object for the first frame in the document.
By name: window.frames.iframeName 
and if an iframe has other iframes inside it you can use the windows.frames.parent

The “sandbox” iframe attribute
The purpose of the "sandbox" attribute is only to add more restrictions. It cannot remove them. In particular, it can’t relax same-origin restrictions if the iframe comes from another origin.

Cross Window Messaging
Cross-window messaging, also known as postMessage, is a JavaScript feature that allows different windows or iframes to communicate with each other securely, even if they originate from different origins.
Cross-window messaging, also known as postMessage, is a JavaScript feature that allows different windows or iframes to communicate with each other securely, even if they originate from different origins

Introduction to Clickjacking
people normally use click jacking in a way that they have buttons that they show to users, giving the user certain impressions by the message they see on the button whereas they mean a lot on the background, having an iframe that will perform malicious things on the website

Old school defenses (weak)
there are ways to block clickjacking, like forbidding an a page of an iframe.
That is: if the window finds out that it’s not on top, then it automatically makes itself the top.
Blocking top-navigation
We can block the transition caused by changing top.location in beforeunload event handler.
theres is a sandbox attribute which is used to restrict things such as navigation.

X-Frame-Options
The server-side header X-Frame-Options can permit or forbid displaying the page inside a frame.
It must be sent exactly as HTTP-header else it wont do anything
DENY
Never ever show the page inside a frame.
SAMEORIGIN
Allow inside a frame if the parent document comes from the same origin.
ALLOW-FROM domain
Allow inside a frame if the parent document is from the given domain.
Showing with disabled functionality
this has a small disadvantage to other sites as they will not get a chance to perform tasks even if they have good intentions

Samesite cookie attribute
In JavaScript, cookies are small pieces of data stored in a user's browser. They are commonly used to store user preferences, session information, and other data that needs to be remembered between browser sessions.

Clickjacking
Clickjacking is a type of cyber attack where a malicious website tricks a user into clicking on something different from what the user perceives. This is usually done by overlaying invisible elements or misleading buttons on top of legitimate content or by placing legitimate content inside a frame on a malicious website. The goal of clickjacking is to deceive users into performing actions without their knowledge or consent, such as clicking on buttons, links, or interactive elements.
Here's how clickjacking works:
Deceptive Design: The attacker designs a malicious web page with hidden elements or overlays that are placed over legitimate content.
User Interaction: The user visits the malicious website, thinking they are interacting with the visible content. However, their interactions are actually happening with the hidden or overlaid elements.
Unintended Actions: Users unwittingly perform actions on the malicious site, such as clicking on buttons or links, without realizing they are interacting with the hidden elements.
Clickjacking can be used for various malicious purposes, including:
Phishing: Trick users into clicking on elements that lead to phishing websites, where sensitive information like login credentials is stolen.
Malware Installation: Trick users into downloading malicious software or granting permissions for malicious actions.
Social Engineering: Deceive users into liking, sharing, or following social media pages without their knowledge, spreading malicious content.
Ad Fraud: Generate fraudulent ad clicks without the user's consent, generating revenue for the attacker.

Example of Clickjacking:
Imagine you receive an email with a link that appears to lead to an interesting video on a social media site. When you click the link, you're taken to a webpage where you see what appears to be a video player with a play button. You click the play button, but unknowingly, the play button is actually an invisible element overlaid on top of a "Like" button of a social media site.
Without your knowledge, you've just liked a malicious page or shared it on your social media profile. This action might then appear on your friends' feeds, spreading the malicious link further. In this scenario, you've been clickjacked into interacting with the webpage in a way that you didn't intend to, and the attacker achieves their goal, whether it's spreading malware, phishing for information, or other malicious activities.

DAY 3
ArrayBuffer
An ArrayBuffer is a type of data structure used in JavaScript that represents a fixed-length buffer of binary data. It is primarily used in low-level operations that require direct access to memory, such as graphics and network protocols. An ArrayBuffer can be used to store data of various types, including integers, floats, and bytes.
One of the main advantages of using an ArrayBuffer is its efficient memory management. Because it is a fixed-length buffer, it can allocate memory more efficiently than a dynamically-sized data structure. Additionally, because it can store data of multiple types, it can be faster than having to create and manage separate data structures for each type of data.
To use an ArrayBuffer in JavaScript, you typically create a new instance of the ArrayBuffer class with a specific length, and then you can access and modify the data stored in the buffer using typed arrays or other data views. Because of its low-level nature, working with ArrayBuffers and typed arrays requires a certain level of programming skill, but it can be a powerful tool for optimizing performance in certain types of applications.

TypedArray
TypedArrays are a set of objects provided by the JavaScript language for storing and manipulating binary data in a structured and controlled way. They are part of the TypedArray interface, which includes classes such as Int8Array, UInt16Array, and Float32Array.
A TypedArray is essentially a wrapper around an ArrayBuffer object, which represents a segment of contiguous memory for storing binary data. The difference between a TypedArray and a normal array is that a TypedArray only allows you to store elements of a particular type, whereas normal arrays can store elements of any type.

dataview in javascript
Delete
Dataview is an object in JavaScript that provides a low-level interface for reading and writing binary data in a typed array. It allows developers to directly manipulate binary data stored in an ArrayBuffer object.
Dataview provides methods to read and write different types of numerical data (integers, floats, etc.) with specific byte order and alignment. It also provides methods to access data at specific positions in the buffer.
Example usage of DataView:
```
// create an ArrayBuffer object with 16 bytes of data
const buffer = new ArrayBuffer(16);
// create a DataView object with the buffer
const view = new DataView(buffer);
// set a 32-bit integer value at the second position in the buffer
view.setInt32(4, 1234);
// read the previously set value
const val = view.getInt32(4);
console.log(val); // output: 1234
```
Note that DataView should be used when working with binary data that has a known structure. For more complex data structures, it is recommended to use higher-level data parsing libraries such as ProtoBuf or MsgPack.
Copy
Delete
typedarray methods
Delete
TypedArray is a global object in JavaScript that provides an array-like interface for working with binary data. It represents a specific view into an underlying binary data buffer, and allows direct manipulation of its contents.
Here are some commonly used TypedArray methods:
1. `TypedArray.set()` - Copies elements from a source TypedArray or array-like object into a TypedArray.
Example Usage:
```
const arr = new Uint8Array([1, 2, 3]);
const buffer = new ArrayBuffer(3);
const typedArray = new Uint8Array(buffer);
typedArray.set(arr);
console.log(typedArray);
// Output: Uint8Array [1, 2, 3]
```
2. `TypedArray.subarray()` - Returns a new TypedArray that is a subarray of the original TypedArray.
Example Usage:
```
const typedArray1 = new Uint16Array(4);
typedArray1.set([1, 2, 3, 4]);
const typedArray2 = typedArray1.subarray(1, 3);
console.log(typedArray2);
// Output: Uint16Array [2, 3]
```
3. `TypedArray.slice()` - Returns a new TypedArray that is a shallow copy of the original TypedArray.
Example Usage:
```
const typedArray1 = new Int8Array([1, 2, 3, 4]);
const typedArray2 = typedArray1.slice(1, 3);
console.log(typedArray2);
// Output: Int8Array [2, 3]
```
4. `TypedArray.reverse()` - Reverses the order of the elements in the TypedArray.
Example Usage:
```
const typedArray = new Float32Array([1.0, 2.0, 3.0]);
typedArray.reverse();
console.log(typedArray);
// Output: Float32Array [3.0, 2.0, 1.0]
```
5. `TypedArray.sort()` - Sorts the elements of the TypedArray in place.
Example Usage:
```
const typedArray = new Int16Array([1, 3, 2]);
typedArray.sort((a, b) => a - b);
console.log(typedArray);
// Output: Int16Array [1, 2, 3]
```
These are just a few examples of the many TypedArray methods available for working with binary data in JavaScript.
Copy
Delete
typedarrays
Delete
TypedArrays are a set of objects provided by the JavaScript language for storing and manipulating binary data in a structured and controlled way. They are part of the TypedArray interface, which includes classes such as Int8Array, UInt16Array, and Float32Array.
A TypedArray is essentially a wrapper around an ArrayBuffer object, which represents a segment of contiguous memory for storing binary data. The difference between a TypedArray and a normal array is that a TypedArray only allows you to store elements of a particular type, whereas normal arrays can store elements of any type.
Here are some common TypedArray classes and their uses:
1. `Int8Array`, `Uint8Array`, `Uint8ClampedArray` - Used for storing 8-bit integers.
2. `Int16Array`, `Uint16Array` - Used for storing 16-bit integers.
3. `Int32Array`, `Uint32Array` - Used for storing 32-bit integers.
4. `Float32Array`, `Float64Array` - Used for storing 32-bit and 64-bit floating point numbers.
TypedArrays can be initialized with an ArrayBuffer object, which can be created directly using the `new ArrayBuffer()` constructor. Once an ArrayBuffer has been created, you can use one of the TypedArray constructors to create a new TypedArray that points to a subset of the binary data.
Example usage:
const buffer = new ArrayBuffer(16);
const uint32 = new Uint32Array(buffer);
const int16 = new Int16Array(buffer);
uint32[0] = 0x01234567;
int16[2] = 0x1234;
console.log(uint32); // Uint32Array [19088743, 0, 0, 0]
console.log(int16); // Int16Array [99, 71, 4660, 0, 0, 0, 0, 0]
out of bound values in typed arrays
Out of bound values in TypedArrays are values that attempt to access a position that does not exist within the memory allocated for the array. This can occur in a number of ways, such as:
1. Trying to store a value that is too large or too small in a TypedArray, for example trying to store a value of 256 in an Int8Array, which only has a range from -128 to +127
2. Trying to access an index that is outside the bounds of the TypedArray, for example trying to access index 10 of a TypedArray that only has 8 elements.
3. Trying to create a TypedArray with a length that is greater than the available memory.

TypedArray methods
TypedArray is a global object in JavaScript that provides an array-like interface for working with binary data. It represents a specific view into an underlying binary data buffer, and allows direct manipulation of its contents.

DataView
Dataview is an object in JavaScript that provides a low-level interface for reading and writing binary data in a typed array. It allows developers to directly manipulate binary data stored in an ArrayBuffer object.
Dataview provides methods to read and write different types of numerical data (integers, floats, etc.) with specific byte order and alignment. It also provides methods to access data at specific positions in the buffer.
 

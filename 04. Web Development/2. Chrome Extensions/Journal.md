Understand the sample extension's js page - k
Event pages - k
Content scripts - k
activeTab permission - k
Content security policy
Cross-Origin XHR
Debugging
Message passing
Native messaging
Options

Messaging
Rehash

********************

Browser action seems to be nothing but a tap on the extension icon.
What though is a page action?

`extensionID` is a unique identifier that the extension system generates for each extension. Every file in an extension is also accessible by an absolute URL which has the extensionID. This id is accessible using @@extension_id predefined message.
```
chrome-extension://<extensionID>/<pathToFile>
```

> What are predefined messages

Extensions can save data using the [storage](https://developer.chrome.com/extensions/storage) API, as well as the HTML5 [web storage](http://dev.w3.org/html5/webstorage/) API (such as localStorage). Need to understand HTML5 better, is it always available, what extra API does it provide.

Its possible for one extension to call another by sending a message. Need to see an example.

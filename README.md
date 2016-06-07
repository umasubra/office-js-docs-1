# Office JavaScript APIs

Welcome to the Office JavaScript API documentation. Here you can find everything you need to about Office add-ins.  To view these documents, we recommend you view them on [dev.office.com](https://dev.office.com/docs/add-ins/overview/office-add-ins).

## Review upcoming feature: Event API in batch syntax

This branch is dedicated to providing an overview of the upcoming **Event APIs using batch API syntax** of Office.Js. 

### Event APIs

_Note: The listed features are still under the design and review phase and are not yet available as part of Office.js. The final design is subject to change. Once the feature is made available, the final specification will be published as part of the regular docs._

* This feature is intended to give the ability for Office JavaScript add-ins to perform event APIs based APIs using the new batch syntax introduced with Office 2016. 
* This will allow add-ins/apps to register listeners (function) based on an object that is bound to the document, receive event arguments to the registered function, un-register listners, unregister all listeners related to a particular event. 
* Two naming options are described below as part of choosing the best one Functionally both options work in the same manner. Let us know which of the option makes best sense to you. 

### Design

#### Adding a listner

```js
// Below line registers a listner (function) named handler on some object that provides some event named sampleChangeEvent. The result of this event registration is returned and stored in eventResult, which can later be used to remove event registration. 
var eventResult  = Object.onSampleChange.subscribe(handler);
...
...

// Event listner function receives an argument object. See the table below for the makeup of the object.
function handler(e) {
...
...
}
```

#### Removing event listner

```js
// Un-register an event handler. 
var eventResult  = Object.onSampleChange.unsubscribe(handler);
// or
eventResult.remove();
```


```js
// Un-register all handlers related to a particular event on an object. 
Object.onDataChangedEvent.unsubscribeAll()
```

### Alternate naming option. 

#### Adding a listner

```js
// Below line registers a listner (function) named handler on some object that provides some event named sampleChangeEvent. The result of this event registration is returned and stored in eventResult, which can later be used to remove event registration. 
var eventResult  = Object.sampleChangeEvent.add(handler);
...
...

// Event listner function receives an argument object. See the table below for the makeup of the object.
function handler(e) {
...
...
}
```

#### Removing event listner

```js
// Un-register an event handler. 
var eventResult  = Object.sampleChangeEvent.add(handler);
// or
eventResult.remove();
```


```js
// Un-register all handlers related to a particular event on an object. 
Object.dataChangedEvent.removeAll()
```


## Callback Value

When the function you passed to the event listner executes, it receives an object that you can access from the listner function's only parameter. The object structure is as below:

|**Property**|Type|**Use to...**|
|:-----|:----|:-----|
|value|String|Value varies depending on the purpose and context of that method. To determine what is returned by the value property for an, refer to the "Callback value" section of the method's topic. Returns  **undefined** because there is no data or object to retrieve when adding an event handler.|
|status|String|Determine the success or failure of the operation.|
|error|Object|Returns an error object that provides error information if the operation fails.|
|context|Object|Access your user-defined object or value, if you passed one as the  parameter.|


**[Tell us what you think](https://github.com/OfficeDev/office-js-docs/issues/new?title=EventApi_BatchSyntax_OpenSpec)**


## Give us your feedback

Your feedback is important to us. 
* Check out the docs and let us know about any questions and issues you find in them by [submitting an issue](https://github.com/OfficeDev/office-js-docs/issues) directly in this repository. Make sure you state the version+build number of the client you are using, and provide repro steps, console output, and error messages in any issue you open.  
* Let us know about your programming experience, what you would like to see in future versions, code samples, etc. Use [this site](http://officespdev.uservoice.com/) for entering your suggestions and ideas.
* If you find an issue with the documentation, please create a GitHub issue by clicking the **Issues** tab above. We also encourage you to fork, make the fix, and do a pull request of your proposed changes.

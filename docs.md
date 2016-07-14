# Quick start
Simpla is a collection of new HTML elements powered by an API. Use them in your code to create editable content.

[download sample template](https://github.com/simplaio/sample-template/archive/master.zip) <!-- {.button} -->

### Setup a project
```comment
Include this snippet in your <head>
```

```html
<script src="https://app.simpla.io"></script>
<script>
  // TODO: Enter project ID
  Simpla('PROJECT-ID');
</script>
```

Login to your [dashboard](https://www.simpla.io/projects) and create a project, then include the Simpla library in your HTML document and call `Simpla()` with your project's ID.

### Use the elements
Drop Simpla's elements into your code wherever you want editable content.

Use `<simpla-text>` for editable text:

```comment
Use simpla-text for editable text
```

```html
<simpla-text sid="text"></simpla-text>
```

<simpla-text class="simpla-example" editable></simpla-text>

Use `<simpla-img>` for editable images:

```comment
Use simpla-img for editable images
```

```html
<simpla-img sid="img"></simpla-img>
```

<simpla-img class="simpla-example" editable></simpla-img>

All Simpla elements must have a unique _Content ID_ (usually contained in the `sid` attribute) and both opening and closing HTML tags.

### Create content
Open your page in a browser, add `#edit` to the end of the URL (eg: `https://mysite.com#edit`), and login to start editing your content. When you're finished press save to publish your changes. Remove `#edit` from the URL to exit edit mode.

# Installation and setup
Simpla runs on the frontend over a RESTful API. It runs on any stack, and works with the framework or tools you already use.

### Install
```comment
Include Simpla from the CDN
```

```html
<script src="https://app.simpla.io"></script>
```

```comment
Or locally via Bower
```

```sh
$ bower install --save simpla
```

Include the [core library](https://github.com/simplaio/simpla) either from our high-redundancy CDN or locally via Bower. 

### Setup

<hr> 

```js
// Init with project ID
Simpla('PROJECT-ID');

// Init with options object
Simpla({
  project: 'PROJECT-ID'
});

```

To initialize Simpla call `Simpla()` with your project ID, either as a string or a property in an options object.

## Options

<hr>

```comment
Defaults of Simpla()
```

```js
Simpla({
  project: '',
  elements: {
    base: 'https://elements.simpla.io',
    paths: [
      '/simpla-block/simpla-block.html',
      '/simpla-text/simpla-text.html',
      '/simpla-img/simpla-img.html',
      '/sm-admin/sm-admin.html'
    ]
  }
});
```

Simpla is configurable via the `Simpla()` initializer.

**`project`**

Every Simpla project has a unique ID. Simpla can't fetch or save data without a valid project ID set.

**`elements`**

```comment
The elements property can also be given an array of full URLs
```

```js
Simpla({
  elements: [
    'https://elements.simpla.io/simpla-block/simpla-block.html',
    'https://elements.simpla.io/simpla-text/simpla-text.html',
    'https://elements.simpla.io/simpla-img/simpla-img.html',
    'https://elements.simpla.io/sm-admin/sm-admin.html'
  ]
})
```

Simpla's HTML elements need to be loaded onto your page before you can use them. The `elements` property takes either an array of full paths to elements, or an object with a `base` url and an array of relative `paths`.

**Note:** All elements _must_ be loaded from the same place, otherwise dependencies won't be properly resolved.

## Hosting elements locally

<hr>

```comment
Install with bower and change the 'base' property to your Bower components directory
```

```sh
$ bower install --save SimplaElements/simpla-block SimplaElements/simpla-text SimplaElements/simpla-img SimplaElements/sm-admin
```

```js
Simpla({
  elements: {
    base: '/bower_components'
  }
});
```

If you're working with [Polymer](https://www.polymer-project.org), serve Simpla's elements locally to avoid dependancy conflicts. Install them with Bower then change the `base` property to your Bower components directory.

**Note:** If possible, hotlinking from Simpla's element CDN (`elements.simpla.io`) is highly recommended, since it multiplexes requests over HTTP/2.

# Using the elements
You create dynamic content with Simpla using a collection of new HTML elements, like `<simpla-text>` and `<simpla-img>`.

## Content IDs
Simpla elements require a 'content ID', which is used to fetch the right piece of content for a given element. A content ID can be any string that doesn't contain spaces or periods (`.`), since Simpla uses periods internally to represent hierarchies.

### SIDs

```html
<simpla-text sid="my-text"></simpla-text>
```

By default, you should set an element's content ID as an `sid` (Simpla ID). SIDs are scoped to the namespaces created by `<simpla-block>` elements, allowing you to create structured data on your page (see [Structuring Data](#structuring-data)).

### GIDs

```html
<simpla-text gid="global-text"></simpla-text>
```

You can use a `gid` (Global ID) to break out of namespaces and ensure it has the same data no matter where it's used in your project. This is useful for using one piece of content in multiple places, for example: reflecting a page title to a nav item (see [Global Data](#global-data)).

## Setting properties

```comment
Set element properties as attributes
```

```html
<simpla-text sid="text" inline></simpla-text>    
```

```comment
Or with Javascript
```

```js
var text = document.querySelector('simpla-text');
text.inline = true;
```

Simpla elements have various properties associated to them (eg: `sid` and `gid`). These properties can be set as HTML attributes or with Javascript. If a property name is multi-word, it is kebab cased in HTML (eg: `my-property`), and camel cased in Javascript (eg: `myProperty`).
# Text

```comment
Simpla-text can be a container or inner content
```

```html
<simpla-text sid="container"></simpla-text>

<h1><simpla-text sid="content"></simpla-text></h1>
```

`<simpla-text>` contains editable rich-text. You can use it as a standalone container or as the content inside other textual elements (eg: headings).

<simpla-text class="simpla-example" editable></simpla-text>

## Options 

### Inline mode
```comment
Force line-breaks with the 'inline' property
```

```html
<simpla-text sid="inline-text" inline></simpla-text>
```

By default simpla-text creates paragraphs for new lines. You can disable paragraphs and force line-breaks instead with the `inline` property. Inline mode is automatically enabled when simpla-text is used inside other textual elements (eg: headings).

### Placeholders
```comment
Set a custom placeholder with the 'placeholder' property
```

```html
<simpla-text sid="title" placeholder="Start typing..."></simpla-text>
```

Simpla-text shows a placeholder in edit mode when it has no content. You can customize the default placeholder with the `placeholder` property.
# Images
```comment
Simpla-img is an editable image
```

```html
<simpla-img sid="img"></simpla-img>
```

`<simpla-img>` is an editable image. Use it in place of the static HTML `<img>` element.

<simpla-img class="simpla-example" editable></simpla-img>

**Note:** Currently setting `width` and `height` attributes directly on a `<simpla-img>` is not supported. Sizing must be done via CSS.

## Options

### Popout mode
If a `<simpla-img>` is partially off-screen whilst editing, it will 'pop' into view when clicked.

```comment
Force a simpla-img to always popout
```

```html
<simpla-img sid="img" popout></simpla-img>
```

You can force a simpla-img to always pop into view when editing with the `popout` attribute. This is useful when editing controls are obscured by something other than the viewport, eg: inside a rounded container with `overflow: hidden`.

### Placeholders
```comment
simpla-img supports any valid CSS background as a placeholder
```

```html
<simpla-img sid="img-1" placeholder="http://placekitten.com/g/600/400"></simpla-img>

<simpla-img sid="img-2" placeholder="#64d8e8"></simpla-img>

<simpla-img sid="img-3" placeholder="pink"></simpla-img>
```

Simpla-img shows a placeholder in edit mode when it has no content. You can customize it with the `placeholder` property. Placeholders can be a path to an image or any valid CSS color value. 

**Note:** If an image is used as a placeholder it doesn't determine the size of `<simpla-img>` like actual content does.

<div class="simpla-example">
  <simpla-img sid="example" placeholder="http://placekitten.com/g/600/400"></simpla-img>
  <simpla-img sid="example" placeholder="#64d8e8"></simpla-img>
  <simpla-img sid="example" placeholder="pink"></simpla-img>
</div>

# Structuring data

Simpla's data structure is constructed on the fly. This means you can very easily create dynamic experiences, with just HTML and Javascript.

## Namespacing

```comment
Create namespaces with simpla-block
```

```html
<simpla-block sid="block">

  <!-- This 'text' is scoped to 'block' -->
  <simpla-text sid="text"></simpla-text>

</simpla-block>
```

Create namespaces, or content blocks, with the `<simpla-block>` element. The SIDs of elements inside a `<simpla-block>` are scoped to that block, ensuring that their content is unique. Like other Simpla elements, simpla-block requires a Content ID to identify the namespace it creates.

```comment
Nest blocks to create hierarchies
```

```html
<simpla-block sid="page">
 
  <!-- page > title -->
  <simpla-text sid="title"></simpla-text>
  
  <simpla-block sid="feature">
    <!-- page > feature > title -->
    <simpla-text sid="title"></simpla-text>
  </simpla-block>

</simpla-block>
```

You can infinitely nest simpla-blocks to create hierarchies. Their SID acts the same as other elements, scoped to their parent block.

## Global data

<hr>

```comment
Break out of namespaces with Global IDs
```

```html
<simpla-block sid="block">

  <!-- The data in this text is NOT scoped -->
  <simpla-text gid="global-text"></simpla-text>

</simpla-block>

<!-- This 'global-text' has the same data -->
<simpla-text gid="global-text"></simpla-text>
```

Break out of namespaces with Global IDs, defined in the `gid` property. Data tied to a GID ignores scoping and is accessible anywhere in your project. Edits in one element will be reflected in all others with the same GID. This is useful for pieces of content that are the same no matter where they're used (eg: contact details, headers and footers).

Simpla-blocks can use GIDs as well, to create globally unique namespaces.

**Note:** If a Simpla element has both an SID and GID, the GID takes precedence.


## Dynamic reloading 

<hr>

```comment
Changing Content IDs reloads data
```

```html
<!-- Change sid to load a new post -->
<simpla-block sid="post-123">

  <h1><simpla-text sid="title"></simpla-text></h1>

  <simpla-text sid="content"></simpla-text>

</simpla-block>
```

Whenever the content ID of a Simpla element changes it re-fetches its data, and in the case of `<simpla-block>`, forces all of its children to recalculate their data as well. This means you can swap whole sections of content by just changing the `sid` of a surrounding block.

For example, you can create a simple frontend blog with a few lines of HTML and Javascript.

# Javascript SDK

```comment
Use Simpla's SDK after initializing your project
```

```js
Simpla('PROJECT-ID');
```

Use Simpla's Javascript SDK to interact with the global state of your app and the API.

```js
window.simpla = Simpla('PROJECT-ID');
```

Before using the SDK make sure you initialize your project with the `Simpla()` initalizer. The initializer returns itself, so you can also store the SDK in a variable if you prefer

## Authentication
Programatically authenticate users with the `login()` and `logout()` methods (note you only need these if you want a programatic way to login/logout, Simpla handles frontend user authentication for you).

### Login
```comment
Authenticate a user with login()
```

```js
simpla
  .login({
    email: '...', 
    password: '...'
  })
  .then(function(token) {
    // Login successful
  })
  .catch(function(error) {
    // Login failed
  });
```

The `login()` method takes an object containing the user's credentials in `email` and `password` properties. It returns a promise with the user's auth token.

### Logout

```comment
Log a user out with logout()
```

```js
simpla
  .logout()
  .then(function() {
    // User logged out
  });
```

The `logout()` method clears the user's token and returns a promise, it doesn't take any arguments. 

## Getting and setting content
Use the low-level `get()` and `set()`  methods to get and set content straight from Simpla's API.

### Get content

```comment
Fetch content with get()
```

```html
<simpla-text sid="my-text"></simpla-text>
```

```js
simpla
  .get('my-text')
  .then(function(data) {
    // JSON data
  });
```

Use the `get()` method to fetch any piece of content from the API. It takes a single argument, the ID of the content, and returns a promise with JSON data.

### Get a namespace

<hr>

```comment
Calling get() on a namespace returns its children
```

```html
<simpla-block sid="section">
  <simpla-text sid="my-text"></simpla-text>
  <simpla-img sid="my-img"></simpla-img>
</simpla-block>
```

```js
simpla
  .get('section')
  .then(function(elements) {
    // Array of items
  });
```

Calling `get()` on the Content ID of a namespace (created with `<simpla-block>`) returns an array of the children in that namespace. 

### Set content

<hr>

```comment
Save JSON data with set()
```

```js
simpla
  .set('id', {
    id: 'id',
    ...
  })
  .then(function() {
    // Successfully set data
  });
```

You can save arbitrary JSON data to any Content ID with the `set()` method. It takes two arguments, an ID in a string and a JSON data object, and returns a promise.

You must be authenticated (see [Authentication](#authentication)) to use `set()`.

### Nested SIDs

<hr>

```comment
Chain SIDs with periods to traverse namespaces
```

```html
<simpla-block sid="page">
  <simpla-block sid="section">
    <simpla-text sid="title"></simpla-text>
  </simpla-block>
</simpla-block>
```

```js
simpla.get('page.section.title');
simpla.set('page.section.content', {});
```

To access content inside namespaces, chain SIDs with periods. This also allows you to create arbitrary data structures instantly with `set()`.

# Contributing
Simpla is open-source under the MIT license, visit our GitHub repos:

**[github.com/simplaio/simpla][simplaio/simpla]** 
The core Simpla library

**[github.com/SimplaElements][SimplaElements]** 
Simpla's element catalogue, hosted on elements.simpla.io

[simplaio/simpla]: https://github.com/simplaio/simpla
[SimplaElements]: https://github.com/SimplaElements

## The elements
The bulk of Simpla's functionality comes from elements in the ecosystem, each talking independently to Simpla's API.

### [`simpla-block`][simpla-block]
Structures data by creating namespaces for SIDs.

### [`simpla-text`][simpla-text]
Contains editable rich-text.

### [`simpla-img`][simpla-img]
An editable image.

### [`sm-module-save`][module-save]
Contains the UI and logic that request all elements save their data back to the API.

### [`sm-module-login`][module-login]
Contains the UI and logic to log a user in when entering edit mode.

### [`sm-module-notify`][module-notify]
Simpla's notification centre. Handles all success, warning, and error messages by logging them and/or notifying with toasts.

[simpla-block]: https://github.com/SimplaElements/simpla-block
[simpla-text]: https://github.com/SimplaElements/simpla-text
[simpla-img]: https://github.com/SimplaElements/simpla-img
[module-save]: https://github.com/SimplaElements/sm-module-save
[module-login]: https://github.com/SimplaElements/sm-module-login
[module-notify]: https://github.com/SimplaElements/sm-module-notify

## Reporting issues
If you find a bug, please report it! If you know which component in the ecosystem is causing the trouble, open a GitHub issue on the appropriate repository. Otherwise open an issue on [simplaio/simpla][simplaio/simpla] or jump on our [Slack] channel and let us know.

Thorough bug reports with expected behavior and steps required to duplicate the issue are greatly appreciated and will help us move quickly.

[slack]: https://slack.simpla.io
[simplaio/simpla]: https://github.com/simplaio/simpla

# Browser support

Simpla supports all modern browsers:

| Browser           | Supported Version   |  
| :---------------- | :------------------ |  
| Google Chrome     | Current             |  
| Internet Explorer | 10+                 |  
| Microsoft Edge    | Current             |  
| Firefox           | Current             |  
| Safari            | 7+                  |  
| Opera             | Current             |  
| Safari Mobile     | Current             |  
| Chrome Mobile     | Current             |  

Simpla relies on an emerging family of specifications called [Web Components](https://www.w3.org/wiki/WebComponents/). Support for Web Components is being actively developed by all major vendors - Google Chrome currently has full support, other browsers have partial support and require polyfills. 

In practice this means Simpla enjoys native-level performance in Chrome, and performance similar to other leading Javascript libraries in other browsers.


| Browser           | Supported Version   | Method     |  
| :---------------- | :------------------ | :--------- |  
| Google Chrome     | Current             | Native     |  
| Internet Explorer | 10+                 | Polyfill   |  
| Microsoft Edge    | Current             | Polyfill   |  
| Firefox           | Current             | Polyfill   |  
| Safari            | 7+                  | Polyfill   |  
| Opera             | Current             | Native     |  
| Safari Mobile     | Current             | Polyfill   |  
| Chrome Mobile     | Current             | Native     |  

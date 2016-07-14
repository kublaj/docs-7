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

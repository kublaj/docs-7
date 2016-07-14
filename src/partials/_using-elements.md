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
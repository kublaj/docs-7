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

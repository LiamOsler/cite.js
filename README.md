# `cite.js`

`cite.js` is a vanilla JavaScript library for making it easy to cite academic, literary, artistic and other works on the web. 

It is designed to be easy to use and easy to extend. `cite.js` is unopinionated about how you should cite works, emphasizes metadata over style, and is designed to be flexible enough to support a wide range of citation styles and formats. 

## Features
- Flexible citation metadata definition style.
- Inline and block citation support.
- Citation of hypermedia and non-hypermedia works.
- Support for multiple citation and reference section styles.
- Extensibility for custom citation styles.

## Installation
### Basic installation
Include `cite.js` at the end of the body of your HTML:

```html
<!DOCTYPE >
<html>
<head>
    <title>Document</title>
</head>
<body>

    <script src="cite.js"></script>
</body>
</html>
```

## Usage
`cite.js` uses the `data-*` global attribute to store information about the works cited in HTML.

Take for instance a sentence that cites a work without using any specific citation style:

```html
<p>Nielsen wrote a report on his time at the Hypertext'89 conference.<p>
```

The `data-cite` attribute is used mark an element as having a citation:

```html
<p data-cite>
    Nielsen wrote a report on his time at the Hypertext'89 conference.
</p>
```

`cite.js` can also be used by combining the `data-cite` attribute in a parent element along with `data-cite-*` as attributes on relevant child elements. For instance, the same segment could be cited in the following way:

```html
<p data-cite>
    <span data-cite-author = "Jakob Nielsen">Nielsen</span> wrote a report on his time at the <span data-cite-title = "Trip Report: Hypertext '89">Hypertext'89</span> conference.
</p>
```

This can be extended to include the citation metadata:

```html
<p data-cite
    data-cite-author = "Jakob Nielsen" 
    data-cite-title = "Trip Report: Hypertext '89" 
    data-cite-publication = "SIGCHI Bulletin" 
    data-cite-volume = "21" 
    data-cite-issue = "4" 
    data-cite-page = "52-61" 
    data-cite-url = "https://doi.org/10.1145/379106.379121">
    Nielsen wrote a report on his time at the Hypertext'89 conference.
</p>
```



This also provides the flexibility to cite the title of the work from the inner text of the element:

```html
<p data-cite
    data-cite-title = "Trip Report: Hypertext '89" 
    data-cite-publication = "SIGCHI Bulletin" 
    data-cite-volume = "21" 
    data-cite-issue = "4" 
    data-cite-page = "52-61" 
    data-cite-url = "https://doi.org/10.1145/379106.379121">
>
    <span data-cite-author = "Jakob Nielsen">Nielsen</span> wrote a report on his time at the Hypertext'89 conference.
</p>
```


## Important `data-cite-*` attributes

`data-cite` - Marks an element as a citation.

`data-cite-title` - The title of the work being cited.

`data-cite-author` - The author(s) of the work being cited. Multiple authors should be separated by a semicolon (support for more formatting options is planned). `data-cite-authors` is also supported, and redundant with `data-cite-author`.

Other custom attributes can be used to store additional metadata about the work being cited. For instance, `data-cite-publication`, `data-cite-volume`, `data-cite-issue`, `data-cite-page`, `data-cite-url`, etc.


## More complex examples

### Citing a book with a blockquote

  

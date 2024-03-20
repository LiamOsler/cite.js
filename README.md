# `data-cite-*` and `cite.js`

`data-cite-*` and `cite.js` are both a citation style for HTML which used the `data-*` global attribute designed to make it easy to academic, literary, artistic and other works on the web, and a vanilla JavaScript library for making it easy to create footnotes, endnotes, and bibliographies in HTML documents.

`cite.js` is designed to be easy to use and easy to extend. `cite.js` emphasizes metadata over style, and is designed to be flexible enough to support a wide range of citation and references formats. 

## Features
- Flexible citation metadata definition style.
- Inline and block citation support.
- Citation of hypermedia and non-hypermedia works.
- Support for multiple citation and reference section styles.
- Extensibility for custom citation styles.

## Installation
### Basic installation of `cite.js`
Include `cite.js` in HTML:

```html
<!DOCTYPE HTML>
<html>
<head>
    <title>Document</title>
</head>
<body>

    <script src = "cite.js"></script>
</body>
</html>
```

### Module installation of `cite.js`
(Modulized installation instructions here)

## Usage
`cite.js` uses the `data-*` global attribute to store information about the works cited in HTML.

The `data-cite` attribute is used to mark an element as having a citation. This can be used to mark an entire paragraph, a blockquote, or any other element as having a citation.

`data-cite-*` attributes are used to store metadata about the work being cited. This can include the author, title, publication, volume, issue, page, URL, and other metadata about the work being cited.

Take for instance a sentence that cites a work without using any specific citation style:

```html
<p>Nielsen published a report on his time at the Hypertext'89 conference.<p>
```

The `data-cite` attribute is used mark an element as having a citation:

```html
<p data-cite>
    Nielsen published a report on his time at the Hypertext'89 conference.
</p>
```

This can be extended to include some metadata about the citation:

```html
<p data-cite 
    data-cite-author = "Jakob Nielsen" 
    data-cite-title = "Trip Report: Hypertext '89"  
    data-cite-publication = "SIGCHI Bulletin">
    Nielsen published a report on his time at the Hypertext'89 conference.
</p>
```

`cite.js` can also be used by combining the `data-cite` attribute in a parent element along with `data-cite-*` as attributes on relevant child elements. For instance, the same segment could be cited in the following way:

```html
<p data-cite>
    <span data-cite-author = "Jakob Nielsen">Nielsen</span> 
    <span data-cite-title = "Trip Report: Hypertext '89">published a report on his time</span> 
    at the Hypertext'89 conference.
</p>
```

Where additional information about the work being cited is stored in the `data-cite-*` attributes of either (or both) the parent and child elements.
```html
<p data-cite
    data-cite-volume = "21" 
    data-cite-issue = "4" 
    data-cite-page = "52-61" 
    data-cite-url = "https://doi.org/10.1145/379106.379121">
    <span data-cite-author = "Jakob Nielsen">Nielsen</span> 
    <span data-cite-title = "Trip Report: Hypertext '89">published a report on his time</span> 
    at the Hypertext'89 conference.
</p>
```

## Common `data-cite-*` attributes

`data-cite` - Is required and marks an element as a citation. Though somewhat unusual, HTML does allow for the use of attributes without values. `data-cite` is combined with other `data-cite-*` attributes to store metadata about the work being cited, either from the HTML element itself or from the value of the `data-cite-*` attribute.

`data-cite-type` - The type (book, article, journal, etc...) of the work being cited.

`data-cite-title` - The title of the work being cited.

`data-cite-author` - The author(s) of the work being cited. Multiple authors should be separated by a semicolon (support for more formatting options is planned). `data-cite-authors` is also supported, and redundant with `data-cite-author`.

Multiple `data-cite-author` attributes can be used to store the names of multiple authors. Unique names will be used to store the names of the authors.

Other custom attributes can be used to store additional metadata about the work being cited. For instance, `data-cite-publication`, `data-cite-volume`, `data-cite-issue`, `data-cite-page`, `data-cite-url`, etc.

`cite.js` allows for the use of any HTML elements to store the metadata about the work being cited. For instance, the `data-cite-author` attribute can be used on a `span` element to store the author of the work being cited.

## Complex examples
### Citing a book with a blockquote
Here is an example of a simple HTML formatting of blockquote with a quote from a book:
```html
<blockquote>
    <p>
        Gentry was convinced that cyberspace had a [S]hape, 
        an overall total form. Not that that was the weirdest idea 
        Slick had ever run across, but Gentry had this obsessive 
        conviction that the shape mattered totally. The apprehension 
        of the Shape was Gentry's grail.</p>
</blockquote>
<p>
    This exchange from <cite>Mona Lisa Overdrive</cite> by author 
    William S. Gibson is an example of the philosophical and ontological 
    debates surrounding the nature of virtual spaces within science fiction.
</p>
```

Metadata about the citation can be added using `cite.js` attributes like this:
```html
<span data-cite data-cite-isbn = "0586207473">
    <blockquote data-cite-page = "55" data-cite-chapter = "The Shape" data-cite-paragraph = "1">
        <p> Gentry was convinced that cyberspace had a [S]hape, 
            an overall total form. Not that that was the weirdest idea 
            Slick had ever run across, but Gentry had this obsessive 
            conviction that the shape mattered totally. The apprehension 
            of the Shape was Gentry's grail.
        </p>
    </blockquote>
    <p>
        This exchange from <cite data-cite-title>Mona Lisa Overdrive</cite> by author 
        <span data-cite-author>William S. Gibson</span> is an example of the philosophical 
        and ontological debates surrounding the nature of virtual spaces within science fiction.
    </p>
</span>
```

Wrapping the blockquote and corresponding blockquote and citation in a `span` with the `data-cite` attribute allows for the citation to be treated as a single unit.

Within the `span`, the `data-cite-title` and `data-cite-author` attributes are used to store the title and author of the work being cited. 

`<cite data-cite-title>Mona Lisa Overdrive</cite>`

`<span data-cite-author>William S. Gibson</span>`

The `data-cite-page` attribute is used to store the page number of the quote.

`<blockquote data-cite-page = "55">`

It can be supplemented with additional metadata about the work being cited, such as the chapter and paragraph number.

`<blockquote data-cite-page = "55" data-cite-chapter = "The Shape" data-cite-paragraph = "1">`

This brings the content of the citation closer to the content of the work being cited, and makes it easier to manage the citation as a single unit. It also has the advantage of not depending on client or server-side parsing of the citation data to display the inline citation content. This allows for `data-cite-*` to remain close to the content of the work being cited, which is in keeping with the principles of Hypermedia as the Engine of Application State (HATEOAS).

### Usage of the `<cite>` element

HTML has a `<cite>` element that is used to mark the title of a work being cited. This can be used to mark the title of a work being cited, and can be used in combination with `data-cite-*` attributes to store metadata about the work being cited.

```html
<p data-cite data-cite-isbn = "0586207473">
    This exchange from <cite data-cite-title>Mona Lisa Overdrive</cite> by author 
    <span data-cite-author>William S. Gibson</span> is an example of the philosophical 
    and ontological debates surrounding the nature of virtual spaces within science fiction.
</p>
```

In this example, `<cite data-cite-title>Mona Lisa Overdrive</cite>` is used to mark the title of the work being cited, and `data-cite-author` is being used on a `<span>` tag to mark the author of the work being cited. The book's ISBN is also being stored in the `data-cite-isbn` attribute in the parent `<p>` tag, which also marks the citation.

### Citing the same work multiple times
Two methods can be used to cite the same work multiple times. The first method is to use the same `data-cite-*` attributes on multiple elements. This method is useful when the same work is being cited multiple times in the same document.



## Extending `data-cite-*` and `cite.js`.
`data-cite-*` and `cite.js` are designed to be flexible and extensible. `data-cite-*` attributes can be used to store any metadata about the work being cited, and `cite.js` can be extended to support custom citation styles. One may even consider including segments of the work being cited in the data-cite-* attributes, though this is not recommended unless the cited work is in the public domain or the inclusion of the work is covered by fair use or another exception to copyright.

## Creating a bibliography
`cite.js` can be used to generate a bibliography by using creating an HTML element with the `bibliography` id. This element will be populated with the citations in the document.

```html
<!DOCTYPE HTML>
<html>
<head>
    <title>Document</title>
</head>
<body>
    <div id = "bibliography"></div>
    <script src = "cite.js"></script>
</body>
</html>
```

The contents of the `bibliography` element will be populated with the citations in the document.

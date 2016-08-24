# Introduction #

Unlike `$.html()` that returns only the element's HTML content, `$.outerHTML()` returns the
selected element and its HTML content or replaces it as `jQuery.replaceWith()` method but
without loosing the chaining. This version introduces support to replace a set of matched
elements by DOM Elements and jQuery objects. It also introduces the support to `.outerHTML(function)`.
Check Notes of the Version for more details.

Check the "examples" folder for some working example.

#### Getting the HTMLString with `.outerHTML()`

Get the HTML of the first element and with its contents in the set of matched elements.

```
var html = $('div').outerHTML();
```

This method uses the browser's outerHTML property that is available for most popular
browsers. When the property is not available, the element is cloned using the browser's
`cloneNode` or jQuery's clone, appended to a temporary `Node` and the `innerHTML` is taken from there.

#### Replacing the `Element` with `.outerHTML(newContent)`

Get the set of matched elements and replace them with the new content and returns the set
of replacing elements.

The replacing content can be a `HTMLString`, an `Element` or a jQuery object.

```
// Replacing a span tag for a link 
var replacingContent = '<a hre="#">Replacing link</a>';

$('span').outerHTML(replacingContent);
```

#### Using `.outerHTML(function(index, outerHTML))` for multiple elements

You can use a function that will receive the `outerHTML` of every matched `Element`.

In the example below, a set of links would replaced by span tags keeping the original text. 

```
$('a').outerHTML(function(index, outerHTML){

    var $this = $(this),
        textContent = $this.text();

    $this.outerHTML('<span>' + textContent + '</span>');

});
```

## License
Copyright (c) 2015 Darlesson Oliveira. Licensed under the MIT license.

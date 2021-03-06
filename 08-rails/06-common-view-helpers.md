# Common View Helpers
## Learning Goals
- What's a view helper?
- Explore some of the most common helpers

## Rails is v helpful
Rails provides many methods when working in views that automate and/or simplify common, tedious tasks in HTML. These methods are collectively referred to as view helpers.

## Some common helpers

### `link_to(text, path, options)`
`link_to` creates an HTML `<a>` element. The first argument given to the method will become the text between the `<a></a>` tags, the second argument will become the value assigned to the `href` attribute of the tag:

```erb
<%= link_to "About Me", "/profile" %>
```

becomes

```html
<a href="/profile">About Me</a>
```

An additional options hash argument is optional to set arbitrary attributes of the `<a>` tag:

```erb
<%= link_to "About Me", "/profile", class: "link" %>
```

The above `link_to` will give you this HTML:

```html
<a href="/profile" class="link">About Me</a>
```

### `button_to(text, path)`
`button_to` is used to generate a form with where the _only_ input is a submit button.
This is generally used to submit HTTP requests with a method type other than `GET`.

```erb
<%= button_to "Remove That", "/products/1" %>
```

The above `button_to` will give you this HTML:

```html
<form method="POST" action="/products/1" >
  <div><input value="Remove That" type="submit" /></div>
</form>
```

`button_to` will default to an http method of POST, but that can be changed by passing an
optional argument of method.

```erb
<%= button_to "Remove That", "/products/1", method: :delete %>
```

The above `button_to` using the optional parameter will give you this HTML:

```html
<form method="DELETE" action="/products/1" >
  <div><input value="Remove That" type="submit" /></div>
</form>
```

### `image_tag(filename, options)`
`image_tag` generates an HTML `<img>` tag. The argument given will be an image filename for the `src` attribute. Rails (the asset pipeline) looks in the `app/assets/images` directory for images. You can provide additional attributes as optional hash parameters:

```erb
<%= image_tag "cat.jpg", alt: "The cutest cat in the whole world." %>
```

The above `image_tag` will give you this HTML:

```html
<img src="/assets/cat.jpg" alt="The cutest cat in the whole world.">
```
## Helpful Links
- [An overview of helpers](http://guides.rubyonrails.org/action_view_overview.html#overview-of-helpers-provided-by-action-view)
- [Complete documentation on view helpers](http://api.rubyonrails.org/classes/ActionView/Helpers.html)

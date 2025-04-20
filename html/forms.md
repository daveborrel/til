# Form

An basic HTML element that handles submitting information.

Inside it, there can be: `<input>`, `<button>`, etc.

```html
<form action="/action_page.php">
  <label for="fname">First name:</label><br />
  <input type="text" id="fname" name="fname" /><br /><br />
  <input type="submit" value="Submit" />
</form>
```

`method` - the HTTP method a person submits the form with
`action` - the URL that processes this information in the form

### Sources

[MDN Notes](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/form)

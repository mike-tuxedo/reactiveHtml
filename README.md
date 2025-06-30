# reactiveHtml

A lightweight, zero-dependency library for making plain HTML reactive with minimal JavaScript. It enables template-style variable binding and reactive DOM updates, all with native browser features. And of course, it's opensoucre ;-)

## Features
- Reactivity for variables in HTML: `{variable}` syntax
- `rs-if` directive for conditional rendering
- `rs-for` directive for list rendering
- Works with direct DOM manipulation
- View Transition API support for smooth animations

## Demo
Open `reactiveHtml.html` in your browser to see a live demo. Try adding todos, toggling visibility, and editing variables to see reactivity in action.

## Usage
1. Clone the repo or copy the `reactiveHtml` folder.
2. Open `reactiveHtml.html` in your browser.
3. Edit the HTML or JS to fit your needs.

## Example
```html
<h2 class="color-{color}">Hello, {name}!</h2>
<input id="nameInput">

<script>
  // initialize with default values
  const store = new ReactiveStore({ name: 'Mike' });

  const { rs } = store;
  document.getElementById('nameInput').addEventListener('input', e => {
    rs.name = e.target.value;
  });
</script>
```

## License
MIT

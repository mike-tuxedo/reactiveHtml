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

<button conclick="addNode()">Add some html node</button>
<div id="newNodes"></div>

<script>
  // Initialize with default values. THATS ALL you have to do! :-)
  const { store, rs } =  = new ReactiveStore({ name: 'Mike' });


  // =================================//
  // The rest is your custom app code //
  // =================================//
  document.getElementById('nameInput').addEventListener('input', e => {
    rs.name = e.target.value;
  });

  function addNode() {
    const paragraph = document.createElement('p');
    paragraph.innerHTML = 'This is a new node with reactive value {name} in it.';
    document.getElementById('newNodes').appendChild(paragraph);
    // If you manually manipulate the dom, you have to call reparse(node). For performance reasons, the store doesn't track every dom change by default.
    store.reparse(paragraph);
  }
</script>
```

## License
MIT

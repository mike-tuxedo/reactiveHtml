# reactiveHtml

A lightweight, zero-dependency, tiny javascript class for making plain HTML reactive. It enables template-style variable binding and reactive DOM updates, all with native browser features. And of course, it's opensoucre ;-)
ReactiveHtml is not feature rich, it has just 3 keyfeatures that I think does most of the job (see Features). If you need a more features, you may be better of with alpinejs, sveltekit, or something like that. I like the kiss principle, so I kept it as simple as I can.

In the future, I will add a basic app like example, but for now stick with the demo page respectively the example below.

## Features
- Reactivity for variables in HTML: `{variable}` syntax
- `rs-if` directive for conditional rendering
- `rs-for` directive for list rendering
- Works with direct DOM manipulation
- View Transition API support for smooth animations

## Demo
Open `reactiveHtml.html` in your browser to see a live demo. Try adding todos, toggling visibility, and editing variables to see reactivity in action.
Preview https://mike-tuxedo.github.io/reactiveHtml/

## Usage
1. Include reactiveHtml.js into your page `<script src="reactiveHtml.js"></script>`.
2. Edit your html or where ever you have your javascript and initiate a store, following the example below.

## Example
```html
<h2 class="color-{color}">Hello, {name}!</h2>
<input id="nameInput">

<button conclick="addNode()">Add some html node</button>
<div id="newNodes"></div>

<!-- if directive -->
<button onclick="toggleShowElement()">toggleShowElement</button>
<p rs-if="showElement">Only visible if {showElement} is true.</p>

<!-- for directive -->
<ul class="items" rs-for="item in items">
    <li class="item">
        <p>{item.name} (idx: {index})</p>
    </li>
</ul>

<script>
  // Initialize with default values. THATS ALL you have to do! :-)
  const { store, rs } =  = new ReactiveStore({ name: 'Mike', showElement: false, items: [{ name: 'Andi' }, { name: 'Tim' }] });

  // =================================//
  // The rest is your custom app code //
  // =================================//
  document.getElementById('nameInput').addEventListener('input', e => {
    rs.name = e.target.value;
  });

  function toggleShowElement() {
      rs.showElement = !rs.showElement;
  }

  function addNode() {
    const paragraph = document.createElement('p');
    paragraph.innerHTML = 'This is a new node with reactive value {name} in it.';
    document.getElementById('newNodes').appendChild(paragraph);
    /* If you manually manipulate the dom, you have to call reparse(node). */
    /* For performance reasons, the store doesn't track every dom change by default. */
    store.reparse(paragraph);
  }
</script>
```

## License
MIT

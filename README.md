# 🚀 reactiveHtml &nbsp; ![MIT License](https://img.shields.io/badge/License-MIT-green) ![Zero Dependencies](https://img.shields.io/badge/zero-dependencies-blue) ![Made with JS](https://img.shields.io/badge/made%20with-JavaScript-yellow)

> **⚠️ DISCLAIMER:**  
> _This project is far from production ready. It hasn't been tested on any real world projects yet!_  
> Just try it out and let me know what you think. 😁

---

## ✨ What is reactiveHtml?

**reactiveHtml** is a **lightweight**, **zero-dependency** 🛠️, **tiny** JavaScript class for making **plain HTML reactive**.  
It enables template-style variable binding and lightning-fast DOM updates, all with native browser features—no frameworks needed! ⚡

> Not overloaded with features—just the essentials for most use-cases.  
> If you need more, check out [Alpine.js](https://alpinejs.dev/), [SvelteKit](https://kit.svelte.dev/), etc.

---

## 🌟 Features

- 🧬 **Reactive Variables:** Use `{variable}` syntax in your HTML!
- 🔀 **`rs-if` Directive:** Conditional rendering made easy.
- 🔁 **`rs-for` Directive:** Effortless list rendering.
- 🪄 **Direct DOM Manipulation:** Works even when you edit the DOM yourself!

---

## 🎮 Live Demo

Want to see it in action?  
**1.** Clone or download the repo and open `reactiveHtml.html` in your browser.  
**2.** Or try it live: [🌐 Live Preview](https://mike-tuxedo.github.io/reactiveHtml/)

Add todos, toggle visibility, edit variables… watch the magic happen! ✨

---

## 🚦 Quick Start

1. **Include the script:**  
   ```html
   <script src="reactiveHtml.js"></script>
   ```

2. **Set up your store and HTML. Example below!**

## 🧑‍💻 Example
```html
<!-- reactive variables -->
<h2 class="color-{color}" style="color: {color};">Hello, {name}!</h2>
<input id="nameInput">

<button onclick="addNode()">Add some html node</button>
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
  // Initialize with default values. THAT'S ALL you have to do! 😎
  const { store, rs } = new ReactiveStore({
    name: 'Mike',
    color: 'limegreen',
    showElement: false,
    items: [{ name: 'Andi' }, { name: 'Tim' }]
  });

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
    // If you manually manipulate the DOM, call reparse(node)!
    store.reparse(paragraph);
  }
</script>
```

## 📜 License

MIT – Use it, hack it, share it! 😄
## 💬 Feedback

Love it? Hate it? Want more features?
Open an issue or just ⭐️ the repo!

May your HTML be ever reactive! 🤖✨

## Chapter 5 - Extensions

### Save and Load game
For saving the game, we will use Local Storage mechanism.

According to Wikipedia, Local Storage (also known as DOM storage) provides web apps with methods and protocols for storing client-side data. It is cross-tab storage, meaning you can save data in one tab and have access to it in another or even after you refresh the page!

Sounds cool right? Let's try it out :)

Firstly, let's create 3 new buttons in our `index.html` page. A button to Save, Load and Clear data.

Add the following anywhere within the `<body>` tags:
```html
<button onClick="save()">Save</button>
<button onClick="load()">Load</button>
<button onClick="clearClicks()">Clear</button>
```

Let's create `save()`, `load()` and `clearClicks()` buttons to handle the Save, Load and Clear data functionality precisely.
```js
function save() {
	window.localStorage.setItem('clicks', clicks);
	console.log("Clicks have been saved!");
}

function load() {
	clicks = 0;
	if (window.localStorage['clicks']) {
		clicks = parseInt(window.localStorage['clicks'])
	}
	update()
	console.log("Clicks have been loaded!");
}

function clearClicks() {
	window.localStorage.setItem('clicks', 0);
	console.log("Clicks have been cleared!")
}
```

Try it ;)


### GitHub

Git is cool!

coming later...
## Chapter 1 - Game time!

In this chapter we will focus on using HTML and JavaScript to create a stand-alone "clicker" game. Later chapters will walk you through adding additional functionalities to this game!


HTML DOM is ... TODO: finish


### Step 1 - First things first
Firstly, before we start, you need to understand the file structure. All code will be located in the `/src` folder. The folder has 3 files, `index.html` - the HTMl file, `styles.css` - the CSS file and `scripts.js` - the JavaScript file. In this chapter we will be only touching `index.html` and `scripts.js` files.

To start with, open `index.html` with an Internet Browser (ie Edge).


### Step 2 - `let` the fun begin!

The point of the "clicker" game is to have a button which you can click to start with, so lets make one!

Let's create a button below `<h1>My Clicker Game</h1>` tag:
```html
<button class="clicker" onClick="clicker()">🖱️</button>
```

Refresh your page in the browser and you should see a button with a computer-mouse emoji in it.

> NOTE: Clicking on that button will do nothing and produce an error in the console (for now at least). We will fix this later!

To get that button do something, we can bind an `onClick()` event to it. The `onClick` event will be triggered every time the button is clicked! As you can see, we already done the 'binding' for you, thats `onClick="clicker()"` part. Here we're binding `clicker()` function to be triggered every time the button is clicked. This function will have to be declared in JavaScript.

### Step 3 - The JavaScript world
To start with open `scripts.js` file.

> HINT: You can use `console.log()` to dump anything to browser console. Press F12 and select "Console" tab to see the dump.

Before we rash and create the `clicker()` function, lets create a variable to track the number of clicks. For ease sake, let's call variable `clicks`.
```js
let clicks = 0;
```
*Places it at the very top of the file!*

Now we can make the `clicker()` function to handle the button clicks.

```js
function clicker() {
	clicks = clicks + 1; // increment the global `clicks` variable by 1
	console.log("Clicks: " + clicks);
}
```
*Can you see the number of clicks increasing in the console? If not, then you are did something wrong!*

### Step 4 - Back to HTML
Seeing number increasing in console is cool and everything BUT how about the page?

Let's make a counter field in HTML and get it to update, shall we?

Add the following above the `<button>` code, should look like below:
```html
<p class="clicks"><span id="clickNum">0</span> clicks</p>
<button class="clicker" onClick="clicker()">🖱️</button>
```

The number still won't update because we're not telling the JavaScript to update it!

### Step 5 - Back to JavaScript

Let's create an `update()` function which will update the HTML DOM accordingly!

```js
function update(){
	document.getElementById("clickNum").innerHTML = clicks
}
```

Now, we should call this function every time the button is clicked, remember the `clicker()` function?

Update the `clicker()` function to make look like the following:

```js
function clicker() {
	clicks = clicks + 1; // increment the global `clicks` variable by 1
	update();
	console.log("Clicks: " + clicks);
}
```

Refresh the page and see. Now the number should also update in the page?
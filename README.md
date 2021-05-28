# Clicker-Game-Tutorial

Building an Idle Clicker Game

Today we're going to run you through how to create a website and build your very own Clicker Game. 

In order to do this, we're going to use the HTML (Hyper Text Markup Language) and CSS (Cascading Style Sheet) languages to create your website.  Then we're going to build our game in JavaScript, which will make our game interactive. We'll also be introducing you to some tools used by professional programmers every day:  GitHub and Visual Studio Code. 


To get you started, we've provided you with three files to begin working on your game website. 

Before we can get started coding, we'll need set up the files that we'll be working with on this computer. And if you want to take your work home with you at the end of today, don't worry - we've got a section on that later.


Let's begin by downloading the files we need from GitHub.  The've been put in something called a Git repository, which can be found here:
https://github.com/Popscotch/Clicker-Game-Tutorial
	
### Step 1

Click on the green "Code" button

### Step 2 

Click on 'Download ZIP' and save it to a location on the desktop.

![Image](https://github.com/Popscotch/Clicker-Game-Tutorial/blob/070615562e874536c6e8c8f37765302d59f6d6db/Intro%201.png)

### Step 3 
Unzip the folder.

### Step 4
Open up Visual Studio Code, then click on 'File', followed by 'Open Folder'. Next, navigate to where you un-zipped the folder and open it.  You should now have four files under the explorer window.

![Image](https://github.com/Popscotch/Clicker-Game-Tutorial/blob/070615562e874536c6e8c8f37765302d59f6d6db/Intro%202.png)

![Image](https://github.com/Popscotch/Clicker-Game-Tutorial/blob/070615562e874536c6e8c8f37765302d59f6d6db/Intro%203.png)

The first file we'll be working with is the HTML file called `index.html`.  Click on it in the explorer to open the file.

## Chapter 1

TODO: Max's

## Chapter 2 - Generating more clicks!

Now that we have a button that can increase our clicks, lets make something that can help us generate clicks without having to click ourselves, an "Auto Clicker"!

### Step 1

First, in our `scripts.js` file, and below `let clicks = 0;`, let's add an new variable that keeps track of our `clicksPerSecond` so we have something like below:

```js
let clicks = 0;
let clicksPerSecond = 0;
```

### Step 2

Next, we need to make a button in our `index.html` file to increase the clicksPerSecond by 1 each time it is pressed. So add this above the `<script>` line in the html.

```html
<button onClick="buyAutoClicker()">Buy Auto Clicker</button>
```

We also need to add a `html` element that will tell us what our current `clicksPerSecond` is. So also add this above the button:

```html
<p>Clicks per second: <span id='clicksPerSecond'>0</span></p>
```

This will just look like a single line of text, but this way we can use JavaScript to change the `<span>` specifically.

### Step 3

We've made the button, and we've told it to run `buyAutoClicker()` when it is clicked with the `onClick` attribute. But we still need to define what `buyAutoClicker()` really is. 

To do this, go into your `scripts.js` file, and start with adding this at the bottom of the file:

```JS
function buyAutoClicker() {
    // empty function
}
```

Whenever our button is pressed, the code within the curly brackets of this function will run. We want to increase our `clicksPerSecond`, lets increase that by one:

```JS
function buyAutoClicker() {
    clicksPerSecond = clicksPerSecond + 1;
}
```

### Step 4

We need to update our `update()` function so that our page will update when we increase our `clicksPerSecond`. Like before, we have to set the innerHTML of our `Clicks per second` line whenever something changes. 

When you're done, your `update()` function should look like this:
```JS
function update() {
    document.getElementById("numberOfClicks=").innerHTML = clicks; // TODO (MIGHT NOT BE THE RIGHT ID)
    document.getElementById("clicksPerSecond").innerHTML = clicksPerSecond;
}
```

### Step 5

Now our clicksPerSecond value doesn't do anything, we need to add some functionality to allow it to increase our clicks over time, and we also want to see this happening visually without having to do anything.

We can do this using `setInterval` function.

First, we need to make a `init` function. There's nothing special about the word `init`, all it means is that it will be run once when the page starts.

At the top of your `scripts.js` file, start with adding the following:
```JS
function init() {

}
```

And at the very bottom of that file, just add this line:

```JS
init();
```

Whenever the page is loaded, the `init` will execute, and any code inside will be ran. We want to define what should happen every interval (Seconds, milliseconds, etc) when the page is opened. We we will use a `setInterval` function to tell the page to increase `clicks` by `clicksPerSecond` every 1000 milliseconds (1 second).

```JS
function init() {
    setInterval(function(){
        clicks = clicks + clicksPerSecond;
    }, 1000)
}
```

We also need to make sure that the page actually shows the numbers change. This is simple, just add `update();` after the line that increases `clicks`

```JS
function init() {
    setInterval(function(){
        clicks = clicks + clicksPerSecond;
        update();
    }, 1000)
}
```

Congratulations! Your number of `clicks` should now go up faster and faster the more 'Auto Clickers' you have!

## Chapter 3

The idea of clicker games is that you purchase generators to produce more resources so that you can purchase even more generators that produce even more resources et cetera et cetra.

We're going to generalise our Auto Clicker using a `class`, and then making another generator that's both more powerful and expensive.

### Step 1

Make a class:
```JS
class Generator {
    constructor(name, price, power) {
        this.name = name
        this.price = price
        this.power = power
        this.quantity = 0
    }


}
```

### Step 3
Change buyAutoClicker
```JS
function buyAutoClicker() {
    clicksPerSecond = clicksPerSecond + 1;
}
```

TODO: Inventory:

TODO: Clicks per second function

TODO: Also a price function

## Chapter 4

TODO: Max's

## Chapter 5 - Extensions

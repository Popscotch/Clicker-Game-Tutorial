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

Now that you have a button that can increase your 'clicks', now it's time to make something that can help us generate clicks over time without having to click ourselves, an "Auto Clicker"!

### Step 1

First, in our `scripts.js` file, and below `let clicks = 0;`, add a new variable that keeps track of our `clicksPerSecond` like so:

```js
let clicks = 0;
let clicksPerSecond = 0;
```

### Step 2

Next, you need to make a button in your `index.html` file to increase the clicksPerSecond value by 1 each time it is pressed. So add this between the `<body>` tags in your `index.html` file:

```html
<button onClick="buyAutoClicker()">Buy Auto Clicker - 10 Clicks</button>
```

Then you also need to add an element that will tell you what your current `clicksPerSecond` is. Also add this between the `<body>` tags:

```html
<p>Clicks per second: <span id='clicksPerSecond'>0</span></p>
```

This will just look like a single line of text when you view your page, but this way you can use JavaScript to change the `<span>` specifically, rather than te entire line.

### Step 3

You've made the button, and You've told it to do `buyAutoClicker()` when it is clicked with the `onClick` attribute. But you still need to define what `buyAutoClicker()` really does. To do this, go into your `scripts.js` file, and start with adding this at the bottom of the file:

```JS
function buyAutoClicker() {
    // Code goes here
}
```

Whenever that button is pressed, the code within the curly brackets of this function will be ran. The goal is to increase `clicksPerSecond` so that value can be used to increase `clicks`. Also include the `update()` function, itwill be helpful for later for updating the text on the page itself.

```JS
function buyAutoClicker() {
    clicksPerSecond = clicksPerSecond + 1;
    update();
}
```

To make the 'Auto Clicker' cost 10 'clicks', expand the function using an `if` statement to implement that logic to test if the player can afford it, and if so, remove 10 `clicks` from the player:

```JS
function buyAutoClicker() {
    if (clicks >= 10) {
        clicksPerSecond = clicksPerSecond + 1;
        clicks = click - 10;
        update();
	}
}
```

### Step 4

You next need to update the `update()` function so that the page will update when the `clicksPerSecond` value changes. Like before, you need to set the innerHTML of the `Clicks per second` line whenever something changes. 

When you're done, your `update()` function should look like this:
```JS
function update() {
    document.getElementById("numberOfClicks=").innerHTML = clicks; // TODO (MIGHT NOT BE THE RIGHT ID)
    document.getElementById("clicksPerSecond").innerHTML = clicksPerSecond;
}
```

### Step 5

Now the `clicksPerSecond` value still doesn't actually do anything yet, you first need to add some functionality to allow it to increase our clicks over time, and you also want to see this happening visually without having to do anything.

This is possible using `setInterval` function.

First, make a `init` function. There's nothing special about the word `init`, it's usually a term reserved for functions that are only ran when the page loads up.

At the top of your `scripts.js` file, start with adding the following:
```JS
function init() {
    // Code goes here
}
```

Then, at the very bottom of that file, just add this line:

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

The general idea of clicker games is that you purchase generators to produce more resources so that you can purchase even more generators that produce even more resources et cetera et cetra. It's a game about exponential growth.

We're going to generalise our Auto Clicker using a `class`, and create some functions so our game is more dynamic.

### Step 1

Let's define a 'generator' class. This is what represents a generator, and we'll ues this class to make more generators.

```JS
class Generator {
    constructor(name, price, power) {
        this.name = name;
        this.price = price;
        this.power = power;
	this.quantity = 0;
    }
}
```

### Step 2

You'll also make an object that contains possible generators like so:

```JS
var generators = [
    new Generator('Auto Clicker', 10, 1)
];
```

What's happening here, is that you've created a class with a `constructor`, a constructor is a function that is called when the class is made. In the `generators` list, it's creating a new generator, and telling it that the name is 'Auto Clicker', the price is '10', and it's power is '1' as per the `constructor` function within the class definition.

### Step 3

You'll need to update some of your previous code to make use of these changes. In the code, `generators[0]` represents the first item in the `generators` list. The 0 represents the `index`, and you can refer to other generators you might add by increasing that number. (Such as `generators[1]` for the second item, if there is one)

```JS
function buyAutoClicker() {
    if (clicks >= generators[0].price) {
    	clicksPerSecond = clicksPerSecond + generators[0].power;
        clicks = clicks - generators[0].price;
        generators[0].quantity++; // This increases 'quantity' by 1
        update();
    }
}
```

By using `generators[0].price` and `generators[0].power`, you're telling the code to refer to the `price` and `power` characteristics of the Auto Clicker, rather than repeating ourselves constantly.

### Step 4

Typically, in idle games, the more you purchase a generator, the more expensive it gets. The best way to do this is to create a function that will tell you the price of a generator. To do that, add this to your `scripts.js` file:

```js
function price(generator) { 
    return Math.pow(generator.price, 1 + (0.1 * generator.quantity))
}
```

This function has a parameter that has been named `generator`. To use it, you would do something like `price(generators[0])`. Your `buyAutoClicker()` function can be changed to use it like below, subsituting `generators[0].price` for `price(generators[0])`.

```JS
function buyAutoClicker() {
    if (clicks >= price(generators[0]) {
    	clicksPerSecond = clicksPerSecond + generators[0].power;
        clicks = clicks - price(generators[0];
        generators[0].quantity++; // This increases 'quantity' by 1
        update();
    }
}
```

### Step 5

See if you can make another new generator, a `Super Clicker` perhaps. To do this, you'll need to do the following:

Firstly, add a new generator to the `generators` list, like so:

```JS
var generators = [
    new Generator('Auto Clicker', 10, 1),
    new Generator('Super Clicker', 100, 10),
];
```

(Feel free to set your own values for these)

Then, using what you learned from the previous steps you've learned:

1. Make a new function similar to `buyAutoClicker()` but using the new generator (`generators[1]`) instead of the first one (`generators[0]`).
2. Make a new button in the `index.html` file, similar to what you did for `buyAutoClicker()`, but instead it should call the new function you just made.
3. Clicking the button should increase your `clicksPerSecond` by the 'power' of the new generator.

## Chapter 4

TODO: Max's

## Chapter 5 - Extensions

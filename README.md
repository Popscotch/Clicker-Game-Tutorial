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

---

## Chapter 1 - Game time!

In this chapter we will focus on using HTML and JavaScript to create a stand-alone "clicker" game. Later chapters will walk you through adding additional functionalities to this game!

### Step 1 - First things first
Firstly, before we start, you need to understand the file structure. All code will be located in the `/src` folder. The folder has 3 files, `index.html` - the HTML file, `styles.css` - the CSS file and `scripts.js` - the JavaScript file. In this chapter we will be only touching `index.html` and `scripts.js` files.

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

There are 2 ways to declare a variable in JavaScript. One way is to use `var` and another is to use `let`. There are a few differences between then, but for the purpose of this chapter we will just be using `let`.

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

Refresh the page and see. Can you see the number updating on the page?

---

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
    document.getElementById("clickNum").innerHTML = clicks;
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

---

## Chapter 3 - More generators

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

By using `generators[0].price` and `generators[0].power`, you're telling the code to refer to the `price` and `power` characteristics of the Auto Clicker, rather than repeating the values.

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

Now you should have the foundations of a clicker game!

---

## Chapter 4 - Styling your Website and Game

Now that we've got our game working, it's time to make it look better. To do this we're going to revisit our styles.css sheet, which tells our browser how each element of our HTML page should be displayed.

### Step 1
To get us started, copy the below code into the file labelled 'styles.css'. 
```CSS
html {
    font-family: "Comic Sans", "Comic Sans", cursive;
    font-weight: bold;
    font-size: large;
}
h1 {
    text-align: center;
}
.clicker {
    font-size: 128px;
    display: block;
    margin: auto;
}
.clicks {
    text-align: center;
}
.clicksPerSecond {
    text-align: center;
}
.generators {
    /* display: block; */
    /* margin: auto; */
    text-align: center;
}
```

Some of the quickest ways you can personalise your website is by changing how the writing looks, so let's update the font style and add some color. 
 
You might have noticed that in the styles page we gave you there's a section of code that looks like this:

```css
html {
    font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
}
```
	
This piece of code tells the html page which fonts to use. Let's try changing the font-family to something different by typing in the name of a font you want to use.  If you want to use a specific font like Comic sans, you just put the name of the font in twice.
We can also add the 'font-weight' property which says how thick the individual text is typed on the webpage, or the 'font-size' property which determines how large the text will be on the page.   Your code should now look something like this:

```css
html {
    font-family: "Comic Sans", "Comic Sans", cursive;
    font-weight: bold;
    font-size: large;
}
```

Don't forget to refresh your webpage every time you make a change so you can see what it looks like!

Looking a little better, but this page could really use some colour. 
 
To make our text something other than a basic black, we need to add the 'color' property in the html section.  Warning!  VS Code uses the american spelling of 'color' so be sure to double check that.
 
 There are four ways to specify what colour you want:
- Name: color: red
- RGB: color: rgb(255,0,0);
- HSL: color: hsl(0,100%, 50%);
- HEX: color: #ff0000;
 
 A list of colours can be found at: https://www.w3schools.com/css/css_colors.asp
 
 ```css
html {
    font-family: "Comic Sans", "Comic Sans", cursive;
    font-weight: bold;
    font-size: large;
    color: blue;
}
```

That clicker button in the middle could also use some colour!  Only this time we need to change the 'background-color' of the button. 
 
Your code should look like this:
```css
.clicker {
    font-size: 128px;
    display: block;
    margin: auto;
    background-color: rgb(255, 99, 71);
}
```

Don't forget to refresh your browser so you can see the changes you've made!

---

## Chapter 5 - Extensions

### Step 1 - Save and Load game
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


### Step 2 - Intoduction to GIT & GitHub

If you are interested in programming/software development lifecycle, then you have most likely heard about GIT at some point. GIT is a version controll system that allows you to easily see the changes done in the code, by whom and when. It gives you the ability to review changes before you merge them to your final product and revoke those changes with ease if they break anything.

Some smart people already wrote a lot of tutorials on what GIT is and on how to use it. You can find a few of them below:
* [Into to GIT](https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners)
* [Git handbook](https://guides.github.com/introduction/git-handbook/)

Basically the steps for working with a repository are:
1. Create repository (essentially a folder for your code). You can use either GitHub or Bitbucket for this.
2. Clone this repository to your local machine. 
To do so, you can run the bellow command. You would need a [git client](https://git-scm.com/downloads) for this! 
```cmd
git clone <url-to-repo>
```
3. Make changes to your files or create new files.
4. Go back to GIT and type the following command. This command will show a diff between the files.
```cmd
git status
```
5. To mark files for submission ("stage" files), all you have to do is `git add .` (the `.` is to add changed/updated all files in the current directory)
6. After you have "staged" your files, we can now commit them - this will push the files to your local git repository instance. To do so, run the following:
```cmd
git commit -m "your message here"
```
7. Now that you commited your changes to your local repository, you can push the changes to GitHub/Bitbucket repository. To do so run the following command:
```cmd
git push
```
8. All done! Now you should see your changes on GitHub/Bucket.


> TIP: If you dislike using a command line, there is a really cool Git App - [SourceTree](https://www.sourcetreeapp.com/)!

Let us know if you need help :)

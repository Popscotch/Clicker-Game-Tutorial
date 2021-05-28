# Clicker-Game-Tutorial

Today we're going to run you through how to create a website and build your very own Clicker Game. 

In order to do this, we're going to use the HTML (Hyper Text Markup Language) and CSS (Cascading Style Sheet) languages to create your website.  Then we're going to build our game in JavaScript, which will make our game interactive. We'll also be introducing you to some tools used by professional programmers every day:  GitHub and Visual Studio Code. 

To get you started, we've provided you with three files to begin working on your game website. 

Before we can get started coding, we'll to need set up the files that we'll be working with on this computer. And if you want to take your work home with you at the end of today, don't worry - we've got a section on that later.


Let's begin by downloading the files we need from GitHub.  They have been put in something called a Git repository, which can be found here:
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

 All code will be located in the `/src` folder. Expand it now, and we'll see that this folder contains 3 files: `index.html` - the HTML file, `styles.css` - the CSS file and `scripts.js` - the JavaScript file. 


, the first of which is the HTML file called `index.html`.  Click on it in the explorer to open the file.

---

## Chapter 1 - Game time!

In this chapter we'll focus on using HTML and JavaScript to create a stand-alone "clicker" game. Later chapters will walk you through adding additional functionalities to this game!

### Step 1 - First things first
In order to see what each piece of code we write does, we need to open our webpage in a browser like Google Chrome or Microsoft Edge. So let's start by opening the 'index.html' file from the folder we saved to our desktop in the section above. 

Now open VS code back up and click on the `index.html` file from the `/src` folder to open it. We also need to do the same with the `scripts.js` file. 

These files are where we'll be writing our code in this chapter. 

### Step 2 - `let` the fun begin!

The point of the "clicker" game is to have a button which you can click to start with, so lets make one!

In the `index.html` file, let's create a button below the  `<h1>My Clicker Game</h1>` tag using this code:
```html 
<button class="clicker" onClick="clicker()">🖱️</button>
```

Refresh your page in the browser and you should see a button with a computer-mouse emoji in it.

> NOTE: Clicking on that button will do nothing yet and produce an error in the console (for now at least). We will fix this later!

To get that button do something, we can bind an `onClick()` event to it. The `onClick` event will be triggered every time the button is clicked! As you can see, we already done the 'binding' for you, that's the `onClick="clicker()"` part. Here we're binding the `clicker()` function to be triggered every time the button is clicked. This function will have to be declared in JavaScript.

### Step 3 - The JavaScript world
Next, we'll move to the `scripts.js` file.

> HINT: You can use `console.log()` to dump anything to browser console. Press F12 and select "Console" tab to see the dump.

There are 2 ways to declare a variable in JavaScript. One way is to use `var` and another is to use `let`. There are a few differences between them, but for the purpose of this chapter we will just be using `let`.

Before we create the `clicker()` function, let's create a variable to track the number of clicks we've made. To make it easy, let's call this variable `clicks`.
```js
let clicks = 0;
```
*Places it at the very top of the file!*

Now we can make the `clicker()` function to handle the button clicks.

```js
function clicker() {
    clicks = clicks + 1; // increments the global `clicks` variable by 1
    console.log("Clicks: " + clicks);
}
```
*Can you see the number of clicks increasing in the console? If not, then you've made a mistake. Reach out to a demonstrator for help!*

### Step 4 - Back to HTML
Seeing the number of clicks increasing in the console is cool and everything BUT how about on the page?

Let's make a counter field in our HTML file and get it to update, shall we?

Add the following code in your file above the `<button>` code:
```html
<p class="clicks"><span id="clickNum">0</span> clicks</p>
```

*The number still won't update because we're not telling the JavaScript to update it!*

### Step 5 - Back to JavaScript

Let's create an `update()` function which will update the HTML DOM accordingly!

```js
function update(){
    document.getElementById("clickNum").innerHTML = clicks
}
```

Now, we should call this function every time the button is clicked, remember the `clicker()` function?

Update the `clicker()` function so it looks like the following:

```js
function clicker() {
    clicks = clicks + 1; // increment the global `clicks` variable by 1
    update();
    console.log("Clicks: " + clicks);
}
```

Now refresh the webpage in your browser and try clicking on the button again. Can you see the number updating on the page?

---

## Chapter 2 - Generating more clicks!

Now that you have a button that can increase your 'clicks'. It's time to make something that can help us generate clicks over time without having to trigger ourselves, an "Auto Clicker"!

### Step 1

In the `scripts.js` file, below `let clicks = 0;`, add a new variable that keeps track of our `clicksPerSecond` like so:

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

This will just look like a single line of text when you view your page, but this way you can use JavaScript to change the `<span>` specifically, rather than the entire line.

### Step 3

You've made the button, and told it to do `buyAutoClicker()` when it is clicked with the `onClick` attribute. But you still need to define what `buyAutoClicker()` really does. To do this, go into your `scripts.js` file, and start with adding this at the bottom of the file:

```JS
function buyAutoClicker() {
    // Code goes here
}
```

Whenever that button is pressed, the code within the curly brackets of this function will be executed. The goal is to increase `clicksPerSecond` so that value can be used to increase `clicks`. Also include the `update()` function, it will be helpful for later for updating the text on the page itself.

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
        clicks = clicks - 10;
        update();
    }
}
```

### Step 4

Next, let's change the `update()` function to update the page when the `clicksPerSecond` value changes. Like before, you need to set the innerHTML of the `Clicks per second` line whenever something changes. 

When you're done, your `update()` function should look like this:
```JS
function update() {
    document.getElementById("clickNum").innerHTML = clicks;
    document.getElementById("clicksPerSecond").innerHTML = clicksPerSecond;
}
```

### Step 5

Now the `clicksPerSecond` value still doesn't actually do anything yet, you first need to add some functionality to allow it to increase our clicks over time, and you also want to see this happening visually without having to do anything.

This is possible using the `setInterval` function.

First, make an `init` function. There's nothing special about the word `init`, it's usually a term reserved for functions that are executed when the page loads up.

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

Whenever the page is loaded, the `init` will execute, and any code inside will be executed. We want to define what should happen every interval (Seconds, milliseconds, etc) when the page is opened. We we will use a `setInterval` function to tell the page to increase `clicks` by `clicksPerSecond` every 1000 milliseconds (1 second).

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

The general idea of clicker games, is for you to purchase generators to produce more resources. Using these resources you can then purchase even more generators that produce  more resources etc. It's a game about exponential growth.

We're going to generalise our Auto Clicker using a `class`, and create some functions so our game is more dynamic.

### Step 1

Let's define a 'generator' class. This is what represents a generator, and we'll use this class to make more generators.

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
let generators = [
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

This function has a parameter that has been named `generator`. To use it, you would do something like `price(generators[0])`. Your `buyAutoClicker()` function can be changed to use it like below, substituting `generators[0].price` for `price(generators[0])`.

```JS
function buyAutoClicker() {
    if (clicks >= price(generators[0])) {
    	clicksPerSecond = clicksPerSecond + generators[0].power;
        clicks = clicks - price(generators[0]);
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
For saving the game, we will utilise Internet Browser's Local Storage mechanism.

**Local Storage** - (some times also called DOM Storage) provides functionality for saving data on the client-side (within the browser). This means that you can save data in one tab and have access to it in another or even after you refresh the page!

Sounds cool right? Let's try it out :)

Firstly, let's create 3 new buttons in our `index.html` page. A button to Save, Load and Clear.

Add the following anywhere within the `<body>` tags:
```html
<button onClick="save()">Save</button>
<button onClick="load()">Load</button>
<button onClick="clearClicks()">Clear</button>
```

Let's create `save()`, `load()` and `clearClicks()` functions to call when the Save, Load and Clear buttons are clicked.
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


### Step 2 - Introduction to Git & GitHub

If you are interested in programming/software development life-cycle, then you have most likely heard about Git at some point. Git is a version control system that allows you to easily see the changes made to code, by whom and when. It gives you an ability to review changes before they are merged into the final product and revoke those changes with ease if they break something.

Some smart people already wrote a lot of tutorials on what Git is and on how to use it. You can find a few of them below:
* [An Intro to Git and GitHub for Beginners (Tutorial)](https://product.hubspot.com/blog/git-and-github-tutorial-for-beginners)
* [Git handbook](https://guides.github.com/introduction/git-handbook/)

Basically the steps for working with a repository are:
1. Create a repository (essentially a folder for your code) if you do not already have one. You can either use GitHub or Bitbucket for this.
2. Clone this repository to your local computer. 
To do so, you can run the bellow command in command line (you would need a [git client](https://git-scm.com/downloads) for this!).
```cmd
git clone <url-to-repo>
```
3. Make changes to your files or create new files.
4. Go back to command line and type the following command. This command will show a difference between the files.
```cmd
git status
```
5. To mark files for submission (to "stage" files), all you have to do is type `git add .` (the `.` is to add all changed/updated files in the current directory) to Git for tracking.
6. After you have staged your files, we can now commit them. This will push/upload the files to your local repository instance (the files will not be uploaded to GitHub/Bitbucket repository just yet). To do so, run the following command:
```cmd
git commit -m "your message here describing your change"
```
7. Now that you committed your changes to your local repository, you can push the changes to GitHub/Bitbucket repository. To do so run the following command:
```cmd
git push
```
8. All done! You should now see your changes on GitHub/Bucket.


> TIP: If you dislike using a command line, there is a really good Git Application called [SourceTree](https://www.sourcetreeapp.com/)!

Let us know if you need help :)

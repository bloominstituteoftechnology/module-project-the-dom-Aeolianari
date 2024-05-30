# Sprint 5 Module 1 Project

## Introduction

Welcome to the Sprint 5 Module 1 Project! In this project, you will practice using "vanilla" JavaScript to manipulate the DOM, without any frameworks. Your goal is to build some widgets on a webpage using only JavaScript.

To complete this project, you will need to do the following:

1. **Select elements** and groups of elements from the DOM.
1. **Create new elements** and attach them to the DOM.
1. **Loop** over arrays and lists of DOM elements.
1. **Generate pseudo-random numbers** using the Math object.
1. **Use data** and template literals to build text content for elements in the DOM.
1. **Manipulate attributes** on elements.
1. **Use setInterval** to schedule repeated actions.

In addition to these technical skills, the following soft skills will significantly impact your performance:

1. Attention to detail. Make sure there isn't a single character out of place!
1. Perseverance. Keep trying until you figure it out!
1. Patience. Make sure to read the entire README for important information.

## Instructions

You have received a take-home coding assessment for a front-end Web Developer position as part of the hiring process. Your task is to build widgets on a webpage using only JavaScript.

You can find a detailed mock [HERE](https://bloominstituteoftechnology.github.io/W_U2_S5M1_module_project/) showing the desired final result.

### 💾 Setup

**Here are the steps to set up this project:**

1. **Clone this repository** to your computer, allowing you to run the software locally for development and testing purposes.

1. Within your terminal, navigate to the project folder **and execute `npm install`**.

1. After successful installation, open two terminal windows at the project folder and **execute `npm start` in your first terminal and `npm test` in your second**.

1. You will load the app in Chrome by **navigating the browser to `http://localhost:3003`**.

1. If you haven't already, install the [Eslint extension](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint) for VSCode.

### 🥷 Tasks

**Here are guidelines for completing your tasks:**

- If you look inside the `frontend` folder you will notice it contains, among other assets, two scripts: `data.js` and `index.js`. If you inspect the head element of the `index.html` document, you will find both scripts being loaded there.

- A single page can load many scripts, and whatever variables exist at the top level of each script are accessible by any scripts executing later. In this case, we include `data.js` first because we want the data it contains to be available to the `index.js` script.

- You will complete your tasks inside the `frontend/index.js` script. Do not modify any other files. Detailed instructions for each task can be found below.

- As you make progress, the behavior of the website will start matching that of the [mock](https://bloominstituteoftechnology.github.io/W_U2_S5M1_module_project/).

- As you complete your tasks, tests will start passing in the terminal. Keep going until all tests are in the green!

- Have fun, and check out the Solution Video for this project if you need help!

**WARNING**

❗ Most of the following tasks involve setting text in the DOM using JavaScript. Please, do not use the `innerText` property of elements to set text! The `textContent` prop should be used instead. The reason is that `innerText` doesn't work in the tests. Read about the differences between the two properties [HERE](https://stackoverflow.com/a/35213639).

#### 👉 TASK 1 - Add a "widget" class name to widgets so CSS kicks in

<details>
  <summary>Click to read</summary>

  ---

Inside the section element of the `index.html` file, you will find four divs. Add a class name of "widget" to all of them. Remember, you're only allowed to change the `index.js` file.

You will know your code is working correctly because some CSS will kick in for the widgets, and you will also see a passing test inside the terminal executing your tests. The end result in the DOM should look like the following:

```html
<section>
  <div class="quoteoftheday widget">
    <h3>Quote of the Day</h3>
  </div>
  <div class="corporatespeak widget">
    <h3>Corporate Speak</h3>
  </div>
  <div class="countdown widget">
    <h3>Countdown</h3>
  </div>
  <div class="friends widget">
    <h3>Friends</h3>
  </div>
</section>
```

  ---

</details>

#### 👉 TASK 2 - Build a "Quote of the Day" widget

<details>
  <summary>Click to read</summary>

  ---

Start by console logging the variable `quotes` inside of `index.js`. You should see an array of quote objects printing to the console. Even though this variable is not declared anywhere inside the file, it is _defined_ because the `data.js` script loaded it into the global space shared by all scripts.

(You can also evaluate top-level variables by entering them into the console and hitting Enter.)

Now that we have determined we can access the array of quotes, you will use `Math.random` to generate a random index **between 0 and 9** (you can Google or ask ChatGPT how). You will use this random index to grab one of the quotes in the quotes array.

Use the random quote you selected to add to the quoteoftheday div the following piece of DOM:

```html
<!-- the actual text will change at every reload, depending on the quote -->
<div class="quoteoftheday widget">
  <h3>Quote of the Day</h3>
  <div>Optimism is an occupational hazard of programming: feedback is the treatment.</div>
  <div>Kent Beck in 2003</div>
</div>
```

Some quotes have a `null` date because it is unknown. In such cases, the div containing the author should be in the following format:

```html
<!-- the name will change depending on the quote -->
<div>John Romero in an unknown date</div>
```

  ---

</details>

#### 👉 TASK 3 - Build a "Corporate Speak" widget

<details>
  <summary>Click to read</summary>

  ---

Using random values from the arrays `adverbs`, `nouns`, and `verbs` contained in `data.js`, add to the DOM inside the corportatespeak div in the following format:

```html
<div class="corporatespeak widget">
  <h3>Corporate Speak</h3>
  <p>
    We need to <!-- random verb --> our <!-- random noun --> <!-- random adverb -->
    in order to <!-- random verb --> our <!-- random noun --> <!-- random adverb -->.
  </p>
</div>
```

The text should change at each page load/refresh.

  ---

</details>

#### 👉 TASK 4 - Build a "Countdown" widget

<details>
  <summary>Click to read</summary>

  ---
This widget will contain text that will countdown to liftoff. Each second, the widget's text will change to show the following:

- The widget will display "T-minus 5..." on page load.
- 1000 milliseconds later, it should display  "T-minus 4..."
- 1000 milliseconds later, it should display  "T-minus 3..."
- 1000 milliseconds later, it should display  "T-minus 2..."
- 1000 milliseconds later, it should display  "T-minus 1..."
- 1000 milliseconds later, it should display  "Liftoff! 🚀"

You will need `setInterval` and optionally `clearInterval` (research this!). The countdown div in the DOM after 3000 milliseconds should look like so:

```html
<div class="countdown widget">
  <h3>Countdown</h3>
  <p>T-minus 2...</p>
</div>
```

  ---

</details>

#### 👉 TASK 5 - Build a "Friends" widget

<details>
  <summary>Click to read</summary>

  ---
This widget will show a random person from the `people` array along with some data related to the person.

Start by selecting a random person from the `people` array in `data.js` using `Math.random`.

Each person has, among other attributes, a `friends` array containing the IDs of some buddies, who also happen to be persons inside the `people` array.

Use the random person to construct the inside of the friends div in the following format:

```html
<div class="friends widget">
  <h3>Friends</h3>
  <p>Michael Chen was born in 1995 and is friends with Carlos Garcia, Mohammed Ali and Jason Wong.</p>
</div>
```

Note how the string is formatted, taking careful note of punctuation and proper placement of the "and" before the last friend.

The friends mentioned in the p tag come from the `friends` property of the randomly selected person.

In the example above, Carlos Garcia, Mohammed Ali, and Jason Wong are the people who correspond to the IDs inside Michael Chen's `friends` array.

If the person is unlucky enough not to have any friends inside their `friends` property, the paragraph renders to the DOM like so:

```html
<p>Luis Gonzalez was born in 1990 and has no friends.</p>
```

  ---

</details>

#### 👉 Task 6 Add tab indices to widgets

<details>
  <summary>Click to read</summary>

  ---

We need to be able to tab between widgets using the Tab key, which helps make the site more accessible.

To do this, select the first widget from the DOM and add a `tabindex` attribute of "1".

The second one should have a `tabindex` of "2" and so on. Here is what the Countdown widget would look like as an example:

```html
<div class="countdown widget" tabindex="3">
  <h3>Countdown</h3>
  <p>Liftoff! 🚀</p>
</div>
```

  ---

</details>

## FAQ

<details>
  <summary>I feel very stuck. What can I do?</summary>

Check out the Solution Video for this project in your learning platform. In it, an industry expert will walk you through their thinking in detail while they solve the tasks. We highly recommend the Solution even if you are not stuck. You will learn lots of tricks.

</details>

<details>
  <summary>I am getting errors when I run npm install or npm start. What is going on?</summary>

This project requires Node to be correctly installed on your computer to work. Your learning materials should have covered the installation of Node. Sometimes Node can be installed but misconfigured. You can try executing `npm run fixit` (check `package.json` to see what this does), but if Node errors are recurrent, it indicates something is wrong with your machine or configuration, and you should request assistance from a learner assistant.

</details>

<details>
  <summary>Do I need to install libraries or add scripts to the HTML?</summary>

No. Everything you need should be installed already.

</details>

<details>
  <summary>Why am I not allowed to edit the CSS file?</summary>

The CSS is the domain of a different team, and in this particular project we're not supposed to touch it. Do not use inline styles to get around this limitation.

</details>

<details>
  <summary>Why am I not allowed to edit the HTML file?</summary>

This part of the product is a Single Page Application, so the HTML is mostly empty, and the page is automatically generated using JavaScript and raw data. We would not want to manually edit HTML files in a website that changed all the time! It would be untenable.

</details>

<details>
  <summary>My page does not work! How do I debug it?</summary>

Save your changes, and reload the site in Chrome. If your code has a syntax problem, the app will print error messages in the console. Focus on the first message. Place console logs right before the crash site (errors usually inform of the line number where the problem originates) and see if your variables contain the data you think they do.

Suppose there are no errors, but the page is not doing what it should. In that case, the debugging technique is similar: put console logs to ensure that the code you are working on is executing and check that all variables in the area hold the correct data.

</details>

<details>
  <summary>How do I run tests against my code?</summary>

Execute `npm test` in your terminal. If a particular test is giving you grief, don't jump straight to the code to try and fix it. Go to Chrome first, and make sure you can replicate the problem there. A problem we can reliably replicate is a problem mostly fixed.

</details>

<details>
  <summary>I believe my code is correct and the test is wrong. What do I do?</summary>

On occasion the test runner will get stuck. Use CTRL-C to kill the tests, and then `npm test` to launch them again. Try to reproduce the problem the test is complaining about by interacting with the site in Chrome, and do not code "to make the test happy". Code so that **your app does exactly what the mock does**. The tests are there for confirmation. Although it's possible that a particular test be flawed, statistically it's more likely that the bug is in your own code. If the problem persists, please request assistance from Staff.

</details>

<details>
  <summary>The output of the test script is just too overwhelming! What can I do?</summary>

If you need to disable all tests except the one you are focusing on, edit the `mvp.test.js` file and, as an example, change `test('👉 focus on this', () => { etc })` to be `test.only('👉 focus on this', () => { etc })`. (Note the "only".)

</details>

<details>
  <summary>I messed up and want to start over! How do I do that?</summary>

**Do NOT delete your repository from GitHub!** Instead, commit _frequently_ as you work. Make a commit whenever you achieve _anything_ and the app isn't crashing in Chrome. This in practice creates restore points you can use should you wreak havoc with your app. If you find yourself in a mess, use `git reset --hard` to simply discard all changes to your code since your last commit. If you are dead-set on restarting the challenge from scratch, you can do this with Git as well, but it is advised that you request assistance from a learner assistant.

</details>

<details>
  <summary>Why are there so many files in this project?</summary>

Although a small, "old-fashioned" website might be made of just HTML, CSS and JS files, these days we mostly manage projects with Node and its package manager, NPM. Node apps typically have a `package.json` file and several other configuration files placed at the root of the project. This project also includes automated tests and a web server, which adds a little bit of extra complexity and files.

</details>

<details>
  <summary>Is this how web projects are normally organized?</summary>

Web projects can be organized in many ways and there aren't many standards. Some developers like the freedom, while others prefer to use opinionated frameworks, which can do a lot of magic but require folders and files be structured and named just so.

</details>

<details>
  <summary>Why is my code inside index.js wrapped in a function?</summary>

This way we can easily import your code as a single function in the `mvp.test.js` test suite. The export syntax is at the bottom of `index.js`.

</details>

<details>
  <summary>What are the package.json and package-lock.json files?</summary>

The `package.json` file contains meta-information about the project like its version number, scripts that the developer can execute, and a list of the dependencies that are downloaded when you execute `npm install`. There can be some wiggle room to allow newer versions of the dependencies to be installed, so the `package-lock.json` file, when present, makes sure the exact same versions of everything are used every time the project is installed from scratch.

</details>

<details>
  <summary>What is the "start" script in the package.json doing? It looks confusing.</summary>

Give ChatGPT the following input for a detailed breakdown:

```txt
Hello, I'm looking at a JavaScript project on GitHub, and inside the package.json file I am seeing the following "script":

"start": "fkill :3003 -f -s && node ./backend/server.js"

Can you explain in detail, but with simple terms, to an audience of inexperienced web developers, what the "start" script is doing?
```

</details>

<details>
  <summary>What is the .eslintrc.js file?</summary>

This file works in combination with the Eslint extension for VSCode to highlight syntax errors and problems in your code. By editing this file you can customize your linting rules.

</details>

<details>
  <summary>What is Jest?</summary>

Jest is a framework that allows you to write tests and execute them, to alert you very quickly of problems with the code. Jest can do in seconds what an entire Quality Assurance team would take hours or even days. In the context of the Sprint Challenge, Jest is used to check your code against specification and give you a grade (% of tests passing).

</details>

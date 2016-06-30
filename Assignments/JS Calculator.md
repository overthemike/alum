## You Should Know
- HTML
- CSS Layout
- Javascript Fundamentals
- jQuery Fundamentals

## Your Mission
Now that you're familiar with all the building blocks of a functional web application, let's build something we can really use - a calculator!

### Explore Mode

**Challenge #1.1:** Use your knowledge of HTML to create a simple calculator interface. It should contain three text inputs (`#num_one`, `#num_two`, and `#answer`) and four buttons (`#add`, `#subtract`, `#multiply`, `#divide`). Place your HMTL in a file called `index.html`, and add some CSS styling in a file called `styles.css`.
**Goal #1.1:** A simple calculator interface for working with 2 numbers.

**Challenge #1.2:** Once you're happy with the appearance of your calculator, let's make it work. In a file named `main.js`, use jQuery's DOM manipulation methods to link the elements on the page so when a user inserts a number in each input and clicks one of the operand buttons, the result of those numbers & that operand are displayed in `#answer`. For example, if I type "1" into `#num_one` and "2" into `#num_two`, and click on the `#add` button, `#answer` should display "3". Be sure to link your Javascript file to your HTML!
**Goal #1.2:** A Javascript file using jquery for our calculator logic.

**Challenge #1.3:** It's always good to use source control with our projects. Create a git repository, commit your work and add your repo to Github.
**Goal #1.3:** Submit your Github URL below.

### Adventure Mode

**Challenge #2.1:** Let's upgrade to a more familiar interface. Refactor your HTML & CSS to imitate the image below. Replace your `#num_one` and `#num_two` fields with a single `#num_input` field, and give each number field an id matching its number (`#one, #two, #three`, etc). Include an `#equals` and `#clear` button, and try to add some CSS transitions to make the process more interactive for users.
![Calculator mockup](https://raw.githubusercontent.com/tiy-lv-frontend-2016-06/jquery-calculator/master/calculator.png)

**Goal #2.1:** A redesigned calculator interface.

**Challenge #2.2:** With an updated interface comes updated logic! Refactor your `main.js` to work with the new interface. Calculations should only be performed after clicking `#equals`, and results should be shown in your `#num_input` field. For this challenge, it's okay to only support two-number expressions (`10+3`, `25/5`, etc). Don't forget to update your Github respository before submitting!
**Goal #2.2:** Updated logic using jQuery for a new calculator workflow.

### Epic Mode

**Challenge #3.1:** Refactor your Javascript to support any expression length. It's okay to not calculate until `#equals` is clicked, but be sure your final result handles the entire expression in your input!
**Goal #3.1:** Refactored Javascript using jQuery for advanced calculator functionality.

## Requirements for Completion
- A Github repository containing:
  - `index.html`
  - `styles.css`
  - `main.js`

## You May Need
- [Calculator Mockup](https://raw.githubusercontent.com/tiy-lv-frontend-2016-06/jquery-calculator/master/calculator.gif)

## User Input

At some point, you're going to want to accept input from your users on a web page. So far we've only covered elements that allow you to share content, but how can we accept content from others? Thankfully, HTML offers us some great interfaces for dealing with user input. We use "forms" in HTML to accept input.[^1] A "form" is an HTML `form` element with various input elements for accepting different types of data. Let's take a look at the types of elements we have access to for creating a dialog with our web page visitors. 

## The Form Element

The most important part of any HTML form is, of course, the `form` element. `form` requires two attributes: an `action` and a `method`. `action` refers to the location this form should send its data to. This will usually be an external script set up to process that data and redirect the user. `method` refers to the HTTP method used to transmit the form data. You'll set this attribute to "GET" for short public data (like a search form) and "POST" for everything else. We'll discuss HTTP methods in more detail in a future lesson.

Here's a simple empty form:

```html
<form action="get-user-login.php" method="POST">
</form>
```

This example form element will send its data to the "get-user-login.php" script via the POST method. But what data will it send? Well...nothing - yet! To submit data, we need to add some HTML elements designed for accepting user input. When added to our form, we call these elements "fields". Let's look at our field options so we can add some data to our example form. 

## Input Elements

HTML offers a ton of different options for handling user input. We'll cover just the most common ones here to get you started, but you'll find a lot more flexibility when you start exploring on your own. [^2]

### Input

The input element is the most commonly-used form element in HTML. How an input element renders on your web page is mostly determined by the value of the element's `type` attribute. Since these are our primary elements for forms, let's look at the types available for the most often-used data:

- `type="text"`: This element will render as a single-line text box. It's great for most short-form text input, include names, addresses and question responses.
- `type="checkbox"`: This element will render a checkbox on the page. Users can click on the checkbox to select or deselect it. Make sure to add a label so users know what it's for!
- `type="file"`: This allows for files to be uploaded by your users. This might seem complicated, but at some point you'll want users to be able to submit screenshots or profile pictures to a website. 
- `type="hidden"`: Hidden fields are a bit of a confusion point for new developers, but they're common on larger websites and very useful for sharing metadata from your form. Hidden fields won't show up on your web page at all, but they're visible in your code and can hold anything from the current web page's name to an automatically-generated timestamp. Remember that "hidden" here just means "not visible", *NOT* "secure", "private", or "encrypted". You should never use a hidden field to send sensitive information. 
- `type="password"`: Password fields look like a regular text input field, but replace characters typed into them with asterices or dots. You're probably familiar with these from websites where your password isn't visible as you type it. Like hidden fields, password fields aren't particularly secure. They will keep people from reading over your shoulder, though.  
- `type="radio"`: "Radio buttons", created by this input type, are similar to checkboxes but allow only one item from a group to be selected. You'll need the `value` attribute to indicate what value should be associated with each radio button and the `name` attribute to associate each radio input with a group. 

The input element is a void element and doesn't use a closing tag. 

#### Forms Using Input Only
###### Follow through a few forms on live websites that use only input elements to gather data.
!video qeeg0ubf7u

## Non-Input Elements

There are a few common situations that the `input` element doesn't provide a suitable type for. For these, we have dedicated elements available. Let's look at the most common ones. 

- `textarea`: The `textarea` provides a larger input field for multi-line or extended text input. Where `<input type="text">` is great for a single word or short sentence, `textarea` is great for paragraphs of prose or extended explanations. `textarea`, confusingly, is NOT a void element: it requires both an opening and closing tag. Any text content you add to this element will be used as a default value. 
- `select` & `option`: The `select` element creates what's commonly known as a "dropdown field". `select` acts as the wrapper element and each `option` inside creates a new selection you can choose from the dropdown. Each `option`'s content will be shown in the select field, and this will be the default value, but you can use the `value` attribute to override this. For example: if you want your dropdown box to include "Red", "Blue", and "Green", but you want your form to submit these values as "R", "B", or "G", your select element would look like the following:
``html
<select>
  <option value="R">Red</option>
  <option value="B">Blue</option>
  <option value="G">Green</option>
</select>
```
- `button`: There's really only one button you'll use for HTML forms: `<button type="submit">Submit</button>`. This is how we create a button to submit our form. Buttons are standard elements that require both an opening and closing tag. The text content of your button element is what will show up on the button when it's rendered on your web page and can be anything - just make sure it makes sense so your users know what the button is doing!

## Making Sense Of Your Form

There are a couple commonly-used elements that can help users understand your form better:

- `label`: The label element creates a simple text label for your form elements. Without a label, users will have difficulty understanding where their content goes. It's a good idea to use a label's `for` attribute to associate the label with a form field - you do this by setting the `for` attribute to the `id` attribute of the field you'd like to associate.
- `fieldset` & `legend`: Fieldsets are logical groups of form elements. You've seen these frequently when filling out forms online - Your personal information may be inside one fieldset, while your payment info may be inside another. Fieldsets use the `legend` element to add a short caption. The legend element should be the first element inside a fieldset. 

## Default Form Behavior

Forms are commonly manipulated by Javascript to perform extra tasks (like formatting phone numbers or checking password requirements) but sometimes you just want a simple form without the added overhead. What happens when a form is submitted on an HTML webpage with no other scripts involved? 

The form first groups all the data in each field into a group of key-value pairs called the "form data set"[^3]. In each case, the "key" will be the `name` attribute of the field (which is mandatory for ALL field elements) and the "value" will be the data from that field. That data is then sent, via the form's `method` attribute, to the location of the form's `action` attribute. The `action` destination will usually contain code that gathers that data, stores or manipulates it in some way, and returns a response confirming that data was recieved. If there are special response details needed (for example: a tracking number when you submit payment for a postage label) those details will be included in the "response" from the action. The form's action may also redirect your browser to another webpage. This is usually where you'll see confirmation numbers or error reports (if there was an error). A redirect is common but not mandatory - it's perfectly acceptable to send your form data to the web page you're currently on, as long as it's set up to handle that data. 

#### What Does Form Data Look Like?
###### We'll write a quick form and post it to a simple API where we can view the data that comes from our form in realtime.
!video mqkjr4kk1a

[^1]: Read more detail on forms at [Mozilla's HTML Form tutorial](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Forms/How_to_structure_an_HTML_form).
[^2]: You can see everything HTML forms have to offer at [Mozilla's HTML Form page](https://developer.mozilla.org/en-US/docs/Web/Guide/HTML/Forms).
[^3]: See this referenced in the [W3C HTML spec](http://www.w3.org/TR/html401/interact/forms.html#h-17.13).

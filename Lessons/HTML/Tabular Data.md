## Tabular Data

Data is one of the greatest things about the Internet. Everything can be measured, monitored and metered. It's new ways of visualizing and managing data that provides much of the impetus for development as a whole. Of course, computers understand data much more easily than humans. What do we do when we're presented with raw data that we'd like to present in a human-readable format? Thankfully, HTML provides a handful of helpful elements specifically intended to organize data. 

## Table and its subelements

The most intuitive of data-themed elements available in HTML is the `table` element. `table` accepts a number of child elements: `tr` (Table Row), `th` (Table Header), and `td` (Table Data).[^1] Let's look at a simple table:

```html
<table>
  <tr>  
    <th>Student</th>
    <th>Class</th>
    <th>Grade</th>
  </tr>
  <tr>
   <td>Studious Stephanie</td>
    <td>Frontend Engineering</td>
    <td>A++</td>
  </tr>
  <tr>
    <td>Average Alexandra</td>
    <td>Data Science</td>
    <td>C</td>
  </tr>
  <tr>
    <td>Lazy Lauren</td>
    <td>Backend Engineering</td>
    <td>F</td>
  </tr>
</table>
```

The first thing we can see is that even small tables require a large number of elements. This is good for displaying data, though - more elements means we have more opportunities to apply custom styles so our data is visually appealing. You can also see the basic structure of a table here: `th` elements should line the top of each column, while `td` elements are used to hold our data.[^1]

## Description Lists

Description list elements have been around for a long time, but have often been misunderstood and ignored.[^2] They're a fantastic tool to use for listing pairs of names and values. Description lists are a good practice as part of employing semantic HTML - we have other ways of making lists, but description elements are explicit about what type of list is being included. 

`dl` is the parent element of description lists. Pairs of names and values within your `dl` should be listed with `dt` (Description Title) and `dd` (Description Description) elements.[^3] These elements have a "many-to-many" relationship: multiple `dt`s can match a single `dd`, and you can associated a single `dt` with multiple `dd`s. 

Here's an example of a glossary implemented within a description list:

```html
<dl>
  <dt>HTML</dt>
  <dd>A markup language </dd>
  <dt>Element</dt>
  <dd>A logical unit defining an HTML object.</dd>
</dl>
```

## Using Tabular Elements For Layout

It used to be common practice for web pages to use tabular elements to provide page structure. Looking at a simple table, it makes sense why: tables provide a nested box structure similar to the Web's native style, and make it easy to say "I want content in this cell and this cell left blank". However, table-based webpages require many more elements and are much more difficult for other developers to interpret. Here's a comparison between the same simple web page layouts - one using `table`, one using semantic markup:

![Web Page Comparisons](https://s3-us-west-2.amazonaws.com/tiy-learn-lesson-assets/images/html/table-vs-semantic.png)

Thankfully, developers have moved away from this practice for a number of reasons. The most important reason is semantics. The `table` element and all its related subelements are intended for sharing data, not nudging content around a web page. HTML provides lots of helpful elements, like `div`, to create layout. There is no layout that can't be created using HTML layout elements, and both your visitors and you will have a better experience if you use the tools HTML provides in the appropriate manner. 

It's important to always think of intent and semantics when creating webpages. Using elements for unintended purposes can result in your web page being difficult to read for people on alternative browsers or using accessibility aids. It can even cause your page to be difficult to find on search engines - this is a major problem for any web page that relies on public views to generate revenue or share a product.[^4]


[^1]: You can read more about tables and some more sub elements available to them at [Mozilla's excellent `table` reference](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table).
[^2]: There's a [great discussion of definition lists at CSS-Tricks](https://css-tricks.com/utilizing-the-underused-but-semantically-awesome-definition-list/).
[^3]: http://www.w3.org/TR/html5/grouping-content.html#the-dt-element
[^4]: You can learn more about why you should always prefer semantic HTML, and how to structure your semantic HTML in a concise manner, from [this excellent Smashing Magazine article on tables vs. divs](http://www.smashingmagazine.com/2009/04/from-table-hell-to-div-hell/).
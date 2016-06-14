## You Should Know
- HTML
- CSS Layout

## Your Mission
Let's duplicate an image using a given HTML page, [`index.html`](https://github.com/theironyard/js-assignments/blob/master/HTML+CSS/html-intro-layout/index.html), and an inspiration image:
![Octocat Table](https://dl.dropboxusercontent.com/s/awfw9xqf1dpcn3c/octocat.png?dl=0)

### Explore Mode

**Challenge #1.1**: Copy our [index.html](https://github.com/theironyard/js-assignments/blob/master/HTML+CSS/html-intro-layout/index.html) and add your own CSS to make it look like the image above. Your CSS should be in a separate file called `styles.css`. 
**Goal #1.1**: Add a custom stylesheet to `index.html`.

**Challenge #1.2**: Make sure your project is safe! Create a git repository containing your project files and upload it to Github.
**Goal #1.2**: Submit your Github URL below.

### Adventure Mode

**Challenge #2.1:** Let's practice writing some custom HTML as well. Follow the pattern in `index.html` and add 3 more Octocats to your web page. Use the Octodex at [http://octodex.github.com](http://octodex.github.com) if you need some images, or draw your own and include them in your Github repository!
**Goal #2.1:** Submit your updated Github URL below.

### Epic Mode

**Challenge #3.1:** Try making your web page responsive when the browser is resized. Here's a hint: consider what CSS rules you know that determine how many items are displayed inline.
**Goal #3.1:** Submit your updated Github URL below. 

## Requirements for Completion
- A Github URL containing:
  - `index.html`
  - `styles.css`

## You Will Need
- A file called `index.html` with the following markup:
```
<!doctype html>
<html lang="en">
<head>
  <title>Octodex</title>
<!-- link to your stylesheet -->
</head>
<body>
<ul class="octodex">
  <li class="octocat">
    <a href="https://octodex.github.com/saritocat">
      <img src="https://octodex.github.com/images/saritocat.png" />
    </a>
    <div class="image-footer">
      <span class="image-number">114</span>
      <div class="image-caption">
        <span>the</span>
        <a href="https://octodex.github.com/saritocat">Saritocat</a>
        <span>by</span>
        <ul class="authors">
          <li>
            <a href="https://github.com/JohnCreek">
              <img src="https://github.com/JohnCreek.png" />
            </a>
          </li>
        </ul>
      </div> <!-- .image-caption -->
    </div> <!-- .image-footer -->
  </li>
  <li class="octocat">
    <a href="https://octodex.github.com/topguntocat">
      <img src="https://octodex.github.com/images/topguntocat.png" />
    </a>
    <div class="image-footer">
      <span class="image-number">113</span>
      <div class="image-caption">
        <span>the</span>
        <a href="https://octodex.github.com/topguntocat">Topguntocat</a>
        <span>by</span>
        <ul class="authors">
          <li>
            <a href="https://github.com/leereilly">
              <img src="https://github.com/leereilly.png" />
            </a>
            <a href="https://github.com/tonyjaramillo">
              <img src="https://github.com/tonyjaramillo.png" />
            </a>
          </li>
        </ul>
      </div> <!-- .image-caption -->
    </div> <!-- .image-footer -->
  </li>
  <li class="octocat">
    <a href="https://octodex.github.com/carlostocat">
      <img src="https://octodex.github.com/images/carlostocat.gif" />
    </a>
    <div class="image-footer">
      <span class="image-number">112</span>
      <div class="image-caption">
        <span>the</span>
        <a href="https://octodex.github.com/carlostocat">Carlostocat</a>
        <span>by</span>
        <ul class="authors">
          <li>
            <a href="https://github.com/jeejkang">
              <img src="https://github.com/jeejkang.png" />
            </a>
          </li>
        </ul>
      </div> <!-- .image-caption -->
    </div> <!-- .image-footer -->
  </li>
</ul>
</body>
</html>
```

- [Octocat Layout Image](https://dl.dropboxusercontent.com/s/awfw9xqf1dpcn3c/octocat.png?dl=0)
- [The Octodex](http://octodex.github.com)

# The HTML_CSS Learning Notes

## 2018-01-01

### **HTML Elements with Zero Height**

  Check this [Stack Overflow](https://stackoverflow.com/questions/5369954/why-is-my-divs-height-zero) link first.

  So the problem encountered in my project was that the `section` element "meals" and `ul` element "meals-showcase" were with zero height. Structure is as shown below.
  ``` html
  <section class="meals">
        <ul class="meals-showcase">
            <li>
                <figure class="meals-photo"><img></figure>
            </li>
        </ul>
  </section>
  ```
  CSS file looks like this:
  ```css
  .meals {
    padding: 0;
  }
  .meals-showcase {
      list-style: none;
      width: 100%;
  }

  .meals-showcase li {
      display: block;
      float: left;
      width: 25%;
  }

  /* figure tag: container for img elements */
  .meals-photo {
      width: 100%;
      margin: 0;
      overflow: hidden;
      background-color: black;
  }

  .meals-photo img {
      opacity: 0.6;
      width: 100%;
      height: auto;
      transform: scale(1.15);
      transition: transform 0.5s, opacity 0.5s;
  }

  .meals-photo img:hover {
      opacity: 1;
      transform: scale(1.03);
  }
  ```
  Notice that for `li` element (child element of `ul` element for the `meal-showcase` class) a `float` attribute is set. Here one can consider the `ul` element as the container of the `li` element. The floating `li` element does not influence the height of its container. Therefore, `li` has height whereas `ul` does not.
  The following changes can solve this problem:
  ``` css
    .meals-showcase {
        list-style: none;
        width: 100%;
        overflow: hidden;
    }
  ```
  *Further reading*: [Block formatting contexts](https://www.w3.org/TR/CSS21/visuren.html#block-formatting); [Containing Floats](http://complexspiral.com/publications/containing-floats/)

---

## 2017-12-31

### **Suedo Class in CSS**

  First refer to this link: [Pseudo Classes](https://www.w3schools.com/css/css_pseudo_classes.asp)

  A pseudo-class is used to define a special state of an element.

  For example, it can be used to:

    * Style an element when a user mouses over it
    * Style visited and unvisited links differently
    * Style an element when it gets focus
  
  Example code:
  ``` html
  <!DOCTYPE html>
    <html>
    <head>
    <style>
    /* unvisited link */
    a:link {
        color: red;
    }

    /* visited link */
    a:visited {
        color: green;
    }

    /* mouse over link */
    a:hover {
        color: hotpink;
    }

    /* selected link */
    a:active {
        color: blue;
    }
    </style>
    </head>
    <body>

    <p><b><a href="default.asp" target="_blank">This is a link</a></b></p>

    </body>
    </html>
  ```
  
  <p><b>Note:</b> a:hover MUST come after a:link and a:visited in the CSS definition in order to be effective.</p>
  <p><b>Note:</b> a:active MUST come after a:hover in the CSS definition in order to be effective.</p>

  Another example would be `h2:after`, which specifies a pseudo class object right after `h2` element. It is also considered as a part of `h2`, and is within `h2`'s boundary. Example code is shown beblow:
  
  ```css
  h2:after {
    /* display mode: block, inline-block, or inline element */
    display: block;
    /* dimensions and color */
    height: 2px;
    width: 100px;
    background-color: #e67e22;
    /* content is basically the text attribute (which will be shown on the page, of this class */
    content: " ";
    /* margin properties: the whole block oject, including margin, border, and padding, is within the h2 block, which is the parent block */
    margin: 0 auto;
    margin-top: 30px;
  }
  ```
  



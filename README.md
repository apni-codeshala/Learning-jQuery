### jQuery CDN link

``` javascript
<script src="https://code.jquery.com/jquery-3.7.1.js" integrity="sha256-eKhayi8LEQwp4NKxN+CfCh+3qOVUtJn3QNZ0TciWLP4=" crossorigin="anonymous"></script>
```

### jQuery syntax
Basic syntax ``` $(selector).action()```
- $ sign to define/access jQuery
- (selector) to find html elements
- action() to be performent on the element

Examples
``` javascript
$(this).hide() // hides the current element

$("p").hide() // hide all <p> elements

$(".test").hide() // hide all element with class="test"

$("#test").hide() // hide the element with id="test"
```

### The Document Ready Event

All jQuery methods are inside a document ready event

```javascript
$(document).ready(function(){
    // jQuery methods goes here
})
```

This is to prevent any jQuery code from running before the document is finished loading(is ready).

It is used to ensure that code within the event handler is executed only after the DOM (Document Object Model) has been fully loaded and is ready for manipulation. This is important because if you try to manipulate elements on the page before they are fully loaded, you might encounter issues or errors.

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>jQuery Document Ready Example</title>
    <!-- Include jQuery library -->
    <script src="https://code.jquery.com/jquery-3.6.4.min.js"></script>
    <script>
        // Use the document ready event
        $(document).ready(function () {
            // Code to be executed when the DOM is ready

            // For example, let's change the text of an element with id "myElement"
            $("#myElement").text("Hello, jQuery!");
        });
    </script>
</head>
<body>
    <!-- Your HTML content -->
    <div id="myElement">Original text</div>
</body>
</html>
```

In this example, the jQuery document ready event is used to change the text of an element with the ID "myElement" after the DOM has fully loaded. If you omit the document ready event and try to manipulate the DOM directly, your code might execute before the DOM is ready, leading to unexpected behavior.

Using ```$(document).ready(function () { /* your code here */ });``` is a common approach, but you can also use a shorthand version by simply writing ```$(function () { /* your code here */ });```. Both accomplish the same thing: ensuring that the enclosed code runs only after the DOM has fully loaded.

### Example of selector
```javascript
$(document).ready(function(){
    $("button").click(function(){
        $("#test").hide();
    })
})
```

Element selector : ```$("p")```.

#id selector : ```$("#test")```.

.class selector : ```$(".test")```.

Select all elements : ```$("*")```.

Select the current element : ```$(this)```. Example for this selector.
```javascript
$(document).ready(function(){
    $("button").click(function(){
        $(this).hide();  // hide the current element button
    })
})
```

Some special type of selecting methods.

- ```$("p.intro")``` select all ```<p>``` element with class="intro"
- ```$("p:firsr")``` select the first ```<p>``` element
- ```$("ul li:first")``` select the first ```<li>``` element of the first ```<ul>```
- ```$("ul li:first-child")``` select the first ```<li>``` element of every ```<ul>```
- ```$("[href]")``` select all element with an href attribute
- ```$("a[target='_blank']")``` select all ```<a>``` element with a target attribute value equal to "_blank"
- ```$("a[target!='_blank']")``` select all ```<a>``` element with a target attribute value NOT equal to "_blank"
- ```$(":button")``` select all ```<button>``` elements and ```<input>``` elements of type="button"
- ```$("tr:even")``` select all even ```<tr>``` elements
- ```$("tr:odd")``` select all odd ```<tr>``` elements

### Function in a seperate file
If your website contains a lpt of pages, and you want your jQuery functions to easy to maintain, you can put your jQuery functions in a seperate .js file.

Example:
```html
<head>
    <script src="https://ajax.googleapis.com.ajax/libs/jquery/3.7.1/jquery.min.js"></script>
    <script src="my_jquery_functions.js"></script>
</head>
```

### jQuery event methods

| Mouse Events | Keyboard Events | Form Events | Document/Window Events |
|--------------|-----------------|-------------|------------------------|
| click | keypress | submit | load |
| dbclick | keydown | change | resize |
| mouseenter | keyup | focus | scrool |
| mouselevel |  | blur | unload |


### Commonly used jQuery event methods

1. click()

    The click() method attaches an event handler function to an HTML element.
    The function is executed when the user click on the HTML element.
    ```javascript
    $("p").click(function(){
        $(this).hide();
    });
    ```

2. dblclick()

    The function is executed when the user double-clicks on the HTML element.
    ```javascript
    $("p").dblclick(function(){
        $(this).hide();
    });
    ```

3. mouseenter()

    The function is executed when the mouse pointer enters the HTML element.
    ```javascript
    $("#p1").mouseenter(function(){
        alert("You entered p1!");
    });
    ```

4. mouseleave()

    The function is executed when the mouse pointer leaves the HTML element.
    ```javascript
    $("#p1").mouseleave(function(){
        alert("Bye! You now leave p1!");
    });
    ```

5. mousedown()

    The function is executed, when the left, middle or right mouse button is pressed down, while the mouse is over the HTML element.
    ```javascript
    $("#p1").mousedown(function(){
        alert("Mouse down over p1!");
    });
    ```

6. mouseup()

    The function is executed, when the left, middle or right mouse button is released, while the mouse is over the HTML element.
    ```javascript
    $("#p1").mouseup(function(){
        alert("Mouse up over p1!");
    });
    ```

7. hover()

    The first function is executed when the mouse enters the HTML element, and the second function is executed when the mouse leaves the HTML element.
    ```javascript
    $("#p1").hover(function(){
        alert("You entered p1!");
    },
    function(){
        alert("Bye! You now leave p1!");
    });
    ```

8. focus()

    The function is executed when the form field gets focus.
    ```javascript
    $("input").focus(function(){
        $(this).css("background-color", "#cccccc");
    });
    ```

9. blur()

    The function is executed when the form field loses focus.
    ```javascript
    $("input").blur(function(){
        $(this).css("background-color", "#ffffff");
    });
    ```

10. on()

    The on() method attaches one or more event handlers for the selected elements.
    ```javascript
    // Attach a click event to a <p> element
    $("p").on("click", function(){
        $(this).hide();
    });

    // Attach multiple event handlers to a <p> element
    $("p").on({
        mouseenter: function(){
            $(this).css("background-color", "lightgray");
        },
        mouseleave: function(){
            $(this).css("background-color", "lightblue");
        },
        click: function(){
            $(this).css("background-color", "yellow");
        }
    });
    ```

### Exercise:

If you press a keyboard key inside an ```<input>``` element, it should be hidden. Use the correct event to do so.
```javascript
$("input").keypress(function(){
    $(this).hide();
});
```

## jQuery Effects

### jQuery hide() and show()

Syntax: 
```
$(selector).hide(speed,callback);

$(selector).show(speed,callback);
```

The optional speed parameter specifies the speed of the hiding/showing, and can take the following values: "slow", "fast", or milliseconds.

The optional callback parameter is a function to be executed after the hide() or show() method completes.

```javascript
$("button").click(function(){
    $("p").hide(1000);
});
```

### jQuery toggle()

You can also toggle between hiding and showing an element with the toggle() method.

Shown elements are hidden and hidden elements are shown.

Syntax:

```
$(selector).toggle(speed,callback);
```
The optional speed parameter can take the following values: "slow", "fast", or milliseconds.

The optional callback parameter is a function to be executed after toggle() completes.

```javascript
$("button").click(function(){
    $("p").toggle();
});
```

### jQuery Effects - Fading

With jQuery you can fade an element in and out of visibility.

jQuery has the following fade methods:
- fadeIn()
- fadeOut()
- fadeToggle()
- fadeTo()

1. fadeIn()

    The jQuery fadeIn() method is used to fade in a hidden element.

    Syntax:
    
    ```
    $(selector).fadeIn(speed,callback);
    ```

    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
            <script>
            $(document).ready(function(){
                $("button").click(function(){
                    $("#div1").fadeIn();
                    $("#div2").fadeIn("slow");
                    $("#div3").fadeIn(3000);
                });
            });
            </script>
        </head>
        <body>
            <p>Demonstrate fadeIn() with different parameters.</p>
            <button>Click to fade in boxes</button><br><br>
            <div id="div1" style="width:80px;height:80px;display:none;background-color:red;"></div><br>
            <div id="div2" style="width:80px;height:80px;display:none;background-color:green;"></div><br>
            <div id="div3" style="width:80px;height:80px;display:none;background-color:blue;"></div>
        </body>
    </html>
    ```

2. fadeOut()

    The jQuery fadeOut() method is used to fade out a visible element.

    Syntax:
    ```
    $(selector).fadeOut(speed,callback);
    ```

    Example:
    ```javascript
    $("button").click(function(){
        $("#div1").fadeOut();
        $("#div2").fadeOut("slow");
        $("#div3").fadeOut(3000);
    });
    ```

3. fadeToggle();

    The jQuery fadeToggle() method toggles between the fadeIn() and fadeOut() methods.

    If the elements are faded out, fadeToggle() will fade them in.

    If the elements are faded in, fadeToggle() will fade them out.

    Syntax:

    ```
    $(selector).fadeToggle(speed,callback);
    ```

    Example:
    ```javascript
    $("button").click(function(){
        $("#div1").fadeToggle();
        $("#div2").fadeToggle("slow");
        $("#div3").fadeToggle(3000);
    });
    ```

4. fadeTo()

    The jQuery fadeTo() method allows fading to a given opacity (value between 0 and 1).

    Syntax:
    ```
    $(selector).fadeTo(speed,opacity,callback);
    ```

    Example:
    ```javascript
    $("button").click(function(){
        $("#div1").fadeTo("slow", 0.15);
        $("#div2").fadeTo("slow", 0.4);
        $("#div3").fadeTo("slow", 0.7);
    });
    ```

### jQuery Effects - Sliding

The jQuery slide methods slide elements up and down.

jQuery has the following slide methods:

- slideDown()
- slideUp()
- slideToggle()

1. slideDown()

    The jQuery slideDown() method is used to slide down an element.

    Syntax:
    ```
    $(selector).slideDown(speed,callback);
    ```

    Example:
    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.7.1/jquery.min.js"></script>
            <script> 
                $(document).ready(function(){
                    $("#flip").click(function(){
                        $("#panel").slideDown("slow");
                    });
                });
            </script>
            <style> 
                #panel, #flip {
                    padding: 5px;
                    text-align: center;
                    background-color: #e5eecc;
                    border: solid 1px #c3c3c3;
                }

                #panel {
                    padding: 50px;
                    display: none;
                }
            </style>
        </head>
        <body>
            <div id="flip">Click to slide down panel</div>
            <div id="panel">Hello world!</div>
        </body>
    </html>

    ```
2. slideUp()

    The jQuery slideUp() method is used to slide up an element.

    Syntax:
    ```
    $(selector).slideUp(speed,callback);
    ```
    Example:
    ```javascript
    $("#flip").click(function(){
        $("#panel").slideUp();
    });
    ```

3. slideToggle() 

    The jQuery slideToggle() method toggles between the slideDown() and slideUp() methods.

    If the elements have been slid down, slideToggle() will slide them up.

    If the elements have been slid up, slideToggle() will slide them down.

    Syntax:
    ```
    $(selector).slideToggle(speed,callback);
    ```
    Example:
    ```javascript
    $("#flip").click(function(){
        $("#panel").slideToggle();
    });
    ```


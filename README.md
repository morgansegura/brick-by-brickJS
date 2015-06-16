#Brick By BrickJS

###A Masonry Alternative Page Layout Plugin

Brick By BrickJS isolates and delivers core Masonry style page layout functionality in the form of a lightweight jQuery plugin.

The plugin is **[MIT Licensed](https://github.com/html5andblog/brick-by-brickJS/blob/master/LICENSE).**

Examples can be found on [HTML5 and Beyond](http://www.html5andbeyond.com/brick-by-brick-js-masonry-alternative-full-instructions/) and on [CodePen](http://www.codepen.io/html5andblog/tag/masonry%20style/).

Documentation can be accessed via the Brick By Brick website or in [Markdown format](https://github.com/html5andblog/brick-by-brickJS/blob/master/brick-by-brick-docs.md).

###Getting Started

###1. Add the HTML

The basic HTML markup consists of a container div which needs an ID or Class. The divs within the container will be the items in the layout display.
The items don't need a specific class to enable the layout as the class 'b-by-b-item' is automatically added to them when the plugin starts.
 
```html
<div id="layout">
     <div>item</div>
     <div>item</div>
     <div>item</div>
     <div>item</div>
     <div>item</div>
 </div>
```
 
###2. Add the CSS

Set the number of columns at variable screen widths using Media Queries.**100% :is equal to 1 Column, 50% is equal to 2 Columns, 33.3% is equal to 3 Columns, etc.**
This CSS will create a three column layout which will scale down to two and then to one with the screen.

```css
     .single-column .b-by-b-item {
       width: 100%!important;
    }
	
    @media (min-width: 0px) and (max-width: 480px) {
       #layout .b-by-b-item {
           width: 100%;
        }
    }
   
    @media (min-width: 481px) and (max-width: 1024px) {
        #layout .b-by-b-item {
          width: 50%;
        }
    }
	
    @media (min-width: 1025px) {
       #layout .b-by-b-item {
         width: 33.33%;
      } 
    }
```

Once the plugin initiates, each of the child divs will be given the class 'b-by-b-item'. You will then be able to use this class to style the items within the layout:

```css
    #layout .b-by-b-item {
        background-color: #ff4500;
    }
```

###3.Link to the jQuery library and plugin file

Load the jQuery Library and the Brick By Brick JS File in head of your HTML document, or just before the body tag closes.

``` html
    <script src="http://code.jquery.com/jquery-1.11.0.min.js"></script>
    <script src="js/layout.js"></script>
```
	
###4.Start the plugin

The plugin is called on the container selector as in: **$(id or class).layout();**

```javascript
$('#layout').layout();
 ```
	
There are two options which can be added to the plugin, these both affect the individual items by adding a margin and padding. Both values default at 5px.

```javascript
  $('#layout').layout({
      itemMargin: 5,
      itemPadding: 5
  });
 ```

	
#Methods

###Brick By Brick methods are applied to the element (and the items within it) on which the plugin is called or initialised.

##addAfter

**Argument types: jQuery object or HTML String**

Appends content to the Brick By Brick layout. Appended items will assume Brick By Brick behaviour. 

- Use an array of one or more jQuery objects (to add existing content) or HTML strings (to add content dynamically).

```javascript
var existingElems = [$('#existing1'), $('#existing2')],
        newElems = ['<div id="new-elem">Some content</div>'];
$('#layout').layout( 'addAfter' , existingElems );
$('#layout').layout( 'addAfter' , newElems );
 ```


##addBefore

**Argument types: jQuery object or HTML String**

Prepends content to the container element. Prepended items will assume Brick By Brick behaviour. 

- Use an array of one or more jQuery objects (to add existing content) or HTML strings (to add content dynamically).


```javascript
var existingElems = [$('#existing1'), $('#existing2')],
       newElems = ['<div id="new-elem">Some content</div>'];
$('#layout').layout( 'addBefore' , existingElems );
$('#layout').layout( 'addBefore' , newElems );
  ```

##removeItems

**Argument types: jQuery selector string, integer (default: 1000)**

Removes content both from the Brick By Brick layout and the DOM. 

- Specify items to remove using an array of one or more jQuery selector strings. jQuery objects cannot be used as arguments

- Optionally specify a duration for the fade-out animation

```javascript
var elements = ['.remove-items', '#remove-item', 'div[data-attr="Value"]'];
$('#layout').layout( 'removeItems' , elements, 1000 );
 ```

	
##hideItems

**Argument types: jQuery selector string, integer (default: 1000)**

Hides content in the Brick By Brick layout. Specify items to hide using an array of one or more jQuery selector strings.

- Specify items to remove using an array of one or more jQuery selector strings. jQuery objects cannot be used as arguments.

- Optionally specify a duration for the fade-out animation

```javascript   
var elements = ['.hide', '#hide-item', 'div[data-display="hide"]'];
$('#layout').layout( 'hideItems' , elements, 1000 );
 ```

##showItems

**Argument type: jQuery selector string, integer (default: 1000)**

Displays hidden content in the Brick By Brick layout. Specify items to show using an array of one or more jQuery selector strings.

- Specify items to show using an array of one or more jQuery selector strings.

- Optionally specify a duration for the fade-in animation

```javascript
 var elements= ['.hidden', '#show-item', 'div[data-display="show"]'];
 $('#layout').layout( 'showItems' , elements, 1000 ); 
 ```

##end

Destroys the Brick By Brick layout so that items within the container element no longer assume Brick By Brick behaviour.

Once the end method has been run, the class 'no-grid' will be added to the layout selector. For example, the div with the ID 'layout' will have the class 'no-grid' added. This can then be used to style the grid.

```javascript 
$('#end').on('click', function(){
      $('#layout').layout( 'end' );
});
 ```

##reload

Reinstates a destroyed Brick By Brick layout.

```javascript 
$('#reload').on('click', function(){
      $('#layout').layout( 'reload' );
 });
 ```



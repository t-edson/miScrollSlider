# miScrollSlider
miScrollSlider is a very simple ínfinite auto scroll slider, created using only HTML and CSS animation. No navigation buttons are included.

Implementing a continuous scroll slider in pure CSS is not so easy. The first approach is using animations and set "animation-direction: alternate", however this don't get the continuous scroll but a two-direction movement.

To solve this problem I propose to repeat the first page of the scroll and locate it at the end, in order to obtain the end->first transition, and then switch quickly to the first page again.

We can use this technic to animate sliders with any number of pages, however the CSS needs to be adapted to the number of frames shown.

Here I show how to slide two pages in an infinite CSS animation loop:

The HTML

```html
<div class="slider">
 <ul class="slidercont">
    <li> This is the Element 1 </li>
    <li> This is The Element 2 </li>
    <!-- YEs the first page again -->
    <li> This is The Element 1 </li>
  </ul>  
</div>
```     
The last page, of the slider, needs to be duplicated in this solution.

The content for a page of the slider must be inserted in the <li> .. </li> tag and in theory can be any kind of html content including responsive content.

The CSS

```css
.slider { 
  margin: auto;
  overflow: hidden;
}
.slidercont {  
  display: flex;
  padding: 0;
  width: 300%; 
  animation: change2pag 20s infinite linear;
}
.slidercont>li {  
  width: 100%;
  list-style: none;
}
@keyframes change2pag {
  /*First state*/
  0% {margin-left: 0;}
  45% {margin-left: 0;}
  /*Secoond state*/
  48% {margin-left: -100%;}
  93% {margin-left: -100%;}
  /*Return to first state*/
  96% {margin-left: -200%;}
  96.001% {margin-left: 0;}
  100% {margin-left: 0;}
}
```

And that's all. No Javascript needed. Maybe it is a good idea to use Javascript to implement the navigation buttons. It's possible too to implement navigation buttons in pure CSS, however it's not a solid implementation.

If included more than two pages, the animation need to include more intervals too, in the @keyframes section.

This slider has been tested in Chrome, Firefox and Opera browsers. It shoul be compatible with all versions that support CSS animations.

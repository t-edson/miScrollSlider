# miScrollSlider
miScrollSlider is a very simple ínfinite auto scroll slider, created using only HTML and CSS animation.

Implementing a continuous scroll slider in pure CSS is not so easy. The first approach is using animations and set "animation-direction: alternate", however this don't get the continuos scroll but a two-direction movement.

To solve this problem I propose to repeat the first frame of the scroll and locate it at the end, in order to obtain the end->first transition, and then switch quicly to the first frame again.

We can use this technic to animate sliders with any number of pages, however the CSS needs to be adapted to the number of frames swhon.

Here I show how to slide two pages in a infinite CSS animation loop:

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


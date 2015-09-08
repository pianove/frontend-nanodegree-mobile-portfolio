## Website Performance Optimization portfolio project


### Getting started

Copy the below URL to your web browser:

http://pianove.github.io/frontend-nanodegree-mobile-portfolio/

####Part 1: Optimize PageSpeed Insights score for index.html
Run the above URL through PageSpeed Insights.

Below you find the modifications that I made based on the suggestions whispered by this awesome Google product.

The original 30/100 Desktop speed score has been significantly improved to 88/100 thanks to

1. Image optimization 
when I resized /views/images/pizzeria.jpg.

then went up to 94/100 thanks to 

2. css optimization (media=print)

3. remove of the $<script async src="js/perfmatters.js"></script>"
as the crpmetrics can be reported by google analytics api. 
the inline script function sends these metrics to an analytic server.]

4. skip web font and inline css into html to optimize bytes and get the same design.

All these changes resulted in a mobile score of 93/100.

####Part 2: Optimize Frames per Second in pizza.html

To launch pizza.html you copy the below Url to your web browser http://pianove.github.io/frontend-nanodegree-mobile-portfolio/views/pizza.html

When scrolling, the original total time to run updatePositions function call was way too long 623.245ms and with many warnings about forced synchronous layout.

Changes made to updatePositions function:

line 483>

use getElementsByClassName('.mover) instead of querySelectorAll

line 485>

The Layout gets retriggered every time we scroll. To avoid style recalculation and lean the for loop, scrollTop is cached and phase calculation removed from the loop

line 486>

since phase value gives always the same set of 5 numbers (1,2,3,4,0) as Modulo gives the remainder when we divide i by 5, it can be calculated outside of loop

line 500>

I used css transform property as a hardware acceleration transform: translateX()

line 518>

added the updatePositions function as a parameter to the window.requestAnimationFrame method in the scroll event listener

line 530> 

Only three rows of pizzas that show up on the screen at any given scroll with 8 columns, i can be reduced to 24. Removed updatePositions() function call, and calculate phase and y coordinate of each pizza

Other changes made to pizza.html

1. use cdn link to minified bootstrap css

2. inline css

The development source code is under branch MySolution on github:
https://github.com/pianove/frontend-nanodegree-mobile-portfolio/tree/mysolution

REMAINING ISSUES

The scripting time went nicely down after all these changes, however the painting time is still very high even after translateX() or playing with other css feature in devtools while continuous painting on.

### Resources
 * [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api")
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>


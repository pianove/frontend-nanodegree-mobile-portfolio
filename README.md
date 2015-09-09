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

Changes made to updatePositions function in order to avoid style recalculation and lean the for loop to optimize calculation time:

Line 483>

    Use getElementsByClassName('.mover) instead of querySelectorAll

Line 485>

    The Layout gets retriggered every time we scroll, scrollTop is cached and phase calculation removed from the loop

Line 486>

    Since phase value gives always the same set of 5 numbers (1,2,3,4,0), can be calculated outside of loop

Line 500>

    I used css transform property as a hardware acceleration transform: translateX()

Line 518>

    Added the updatePositions function as a parameter to the window.requestAnimationFrame method in the scroll event listener

line 530> 

    Only a handful pizzas show up on screen at a time, to optimize i value based on screen resolution, window height and width were introduced. Removed updatePositions() function call, and calculate phase and y coordinate of each pizza.

Changes made to changePizzaSizes(size) function

    Optimize for loop calculation time by moving out newwidth and dx values.

    querySelectorAll replaced by getElementsByClassName



Other changes made to pizza.html

    Use cdn link to minified bootstrap css

    Inline css

The development source code is under branch MySolution and folder/views/js/main.js on github:
https://github.com/pianove/frontend-nanodegree-mobile-portfolio/tree/mysolution

The production code is linted/optimized and minified with gulp under views/public/js and public/images.


REMAINING ISSUES

The scripting time went nicely down after all these changes, however the painting time is still very high even after translateX() or playing with other css feature in devtools while continuous painting on or optimizing through gulp.

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


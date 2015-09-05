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
3. remove of the <script async src="js/perfmatters.js"></script> as the crpmetrics can be reported by google analytics api. the inline script function sends these metrics to an analytic server.
4. skip web font and inline css into html to optimize bytes and get the same design.

All these changes resulted in a mobile score of 93/100.


####Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, you will need to modify views/js/main.js until your frames per second rate is 60 fps or higher. You will find instructive comments in main.js. 

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

To launch pizza.html you copy the below Url to your web browser http://pianove.github.io/frontend-nanodegree-mobile-portfolio/views/pizza.html

1.When scrolling, the original total time to run updatePositions function call was way too long 623.245ms and with many warnings about forced synchronous layout.

Changes made to updatePositions function:
1. use getElementsByClass('.mover) instead of querySelecteroAll
2. since phase value gives always the same set of 5 numbers (1,2,3,4,0) as Modulo gives the remainder when we divide i by 5,  
To optimize this 

### Optimization Tips and Tricks
* [Optimizing Performance](https://developers.google.com/web/fundamentals/performance/ "web performance")
* [Analyzing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/analyzing-crp.html "analyzing crp")
* [Optimizing the Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/optimizing-critical-rendering-path.html "optimize the crp!")
* [Avoiding Rendering Blocking CSS](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-blocking-css.html "render blocking css")
* [Optimizing JavaScript](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript.html "javascript")
* [Measuring with Navigation Timing](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/measure-crp.html "nav timing api"). We didn't cover the Navigation Timing API in the first two lessons but it's an incredibly useful tool for automated page profiling. I highly recommend reading.
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/eliminate-downloads.html">The fewer the downloads, the better</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer.html">Reduce the size of text</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/image-optimization.html">Optimize images</a>
* <a href="https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching.html">HTTP caching</a>

### Customization with Bootstrap
The portfolio was built on Twitter's <a href="http://getbootstrap.com/">Bootstrap</a> framework. All custom styles are in `dist/css/portfolio.css` in the portfolio repo.

* <a href="http://getbootstrap.com/css/">Bootstrap's CSS Classes</a>
* <a href="http://getbootstrap.com/components/">Bootstrap's Components</a>


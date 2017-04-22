## Two main goals for this website performance optimization project

1) Optimize Website Performance by working on the Critical Rendering Path (CRP) for 90+ speed per Google PageSpeed Insights
2) Optimize Frames per Second (FPS) to perform at 60fps in pizza.html by getting rid of all the jank when resizing and scrolling through the website.

## Website Performance Optimization portfolio project

The goal of this project was to optimize the online portfolio for speed. How? By using different tools and skills such as Google Developer Tools to inspect and optimize the Critical Rendering Path (CRP) to render as quickly as possible, [Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) to understand and optimize performace in terms of speed, [ngrok](https://ngrok.com/) to run a local server and use the public link in PageSpeed. 

I've also applied skills such as Minify and Inline CSS for stylesheets and web fonts, asynch JS, and elimination of render-blocking CSS and JavaScript in above-the-fold content.

### Optimizations Performed

#### Part 1: Optimize PageSpeed Insights score for index.html
* Removed external request for Web Fonts and used inline CSS to add them inside index.html
* Minified and inlined CSS and added in index.html
* Added `asynch` to JS Script and moved to the bottom of index.html body
* Optimized all images using ImageOptim
#### How to run it
* Download Zip file from [repository](https://github.com/rchrdchn/website-optimization)
* Unzip file
* Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.
* Use Command Line to create local server - instructions here:
  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```
* Copy the `http` link to your `local host 8080`
* Open browser and go to [Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
* RESULT: Paste `http local host 8080` link in PageSpeed Insights to see final result of 90+

#### Part 2: Optimize Frames per Second in pizza.html
* Edited the main.js file so the resizing of the pizzas happens in less than 5 ms and the scrolling runs at 60 FPS
* Simplified the function `resizePizzas` so it doesn't trigger forced synchronous layout (FSL). The pizzas width simply gets set to a certain percentage of the original image size, depending on the slider position.
* Changed `updatePositions` so it doesn't trigger FSL by first getting `scrollTop` and then updating all elements later.
* Updated `querySelectorAll("#mover")` to `getElementsByClassName("mover")` so it doesn't have to recalculate on every iteration
#### How to run it
* Download Zip file from [repository](https://github.com/rchrdchn/website-optimization)
* Unzip file
* Open browser
* Go to project folder -> `views` folder -> open `pizza.html`
* Right click on pizza.html window, select inspect, go to `console` to view time to generate layout and paint in miliseconds (ms)
* Alternative in Mac: `option` + `command` + `j` keyword
* Press `esc` keyword, click on the `rendering` tab, and check `FPS meter`
* With `console` opened, scroll down and up in the web page
* RESULT: you should see Frame Rate on the upper right to be 60 fps consistently

To get started, check out the repository and inspect the code.

### Getting started

#### Part 1: Optimize PageSpeed Insights score for index.html

Some useful tips to help you get started:

1. Check out the repository by cloning it with

  ```git clone https://github.com/rchrdchn/website-optimization.git```

1. Open a browser and visit localhost:8080
1. Download and install [ngrok](https://ngrok.com/) to the top-level of your project directory to make your local server accessible remotely.

  ``` bash
  $> cd /path/to/your-project-folder
  $> ./ngrok http 8080
  ```

1. Copy the public URL ngrok gives you and try running it through [Google PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)! Optional: [More on integrating ngrok, Grunt and PageSpeed.](http://www.jamescryer.com/2014/06/12/grunt-pagespeed-and-ngrok-locally-testing/)

#### Part 2: Optimize Frames per Second in pizza.html

To optimize views/pizza.html, I had to modify views/js/main.js until frames per second rate is 60 fps or higher. All optimization can be found in the comments in main.js. 

You might find the FPS Counter/HUD Display useful in Chrome developer tools described here: [Chrome Dev Tools tips-and-tricks](https://developer.chrome.com/devtools/docs/tips-and-tricks).

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

### Author
Code written and optimized by [Richard Chan](http://richardchan.me/)
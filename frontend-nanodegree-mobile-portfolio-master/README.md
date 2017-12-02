# Udacity Web Perforance Project

## How to Access My Project
Direct your browser to [my GitHub repository](https://github.com/nightowl2121/nightowl2121.github.io)

## How to Check the Portfolio's PageSpeed Insights Score
Open **index.html** in my repository, copy the path, and paste it into [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)

## How to Load Pizza.html
**pizza.html** is found in the views folder. Copy its path, and paste it into your browser.

# Optimizations

## Index.html
I eliminated some reder blocking by inlining the necessary CSS and moving the links to the style sheets to the bottom of the code right before `</body>`.

I also eliminated some render blocking by asynchronously loading the JavaScript files in lines 149 & 150.

## Pizza.html
No optimizations were made to **pizza.html**. I successfully got the pizza page to 60fps by only editing main.js.

## Main.js
1.
        // Moves the sliding background pizzas based on scroll position
        function updatePositions() {
        // document.body.scrollTop is no longer supported in Chrome.
          var scrollTop = document.documentElement.scrollTop || document.body.scrollTop;
          var items = document.querySelectorAll('.mover');
          frame++;
          window.performance.mark("mark_start_frame");

          // Sets the new location of each moving pizza when the page is scrolled
          for (var i = 0; i < items.length; i++) {
            var phase = Math.sin((scrollTop / 1250) + (i % 5));
            // The following line of code is from a user on Slack that I helped with this project
            // Used with permission
            items[i].style.transform = "translateX(" + (700 * phase) + "px)";
          }
          
In this snippet of code, I moved `var scrollTop` and `var items` higher up in the function

I also added `items[i].style.transform` to make the pizza scrolling happen more quickly

2.
        // Iterates through pizza elements on the page and changes their widths
          // This chunk of code was taken from the course video called "Quiz: Stop FSL" 
          // ^^^(Section 5: Advanced Interactive Websites, Lesson 8: Styles and Layouts, Video 10) 
          function changePizzaSizes(size) {
            // Assigns the width for each pizza size
            switch(size) {
              case "1":
                newWidth = 25;
                break;
              case "2":
                newWidth = 33.3;
                break;
              case "3":
                newWidth = 50;
                break;
              default:
                console.log("bug in sizeSwitcher");
            }

            var randomPizzas = document.querySelectorAll(".randomPizzaContainer");

            // Gives the pizzas the new sizes once the slider is changed
            for (var i = 0; i < randomPizzas.length; i++) {
              randomPizzas[i].style.width = newWidth + "%";
            }
          }

          changePizzaSizes(size);
  
In this snippet of code, I got rid of the bottleneck that was causing forced synchronous layout within the pizza slider, causing the pizza to change sizes in under 1ms.

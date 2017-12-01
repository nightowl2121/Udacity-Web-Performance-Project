# Udacity Web Perforance Project

## How to Access My Project
Direct your browser to [my GitHub repository](https://github.com/nightowl2121/nightowl2121.github.io)

## How to Check the Portfolio's PageSpeed Insights Score
Open **index.html** in my repository, copy the path, and paste it into [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)

## How to Load Pizza.html
**pizza.html** is found in the views folder
Copy its path, and paste it into your browser

# Optimizations

## Index.html
I eliminated some reder blocking by inlining the necessary CSS and moving the links to the style sheets to the bottom of the code right before `</body>`

I also eliminated some render blocking by asynchronously loading the JavaScript files in lines 149 & 150

## Pizza.html
No optimizations were made to **pizza.html**. I successfully got the pizza page to 60fps by only editing main.js


# How a Browser Renders HTML, CSS, and JavaScript

When we build websites, it is essential to understand how a browser converts our HTML, CSS, and JavaScript files into a live web page. This helps us create pages that are faster, cleaner, and more reliable. The rendering process happens in several steps, and each step plays a key role in displaying the final page on the screen.

## 1. Parsing the HTML and Building the DOM
When the browser starts receiving the HTML file, it immediately begins reading it. The HTML is broken down into small tokens, including start tags, end tags, and text. Using these tokens, the browser builds the **DOM (Document Object Model)**. The DOM is a tree-like structure that represents all elements in the web page.

## 2. Fetching External Resources
While reading HTML, the browser may find external resources such as CSS files, JavaScript files, images, or fonts. It sends separate requests to download them.

* CSS files do not stop the process, but they block the final rendering until they are fully loaded.
* JavaScript files, by default, block HTML parsing until they load and run.

To avoid blocking, developers sometimes use:
* `defer` — runs the script after HTML parsing finishes.
* `async` — runs the script as soon as it loads, without waiting and without order.

## 3. Parsing CSS and Building the CSSOM
After CSS files load, the browser parses them and builds another tree called the **CSSOM (CSS Object Model)**. It contains all CSS rules, selectors, and properties.  
CSS blocks rendering because the browser must know all styles before it can place elements on the screen.

## 4. Executing JavaScript
When JavaScript files load, the browser parses, compiles, and executes them using its JavaScript engine. This step is heavier than parsing HTML or CSS, so it affects performance.

There are two important events:
* `DOMContentLoaded` — fired when HTML is parsed and synchronous scripts are done.
* `load` — fired when everything is fully loaded, including images and async scripts.

## 5. Creating the Render Tree (DOM + CSSOM)
The browser now combines the DOM and CSSOM to form the **render tree**.  
The render tree contains only the elements that will appear on the screen.  
For example:
* Elements like `<head>` are removed.
* Elements with `display: none` are not included.
* Elements hidden with `visibility: hidden` or `opacity: 0` are included.

## 6. Layout and Painting
Next, the browser calculates the exact position and size of each element. This step is called **layout**.  
After that, the browser paints each element on the screen. Painting is the final step that turns data into actual pixels the user sees.

Once all these steps are finished, the web page becomes visible and interactive.

## References
* https://starkie.dev/blog/how-a-browser-renders-a-web-page
* https://engineering.teknasyon.com/what-is-the-dom-how-does-html-rendering-happen-in-browsers-cbeb12bdfea6

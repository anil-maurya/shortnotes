# JavaScript Performance


## Cources

=> https://developers.google.com/web/fundamentals
=> Udacity Cource

## How Browser Render Webpages

HTML => DOM
				=> Render Tree => Layout => Paint
CSS  => CSSOM 


## DOM

## CSSOM - CSS Object Model

After constructing the DOM, the browser reads CSS from all the sources (external, embedded, inline, user-agent, etc.) and construct a CSSOM. CSSOM stands for CSS Object Model which is a Tree Like structure just like DOM.


## Render Tree

Render-Tree is a tree-like structure constructed by combining DOM and CSSOM trees. The browser has to calculate the layout of each visible element and paint them on the screen, for that browser uses Render-Tree. Hence, unless Render-Tree isn’t constructed, nothing will get printed on the screen.

Render-Tree combines DOM and CSSOM to generate a tree-like structure containing only the elements which will be printed on the screen.


## Rendering Sequence

When a web page is loaded, the browser first reads the TEXT HTML and constructs DOM Tree from it. Then it processes the CSS whether that is inline, embedded or external CSS and constructs the CSSOM Tree from it. After these trees are constructed, then it constructs the Render-Tree from it. Once the Render-Tree is constructed, then the browser starts the printing individual elements on the screen




## Critical Rendering path

The Critical Rendering Path is the sequence of steps the browser goes through to convert the HTML, CSS, and JavaScript into pixels on the screen. Optimizing the critical render path improves render performance.The critical rendering path includes the Document Object Model (DOM), CSS Object Model (CSSOM), render tree and layout.


The document object model is created as the HTML is parsed. The HTML may request JavaScript, which may, in turn, alter the DOM. The HTML includes or makes requests for styles, which in turn builds the CSS object model. The browser engine combines the two to create the Render Tree. Layout determines the size and location of everything on the page. Once layout is determined, pixels are painted to the screen.

Optimizing the critical rendering path improves the time to first render. Understanding and optimizing the critical rendering path is important to ensure reflows and repaints can happen at 60 frames per second, to ensure performant user interactions and avoid jank.



https://developer.mozilla.org/en-US/docs/Web/Performance/Critical_rendering_path


## Paint and Layout/Reflow

https://blog.usejournal.com/what-the-heck-is-repaint-and-reflow-in-the-browser-b2d0fb980c08


## Debouncing and Throttling



## High Performance animations


## async, defer

https://javascript.info/script-async-defer


## Prefetch, Preload, and Preconnect

https://www.machmetrics.com/speed-blog/guide-to-browser-hints-preload-preconnect-prefetch/


Ultimate Guide to Browser Hints: Preload, Prefetch, and Preconnect 



## PWA 

=> Caching Files with Service Worker
https://developers.google.com/web/ilt/pwa


## lazy Loading

Lazy loading (also called on-demand loading) is an optimization technique for the online content, be it a website or a web app.

Instead of loading the entire web page and rendering it to the user in one go as in bulk loading, the concept of lazy loading assists in loading only the required section and delays the remaining, until it is needed by the user.

Advantages of Lazy loading:

On-demand loading reduces time consumption and memory usage thereby optimizing content delivery. As only a fraction of the web page, which is required, is loaded first thus, the time taken is less and the loading of rest of the section is delayed which saves storage. All of this enhances the user’s experience as the requested content is fed in no time.
Unnecessary code execution is avoided.
Optimal usage of time and space resources makes it a cost-effective approach from the point of view of business persons. (website owners)
Disadvantages of Lazy loading:

Firstly, the extra lines of code, to be added to the existing ones, to implement lazy load makes the code a bit complicated.
Secondly, lazy loading may affect the website’s ranking on search engines sometimes, due to improper indexing of the unloaded content.


## DOM recycling

The general idea is to use already created DOM elements that are off-screen instead of creating new ones. Admittedly, DOM nodes themselves are cheap, but they are not free, as each of them adds extra cost in memory, layout, style and paint. Low-end devices will get noticeably slower if not completely unusable if the website has too big of a DOM to manage. Also keep in mind that every relayout and reapplication of your styles – a process that is triggered whenever a class is added or removed from a node – grows more expensive with a bigger DOM. Recycling your DOM nodes means that we are going to keep the total number of DOM nodes considerably lower, making all these processes faster.



## HTTP Status Codes


https://developer.mozilla.org/en-US/docs/Web/HTTP/Status


## Applications Security - HTTPS


## CORS, XSS, CSRF

https://dev.to/maleta/cors-xss-and-csrf-with-examples-in-10-minutes-35k3

## Cookies

## Browser Storage


## History API


## Single Page Application (SPA) 

- Advantages
	- Highly React
	- Decoupled frontend

- Disadvantages
	- SEO is challenging
	- JavaScript Strictly Required
	- Tedns to favor modern browser


## Multi Page Application (MPA)

- Advantages
	- SEO friendly
	- Loads of existing frameworks, solutions and best practices
	- Tends to better support legacy browsers
	
- Disadvantages
	- Slower, constantly needs to load pages
	- Tightly coupled frontend and backend







## Accessibility 
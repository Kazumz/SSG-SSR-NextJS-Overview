# Overview
This repository has been created to demonstrate the differences between CSR (Client-side rendering) and an SSG (Static-site generation) / SSR (Server-side rendering) approach when creating React applications.

## Client Side Rendering (CSR)
Since the internet's inception, it's followed a fairly consistent pattern of what happens when a user visits a website. When you visit a website, you're actually downloading the content of that website from the server. For example, visting a website that contains a single HTML page with some lorem ipsum text on it would yield somewhat the following process:
- Visit Website
- Download HTML content
- Upon completion, your browser will "paint/render" this for you on screen. The HTML instructs the browser how to display this particular page. 

### Create React App
Just a library that runs inside of the user's browser, writing and replacing pieces of the DOM after it's all been downloaded from the website you're visting.

### What happens with someone visits a website?
- Download HTML, CSS, and JavaScript bundles.
![Client Side Rendering](https://miro.medium.com/max/700/1*CRiH0hUGoS3aoZaIY4H2yg.png)

- User is shown the default index.html "You must use JavaScript to view this Website" page.
- The default page is overwritten by the index.js(ts) ReactDOM.Render() and any child components.

## Credits
https://medium.com/walmartglobaltech/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8#:~:text=The%20main%20difference%20is%20that,with%20links%20to%20your%20javascript.

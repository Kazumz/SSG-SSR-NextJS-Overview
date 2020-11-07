# Overview
This repository has been created to demonstrate the differences between CSR (Client-side rendering) and an SSG (Static-site generation) / SSR (Server-side rendering) approach when creating React applications.

In order to understand the benefits of SSG / SSR, we must first look at what CSR is and what the differences between the two approaches are.

## Client Side Rendering (CSR)
Since the internet's inception, it's followed a fairly consistent pattern of what happens when a user visits a website. When you visit a website, you're actually downloading the content of that website from the server. For example, visting a website that contains a single HTML page with some lorem ipsum text on it would yield somewhat the following process:
- Visit Website
- Download HTML content (GET)
- Upon completion, your browser will "paint/render" this for you on screen. The HTML instructs the browser how to display this particular page. 

It's as simple as that. However over the years since the inception of the internet, web applications have become a thing; they're no longer just simple web pages but a web of complexities as businesses and developers push the boundaries. There are many libaries and frameworks that assist you in developing more complex websites, some like Razor/MVC. However, the web is now moving to single page applications and this is where we run in to a problem.

Due to the way SPA's (Single-page applications) work, the JavaScript that the user has to download when visiting your website increases dramatically. Whereas with a non-SPA application you'd be downloading large lumps of HTML when navigating between pages, in an SPA you'll be downloading large lumps of JavaScript that dynamically creates HTML and writes that to the DOM for you instead. This means that not only do you now have to download a large amount of JavaScript, your browser also has to run the JavaScript and write the output of that to the DOM. It's more intensive than simply downloading an already constructed HTML page. 

For the rest of this overview, we'll be focusing on React which is a library for creating SPA's.

### Create React App
(https://create-react-app.dev/docs/getting-started/)
Create React App (CRA) is a great template for getting up and running with React fast. React in itself is NOT a framework, it is a library. CRA as a template does not take that away from you, it simply abstracts the setup from you and provides you with a good simple base for your new React application.

In most cases when developing modern SPA's, you simply do not need to go further than Create React App. As React is a libary and not a framework, it by default is executed in a CSR manner. The user downloads the JavaScript bundles containing your React logic when visiting your website, React kicks in, your DOM is written to. 

### What happens with someone visits a website?
- Download HTML, CSS, and JavaScript bundles.
![Client Side Rendering](https://miro.medium.com/max/700/1*CRiH0hUGoS3aoZaIY4H2yg.png)

- User is shown the default index.html "You must use JavaScript to view this Website" page.
- The default page is overwritten by the index.js(ts) ReactDOM.Render() and any child components.

## Credits
https://medium.com/walmartglobaltech/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8#:~:text=The%20main%20difference%20is%20that,with%20links%20to%20your%20javascript.

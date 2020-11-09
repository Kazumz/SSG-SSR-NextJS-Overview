# Overview
This repository has been created to demonstrate the differences between CSR (Client-side rendering) and an SSG (Static-site generation) / SSR (Server-side rendering) approach when creating React applications.

In order to understand the benefits of SSG / SSR, we must first look at what CSR is and what the differences between the two approaches are.

## Client Side Rendering (CSR)
Since the internet's inception, it's followed a fairly consistent pattern of what happens when a user visits a website. When you visit a website, you're actually downloading the content of that website from the server. For example, visting a website that contains a single HTML page with some lorem ipsum text on it would yield somewhat the following process:
- Visit Website
- Download HTML content (GET)
- Upon completion, your browser will "paint/render" this for you on screen. The HTML instructs the browser how to display this particular page. 

It's as simple as that. However over the years since the inception of the internet, web applications have become a thing; they're no longer just simple web pages but a web of complexities as businesses and developers push the boundaries. There are many libaries and frameworks that assist you in developing more complex websites, some like Razor/MVC. However, the web is now moving to single page applications and this is where we run in to a problem.

Due to the way SPA's (Single-page applications) work, the JavaScript that the user has to download when visiting your website increases dramatically. Whereas with a non-SPA application you'd be downloading large lumps of already constructed HTML when navigating between pages from the server or some sort of blob storage, in an SPA you'll be downloading large lumps of JavaScript that dynamically creates HTML and writes that to the DOM for you instead. This means that not only do you now have to download a large amount of JavaScript, your browser also has to run the JavaScript and write the output of that to the DOM. It can be far more intensive than simply downloading an already constructed HTML page. 

Much of what the server used to do for you, where the horsepower is, is now happening in the user's browser. As an example, with an Razor / MVC application, you'd perform your intensive calculations server side and return a View (HTML). All the user's browser then needs to do is display it.

For the rest of this overview, we'll be focusing on React which is a library for creating SPA's.

### Create React App
(https://create-react-app.dev/docs/getting-started/)

Create React App (CRA) is a great template for getting up and running with React fast. React in itself is NOT a framework, it is a library. CRA as a template does not take that away from you, it simply abstracts the setup from you and provides you with a good simple base for your new React application.

In most cases when developing modern SPA's, you simply do not need to go further than Create React App. As React is a libary and not a framework, it by default is executed in a CSR manner. The user downloads the JavaScript bundles containing your React logic when visiting your website, React kicks in, your DOM is written to. 

### What happens with someone visits a CSR React application?
![Client Side Rendering](https://miro.medium.com/max/700/1*CRiH0hUGoS3aoZaIY4H2yg.png)
- Download HTML, CSS, and JavaScript bundles.
- User is shown the default index.html "You must use JavaScript to view this Website" page.
- The default page is immediately overwritten by the index.js(ts) ReactDOM.Render() and any child components. This happens syncronously.

## Static Site Generation and Server Side Rendering
The difficult thing understanding these two topics is the layers of abstraction introduced by frameworks that try to solve the aforementioned issues with CSR. This is also where things become far more complex than developing against standalone React as a library in the client vs frameworks that integrate React in the server. Your server is no longer serving up HTML, JavaScript bundles etc; it's actually performing logic in the server using this approach as well as serving up HTML and JavaScript bundles.

I'll use Next.js as an example of utilising SSG and SSR here. Next.js is something I'm interested in as a framework for solving the issues with CSR. Next.js follows similar concepts of Razor/MVC, but running in a Node.js environment.

### Next.js
https://nextjs.org/

Next is a modern server based framework that runs inside of Node.js and serves up React based content.

### Static Site Generation
The beauty of SSG is what happens when you build your application. Whereas with CSR the JavaScript is downloaded and then HTML is rendered to the DOM, with SSG this happens at build time. How mind blowing is that?! The component that you wrote in React that just contains some JSX and is stateless is now forever a static HTML page served up over and over. The user's machine never needs to render this page out itself, it's served up from the server as plain old HTML. In theory, there was little to no work that the user's browser had to perform to display this page. 

A great way to think about SSG is that when you build your application, a "preview" is generated for that component. The user is shown the "preview" for that component before React performs reconciliation itself in the browser to determine if there's anything additional to do now that we're in the user's browser. This is because you're not able to do everything you need to do server side such as accessing some browser based API's. Subsequent state changes that occur in the component also occur client-side.

With a framework like Next, this is how all of the React components are built. SSR is mearly an addition to this.

### Server Side Rendering
In addition to SSG, we may not always want to serve up static HTML to a user, we may want to calculate something at request time. When a request for the page hits the Node server and ultimately our hosted Next app, we have the ability to intercept and dynamically create the page that's about to be given and displayed to the user. This is more intensive for the server, but the benefit of this is that we can easily scale our server which is something we're not able to do with a user's browser.

As with SSG, React will still perform reconciliation when in the browser as you may not have access to everything you need server side such as accessing some browser based API's.

### What happens when someone visits a SSG/SSR React application?
![Server Side Rendering](https://miro.medium.com/max/700/1*jJkEQpgZ8waQ5P-W5lhxuQ.png)
- Download HTML (either generated via SSG or SSR), page is displayed to the user.
- Download JavaScript
- React reconciliation, writing any additional HTML to the DOM if required.

## Conclusion
Pick wisely, using server side frameworks like Next.js is much more complex than CSR and a CRA setup. Is it worth your time and the additional overhead? Many web applications out there are not intensive enough to justify using Next or SSG/SSR and will get little to no benefit with all of the extra complexity.

Fundamentally, the only reason to use a server side framework like Next.js are:
- Intensive calculations can happen server side.
- The user will see the page content earlier as we do not need to wait to download the JavaScript bundles. However, this can be mitigated by lots of approaches using CSR and may not actually make a difference if your components are constructed in a way that they rely on browser API's.

## Credits
https://medium.com/@lexgrigoryan

# Web Programming

## Practical Web Design

### Evolution of Web Design
* <strong>The first ever website : The beginning of the World Wide Web</strong>
  * <a href="http://info.cern.ch/" target="_blank">http://info.cern.ch/</a>
* <strong>Table-based layouts : Introducing table markup in HTML</strong>
  * Texts and images were dancing across websites everywhere
* <strong>Introduction of Flash: The renaissance of web design </strong>
  * Adobe Flash : Designers were able to add animation, custom fonts and shapes, 3D buttons, splash pages
* <strong>CSS : A new way of designing websites</strong>
  * Cascading Style Sheets (CSS)
  * CSS defines how the HTML is displayed
  * Better SEO
* <strong>Web 2.0: JavaScript</strong>
  * A new intelligence for web
* <strong>The rise of the mobile: The boom of mobile web design </strong>
  * In 2016, mobile and tablet internet usage exceeded desktop usage
* <strong>Responsive web design: Designing for mobile and desktop</strong>
  * use the same content, but a different layout for the design on each screen
* <strong>Flat design: The rise of a new design trend </strong>
  * opposite of rich design
  * No gradient, drop shadows, textures, and any type of design that makes it look real and three dimensional

### Web Design and its Components
* <strong>Grids</strong>
  * Responsive design
  * Grids used since print design, for books, publications, and especially magazines
* <strong>Call to Action</strong>
  * Encourages an action from the user, end goal (sale)
  * Make it big, obvious, and stand out
* <strong>Breadcrumb</strong>
  * Hansel and Gretel
  * breadcrumb in web allows the user to find their way back from where they started
* <strong>Search bar</strong>
* <strong>Icons</strong>
* <strong>Modal</strong>
  * Modal boxes are generally pop-up windows that appear on the screen rather than opening a new tab/window
* <strong>Typography</strong>
  * Serif fonts -- Times New Roman, Baskerville, Georgia, Garamond
  * Sans-serif -- Arial, Helvetica, Futura, or Gotham
  * Casual scripts
  * Monospace – Consolas, Courier, Monaco
* <strong>Colors</strong>
  * color meaning
* <strong>Usability</strong>
  * how easy the user interface is to use
* <strong>Simplicity</strong>
* <strong>Navigability</strong>
* <strong>Accessibility – Uptime, No Broken links</strong>
* <strong>Consistency</strong>
  * <strong>Design </strong>
    * Every element you create such as links, buttons, inputs, or titles should follow a design identity of your own
  * <strong>Content </strong>
    * Mood and tone used on the website have to reflect the brand
  * <strong>Interaction</strong> 
    * Website is responding to a user's interaction should always be consistent and remain the same

### Website-Designing Workflow
* <strong>Goal identification: how to identify our goal</strong> 
* <strong>Scope definition: List out the scope </strong> 
  * Clients' expectations and your expectations are not the same
* <strong>Wireframe creation</strong> 
  * How to create wireframes simple rectangles with your favorite design application, or you can even sketch it by hand
* <strong>Designing: Framework to create a great design</strong> 
  * Get inspiration, Improve, Invent
* <strong>Implementing, testing, and launching</strong> 

### Goal identification
* What is the purpose of the website?
* Who is the website for?
* Is this useful for our audience?
* What do they expect to find or do there?
* Does the website need to follow a brand or have its own brand identity?
* Are there any competitors? If there are, how is the website different than others?

### Sample Website
* Homepage
* Upcoming events page
* Past events page
* Event page details
* Blog page
* About Us page
* Contact page
* Login page

![image](https://user-images.githubusercontent.com/64727012/170271983-b96236b2-d5a9-4cc9-bd75-6d6553c8cbad.png)

### Responsive vs. Adaptive Design
* <strong>Responsive design</strong>
  * New way of designing for the desktop, and also for the mobile interface
  * Use the same content, but a different layout for the design on each screen
  * Create a universal look and feel with one design that varies from device to device

![image](https://user-images.githubusercontent.com/64727012/170272565-6dcf563e-026c-4c16-9c4f-6fee2933ead5.png)


* <strong>Adaptive design</strong>
  * detect the user device and to redirect the user to a website designed especially for this resolution
  * <a href="https://www.amazon.com" target="_blank">Amazon.com</a>

#### Responsive design Pros and Cons
![image](https://user-images.githubusercontent.com/64727012/170272749-e9743dd3-18e9-40f1-85a1-9aceceb25124.png)

#### Adaptive design Pros and Cons
![image](https://user-images.githubusercontent.com/64727012/170272804-5c873d9c-d09f-44e0-a9d9-20db3c1134fb.png)

### CSS box model
![image](https://user-images.githubusercontent.com/64727012/170273587-d53e6304-211f-4564-b589-82d945193838.png)

### What is Bootstrap?
* <strong>Bootstrap</strong> is an open source HTML, CSS, and JS library that helps you build websites and apps very easily
* <strong>Bootstrap Grid system</strong> 
* <strong>Bootstrap navigation</strong> 

### Server-side vs. Client-side rendering
* <strong>What is a server-side rendering?</strong> 
  * a request to the server is made, and it renders the website in HTML
  * <strong>Pro :</strong>
    * Better SEO because search engines can crawl the site
    * The initial page loads faster
    * Good for static sites
  * <strong>Cons :</strong>
    * Frequent server requests
    * Slower rendering
    * Page has to reload every time
* <strong>What is a client-side rendering?</strong>
  * rendered with JavaScript. Instead of getting the HTML by itself, you're getting a simple HTML structure but with JavaScript to render the rest of the HTML with your browser
  * AngularJS, ReactJS, VueJS
  * <strong>Pro :</strong>
    * Faster rendering after the initial load
    * Good for web applications
    * Fewer requests to the server
  * <strong>Cons :</strong>
    * Bad SEO if not implemented correctly
    * The initial load may require more time
    * Requires an external library in most cases

## Web Coding & Development All-in-One For Dummies

### How the web works
1. You tell the web browser the web page you want to visit
2. The browser decodes the URL – DNS(host name to IP Address)
3. The browser contacts the web server and requests the web page
4. The web server decodes the page request
5. The web server sends the web page file to the web browser
6. The web browser decodes the web page file
7. If the web page requires more resources, the web browser asks the server to pass along those resources
8. For each of the requested resources, the web server locates the associated file and sends it to the browser
9. The web browser gathers up all the text, images, and other resources and
10. displays the page in all its digital splendor in the browser’s content window

![image](https://user-images.githubusercontent.com/64727012/170277284-065f85fe-b676-422a-bcf9-7f873f080372.png)

* <strong>Front-end</strong>
  * That part of the web page that the web browser displays in the browser window. That is, it’s the page stuﬀ you see and interact with.
  * HTML, CSS
* <strong>Back-end</strong>
  * That part of the web page that resides on the web server. That is, it’s the page stuﬀ that the server gathers based on the requests it receives from the browser
  * PHP, MySQL
* <strong>Front-end, meet Back-end: JavaScript</strong>
  * jQuery

### How Dynamic Web Pages Work
* JavaScript determines the data that it needs from the server
* JavaScript sends a request for that data to the server
* The PHP script receives the request and passes it along to MySQL
* MySQL uses the SQL command to extract the required information from the database and then return that data to the PHP script
* The PHP script manipulates the returned MySQL data into a form that JavaScript can use
* PHP sends the JSON data back to JavaScript
* JavaScript displays the data on the web page

### What is a Web App?
> It’s actually something very similar to an app on a device or PC. That is, it’s a website, built using web technologies such as HTML, CSS, and JavaScript. A web app is a website that looks and acts like an app on a device or computer
*  The web app is focused on a single topic or task
*  The web app oﬀers some sort of interface that enables the user to operate the app in one or more ways



<strong>Reference</strong>
* "Practical Web Design"

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

### Local Web Development Environment
* <strong>integrated development environment (IDE) – Eclipse, STS</strong>
* <strong>A web server – Apache2, Tomcat, NginX</strong>
* <strong>A relational database management system (RDBMS) – MySQL, Postgresql</strong>
* <strong>A server-side programming language – PHP, Java, Python, JavaScript</strong>
* <strong>An interface for controlling (starting, stopping, and so on) the web server</strong>
* <strong>An interface for accessing and manipulating the RDBMS – PHPMyAdmin, MySQL Workbench</strong>

### XAMPP for Windows Development Environment
* <strong>Apache:</strong> This is an open-source web server that runs about half of all the websites on Earth
* <strong>MariaDB:</strong> This is an open-source server database that is fully compatible with MySQL
* <strong>PHP:</strong> This is the server-side programming language
* <strong>phpMyAdmin:</strong> This is an interface that enables you to access and manipulate MariaDB databases
* <strong>Linux</strong> -- LAMP

### Web Hosting Providers
* Free hosting provider – wordpress.com
* Commercial hosting provider
  1. Storage space
  2. Bandwidth
  3. Domain name -- GoDaddy or Register.com
  4. Email addresses
  5. Shared server, Dedicated server – Cloud, Virtual Machine
  6. Operating system -- Unix (or Linux) and Windows Server
  7. Databases
  8. Uptime 
  9. Tech support
  10. FTP support
  11. Website statistics
  12. Ecommerce
  13. Scalability
<br/>
<br/>
<br/>

### ...HTML tags, and CSS skip ...

<br/>
<br/>
<br/>

### What Can You Do with JavaScript?
* You can ask a web server for data and then display that data on your page
* You can add, modify, or remove page text, HTML tags, and even CSS properties
* You can display messages to the user and ask the user for info
* You can “listen” for and then perform actions based on events such as visitors clicking their mouse or pressing a key
* You can send the user’s browser to another page
* You can validate the values in a form before submitting it to the server
* You can collect, save, and retrieve data for each of your users, such as site
* customizations

### What Can’t You Do with JavaScript?
* It can’t write data permanently to an existing file. For example, you can’t take the data from a guest book and add it to a page that displays the messages
* It can’t access files on the server
* It can’t get any information about the user, including email or IP addresses
* It can’t submit credit card–based purchases for authorization and payment
* It can’t create multiplayer games
* It can’t get data directly from a server database
* It can’t handle file uploads

<br/>
<br/>
<br/>

### ...Javascript code, and jQuery skip ...

<br/>
<br/>
<br/>

### Reactive Pages with Events
* What’s an event?
  * Loading the page
  * Clicking a button
  * Pressing a key
  * Scrolling the page
* Event handler
  * Event listener: An instruction to the web browser to watch out for (“listen” for) a particular event occurring on a particular element
  * Callback function: The code that the web browser executes when it detects that the event has occurred

#### Event Types
* <strong>Document:</strong> Events that fire in relation to the loading of the document object
* <strong>Mouse:</strong> Events that fire when the user does something with the mouse
* <strong>Keyboard:</strong> Events that fire when the user interacts with the keyboard
* <strong>Form:</strong> Events associated with web page forms
* <strong>Browser window:</strong> Events that fire when the user interacts with the browser window

## Responsive Web Design by Example

### What is Responsive Web Design?

* Responsive design philosophy
* Responsive design principles
* Responsive versus adaptive
* Screen resolution
* Media queries
* Relative units
* Maximum and minimum values
* Mobile or desktop first
* Bitmaps versus vectors
* Responsive grids and columns

### What is Bootstrap, Why Do We Use It?
* Brief history 
  * In 2011, Bootstrap was created by two Twitter employees 
  * In early 2012 after a lot of contributions from the core team and the community, Bootstrap 2 was born
  * In 2013, Bootstrap 3 was released with a mobile-first approach
  * Current version, Bootstrap 4
*  Why use Bootstrap?
  * A responsive grid 
  * Cross browser compatibility -- Normalize.css 
  * Various UI components
  * Extremely easy to start using Bootstrap in your website
  * Bundles common JavaScript plugins such as jQuery
  * Customizable, allowing you to remove any unnecessary features 

#### Bootstrap's grid system
* <strong>Columns</strong>: These are the horizontal containers for storing content on a single row
* <strong>Rows</strong>: These are top level containers for storing columns

![image](https://user-images.githubusercontent.com/64727012/170705356-7a16c87c-c30a-40d0-96f7-c083f21772ea.png)

* <strong>Basics</strong>
  * Two Column Types
    * .container -- Used for a fixed width
    * .container fluid -- Used for full width to span the entire browser
  * Row -- used to horizontally group columns
    * .row
* <strong>Suppose a row is 12 columns</strong>
  * .col-6: Spans six columns on all screen sizes
  * .col-md-6: Spans six columns only on medium screen sizes
* <strong>Column Width</strong>

![image](https://user-images.githubusercontent.com/64727012/170705806-e56f4a2d-0dc8-4838-895c-0ff2fb40a83c.png)

#### Usage and Example
* <strong>Equal width columns example</strong>

![image](https://user-images.githubusercontent.com/64727012/170706157-083f5558-58b3-4cce-a266-b328eb94d13b.png)

* <strong>Multi-row, equal-width columns example</strong>
 
![image](https://user-images.githubusercontent.com/64727012/170706168-15f40418-5285-417c-ae36-02d50842bde9.png)

* <strong>Multi-row, equal-width columns without multiple rows example</strong>

![image](https://user-images.githubusercontent.com/64727012/170706178-4a0f2706-b87c-4cd8-8d09-24ae9b802683.png)

* <strong>Differently sized columns</strong>

![image](https://user-images.githubusercontent.com/64727012/170706297-1eb8ba74-3743-4bc2-b617-c57ef73add46.png)

* <strong>Mixing and matching</strong>

![image](https://user-images.githubusercontent.com/64727012/170707581-96d2b1db-2c15-4d6e-a1c5-3e5e4f0171a4.png)

### Reusable Project Template

#### What is a reusable project template?
* Include HEADER_FILE
* Main content for page
* Include FOOTER_FILE

#### Development environment prerequisites
* <strong>XAMPP</strong>
  * OS – macOS, Windows, Linux
  * Apache2
  * MySQL – Changed to MariaDB
  * PHP, Perl
* <strong>Install to Ubuntu 16.04</strong>
  * Install Apache2
  * Install mysql
  * Install php 7
  * $ sudo apt-get install libapache2-mod-php7.0
  * /var/www/html/phpinfo.php
  * After make <?php phpinfo(); ?>, check in Web Browser http://localhost/phpinfo.php

#### Responsive Versus Adaptive Design
* <strong>Responsive design</strong>
  * new way of designing for the desktop, and also for the mobile interface
  * use the same content, but a different layout for the design on each screen
  * create a universal look and feel with one design that varies from device to device
* <strong>Adaptive design</strong>
  * detect the user device and to redirect the user to a website designed especially for this resolution
  * <a href="https://www.amazon.com" target="_blank">Amazon.com</a>

#### Abstraction
1. index.html to index.php
2. Create a folder called SNIPPETS, with two PHP files HEADER.php and FOOTER.php

![image](https://user-images.githubusercontent.com/64727012/170709755-e3c88ebd-d2d3-4865-901d-12a0beaf0fc6.png)

### Creating the Introduction Section
* <strong>Single-page website</strong>
  * A website with only a single page split into sections, using buttons to anchor to the different sections
  * Ex) <a href="https://www.kitkat.com/android/">https://www.kitkat.com/android/</a>
* <strong>Used in</strong>
  * Portfolio
  * Landing page
  * Coming soon page
  * App page
  * Simple gallery
  * Product page

### Jumbotron

* Feature of Bootstrap
* Big displays that are used at sporting events
* Implementing a basic jumbotron

![image](https://user-images.githubusercontent.com/64727012/170710639-9c5bd278-c9f0-4c07-8e90-b4e69f77fd26.png)

### Creating a Generic Reusable Single Page Section
* <strong>Different sections in single page websites</strong>
  * Contact form
  * About us
  * Projects/work
  * Useful company info such as opening times

## Flask : Building Python Web Services

### Creating development environment
* <strong>Install Python</strong>
  1. Install Anaconda3
  2. jupyter-notebook --generate-config
  3. conda install virtualenv
  4. conda create –n flask
  5. pip install mysql-connector

### Flask
* <strong>Flask</strong> is a micro framework for Python web development
* <strong>Django</strong> -- "fuller" framework, has own ORM
* hello.py
```python
from flask import Flask
app = Flask(__name__)
@app.route("/")
def index():
    return "Hello, World!"
if __name__ == '__main__':
    app.run(port=5000, debug=True)

```

![image](https://user-images.githubusercontent.com/64727012/170809148-5bb0832c-4415-428e-a90b-9909560a4c63.png)

#### Using Templates in Headlines Project
* <strong>Jinja</strong> -- Python template engine. We can easily define dynamic blocks of HTML which are populated by Python
* Flask was built on top of Jinja
* templates directory
<br/>

* <strong>home.html</strong>

```html
<html>
  <head>
    <title>Headlines</title>
  </head>
  <body>
    <h1>Headlines</h1>
    <b>{{title}}</b><br />
    <i>{{published}}</i><br />
    <p>{{summary}}</p>
  </body>
</html>
```

* <strong>python code</strong>
```python
@app.route("/")
@app.route("/<publication>")
def get_news(publication="bbc"):
    feed = feedparser.parse(RSS_FEEDS[publication])
    first_article = feed['entries'][0]
    render_template("home.html",
				title=first_article.get("title"),
				published=first_article.get("published"),
				summary=first_article.get("summary"))

```


* <strong>Advanced Jinja templates</strong>

  * <strong>python code</strong>
   ```python
   render_template("home.html", articles=feed['entries'])
   ```
  * <strong>home.html</strong>
   ```html

   <html>
       <head>
           <title>Headlines</title>
       </head>
       <body>
           <h1>Headlines</h1>
           {% for article in articles %}
               <b><a href="{{article.link}}">{{article.title}}</a></b><br />
               <i>{{article.published}}</i><br />
               <p>{{article.summary}}</p> 
               <hr />
           {% endfor %}    
       </body>
   </html>

   ```

#### User Input for Headlines Project
* Getting user input using HTTP <strong>GET</strong>
  * localhost:5000/?publication=bbc
* Getting user input using HTTP <strong>POST</strong>
  * used to post larger chunks of data or more sensitive data to the server
  * not visible in the URL

* <strong>headlines.py</strong>

```python

from flask import render_template
from flask import request
import json
import urllib
import urllib.request
WEATHER_URL = "http://api.openweathermap.org/data/2.5/weather?q={}&units=metric

publication = request.args.get('publication’)

city = request.args.get('city’)
query = urllib.parse.quote(city)
url = WEATHER_URL.format(query)
data = urllib.request.urlopen(url).read()
parsed = json.loads(data.decode('utf-8'))

```

* <strong>home.html</strong>
  * By default, this will create an HTTP GET request when submitted, by passing any inputs as GET arguments into the URL

```html

<form>
  <input type="text" name="query" placeholder="search" />
  <input type="submit" value="Submit" />
</form>
<form>
  <input type="text" name="city" placeholder="weather search">
  <input type="submit" value="Submit">
</form>

```

#### Getting user input using HTTP POST
* request.args.get -> request.form.get
* @app.route("/") -> @app.route("/", methods=['GET','POST’])
  * By default, only GET is permitted

* HTML form use POST
```html

<form action="/" method="POST">

```

#### Parsing JSON with Python

```python

import json
…
parsed = json.loads(data.decode('utf-8'))
weather = None
if parsed.get('weather'):
    weather = {'description': parsed['weather'][0]['description'],
                   'temperature': parsed['main']['temp'],
                   'city': parsed['name'],
                   'country': parsed['sys']['country']
                   }

```

* <strong>weather.json</strong>

```json

{
 "coord":{"lon":-0.13,"lat":51.51},
 "weather":[{"id":801,"main":"Clouds","description":"few clouds","icon":"02n"}], 
 "base":"stations",
 "main":{"temp":17.98,"pressure":1019,"humidity":77,"temp_min":15,"temp_max":21},
 "visibility":10000, 
 "wind":{"speed":0.5},
 "clouds":{"all":20}, "dt":1534819800, 
 "sys":{"type":1,"id":5091,"message":0.0052,"country":"GB","sunrise":1534827333,"sunset":1534878637}, 
 "id":2643743, "name":"London","cod":200
}


```

### Improving the User Experience 
* Adding cookies to our Headlines application
* Adding CSS to our Headlines application

#### Using cookies with Flask
* <strong>Setting cookies in Flask</strong>

```python
import datetime
from flask import make_response
…
response = make_response(render_template("home.html", articles=articles,
                                     weather=weather, currency_from=currency_from,
                                     currency_to=currency_to, rate=rate, 
                                     currencies=sorted(currencies)))
expires = datetime.datetime.now() + datetime.timedelta(days=365)
response.set_cookie("publication", publication, expires=expires)
response.set_cookie("city", city, expires=expires)
response.set_cookie("currency_from", currency_from, expires=expires)
response.set_cookie("currency_to", currency_to, expires=expires)
return response

```

* <strong>Retrieving cookies in Flask</strong>

```python
publication = request.cookies.get("publication")
```

* <strong>Fallback Logic – Finding Default Value</strong>
```python
def get_value_with_fallback(key):
    if request.args.get(key):
        return request.args.get(key)
    if request.cookies.get(key):
        return request.cookies.get(key)
```

### Cookies vs Session in Flask

* <strong>Session</strong>
  * Object which allows you to store information specific to a user from one request to the next. 
  * Implemented on top of cookies
  * Simmilar to cookies, but use like dictionary of python.

```python

app.secret_key = 'You Will Never Guess'
@app.route('/setuser/<user>')
def setuser(user):
    session['user'] = user
    return 'User value set to: ' + session['user']
@app.route('/getuser')
def getuser():
    return 'User value was previously set to: ' + session['user’]

```

### Building RESTful APIs
![image](https://user-images.githubusercontent.com/64727012/170810398-1384fa6b-47c8-41df-b4df-8279fb3995ee.png)

#### HTTP codes used in REST 

![image](https://user-images.githubusercontent.com/64727012/170810404-9362519e-caf8-4c00-94bd-afe12860d838.png)

#### Using Flask-RESTful

* Flask-RESTful is an extension for Flask that adds support for quickly building REST APIs
* pip install flask-restful
* from flask_restful import Resource, Api

* <strong>RestHelloWorld.py</strong>
```python

from flask import Flask
from flask_restful import Resource, Api
app = Flask(__name__)
api = Api(app)

class HelloWorld(Resource):
    def get(self):
        return {'hello': 'world'}
api.add_resource(HelloWorld, '/')

if __name__ == '__main__':
    app.run(debug=True)

```

![image](https://user-images.githubusercontent.com/64727012/170810483-15632fda-d920-4ed9-bd63-63ad096e62c5.png)

### URI Format

* URI = scheme "://" authority "/" path [ "?" query ] [ "#" fragment ]
* Rule: A trailing forward slash (/) should not be included in URIs
* Rule: Hyphens (-) should be used to improve the readability of URIs
* Rule: Underscores (_) should not be used in URIs
* Rule: Lowercase letters should be preferred in URI paths
  1. http://api.example.restapi.org/my-folder/my-doc
  2. HTTP://API.EXAMPLE.RESTAPI.ORG/my-folder/my-doc
  3. http://api.example.restapi.org/My-Folder/my-doc
  * First, Second are same, Third is different


<strong>Reference</strong>
* Philippe Hong, "Practical Web Design"
* Frahaan Hussain, "Responsive Web Design by Example"
* Paul McFedries, "Web Coding & Development All-in-One For Dummies"
* Jack Stouffer, Gareth Dwyer, Shalabh Aggarwal, "Flask: Building Python Web Services"

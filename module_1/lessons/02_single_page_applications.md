# A History of SPAs

The path to creating single-page applications (SPAs) for the Web was a long one. Knowing the path that Web developers took to get to them can help us understand the shape that they take, today. So, come along on the journey of Web evolution.

## The First Step: Data Without Reloading

In the old days, Web developers created applications that consisted of many different HTML pages sent to the browser linked together through actions that a person could take by clicking on `<a>` tags or by submitting content through `<form>` elements. From an [article on Wikipedia](https://en.wikipedia.org/wiki/Ajax_(programming)):

> In the early-to-mid 1990s, most Web sites were based on complete HTML pages. Each user action required that a complete page be loaded from the server. This process was inefficient, as reflected by the user experience: all page content disappeared, then reappeared. Each time the browser reloaded a page because of a partial change, all of the content had to be re-sent, even though only some of the information had changed. This placed additional load on the server and made bandwidth the limiting factor on performance.

As browsers became more powerful, Web developers took advantage of the increased functionality offered by JavaScript. In 1999, Microsoft took advantage of JavaScript's potential and invented the `XMLHttpRequest`, a way for programmers to use JavaScript to get data from an *Application Programming Interface* (API) without the browser having to reload the page. For more than five years, programmers discovered and used this new functionality without a common way to talk about it. In 2004 and 2005, Google widely published its Gmail and Google Maps Web applications that relied heavily on the `XMLHttpRequest` object. In a [paper describing the new
Web applications](https://web.archive.org/web/20080702075113/http://www.adaptivepath.com/ideas/essays/archives/000385.php), Jesse James Garrett coined the term *AJAX* to label the programming model of using `XMLHttpRequest`.

## The Second Step: Rendering Data

Now that Web developers had AJAX, they could get data from an API. As you may guess, Microsoft originally intended the `XMLHttpRequest` to return data formatted as XML documents. Once an application received some XML from an `XMLHttpRequest`, something like

```xml
<book title="Lord of Light"
      isbn="0060567236"
      xlink:href="/books/18721612"
      year-published="1967">
  <authors>
    <author firstName="Roger"
            lastName="Zelazny"
            xlink:href="/authors/83730" />
  </authors>
  <cover-images>
    <image height="400"
           width="300"
           xlink:href="http://cdn.example.com/askdfasdkf"
           rel="large" />
  </cover-images>
</book>
```

then a Web developer could write code to transform that into HTML like

```html
<div class="book">
  <div class="book-image">
    <img height="400"
         width="300"
         src="http://cdn.example.com/askdfasdkf">
  <h4 class="book-title">
    <a href="/books/18721612">Lord of Light</a>
  </h4>
  <div class="book-author">
    <a href="/authors/83730">Zelazny, Roger</a>
  </div>
</div>
```

The problem with this method is two-fold: XML is ugly and programmers didn't seem to like it, and to transform XML into HTML usually requires learning yet another not-so-fun language named XSLT. So, developers went in search of a different format for the data that they could use and found it in JSON. They could use just regular old JavaScript to use the data in JSON to create new entries in the DOM with the received information. But, that, too became arduous and boring.

When confronted with arduous and boring tasks, most programmers will fight that icky feeling by creating something new to help them with their problems. Most had used some sort of server-side templating language like [JSP](https://en.wikipedia.org/wiki/JavaServer_Pages) or [erb](https://en.wikipedia.org/wiki/ERuby) and decided that they could write one that would work in the browser using JavaScript and the DOM. Like daisies in a field, they sprang up all over the place.

## The Third Step: Data Binding

Now that developers could get data from a server and make pretty Web pages with it, the last problem they needed to solve was getting information from a person as that person interacted with the Web page. In 2010, a whole bunch of companies and open-source developers released well-tested and thorough libraries to address the data-binding needs of Web programmers.

These frameworks provided easy-to-use wrappers around the AJAX functionality in the browsers provided an easier-to-use templating system than more lower-level toolkits like jQuery, and bound user input automatically to the JavaScript objects that powered the Web application.


## The Final Step: Routing

The final step to getting to the SPA was an easy way for developers to allow the user to click a link or button and have the Web page change in such a way that it looked like a new page had loaded.

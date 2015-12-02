
#Javascript Libraries
Libraries give you access to code that someone else wrote. 

Let’s see how we can borrow a function by copying and pasting it into a javascript file.

### Using New Javascript Functions in HTML
Open this lesson on Github and clone the sample folder onto your local machine.  You should see
* an index.html page
* a javascript file called main.js - which is pretty empty.

 
We want to add a new function, `addListItem` to main.js
```
function addListItem(text){
  list = document.querySelector('ul');
  item = document.createElement('li');
  item.innerText = text;
  list.appendChild(item);
}
```

1. Copy and paste the above code into the main.js file
2. In index.html, you can now use addListItem

Fortunately, we don’t have to rely on copying and pasting in order to share code. In fact, copying and pasting code is really bad practice. Instead we can use external libraries. 


### Using External Libraries

We've seen that we can save our javascript in external files, then include them via `script` tags. This is a good engineering practice even when we aren’t using someone else’s code. Keeping functions in different files and loading them with `script` lets us see the different pieces of our app in the file structure.

To include javascript into your html page, use the `<script>` tag. When you want to use an external library, point the src attribute to the url of the library you want to use. Like this:
```html
<script src=“https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.4/jquery.js”></script>
```
Just like we can include our javascript, we can include someone else's javascript too! If you [click here](https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.4/jquery.js), you’ll find that it gives you a big page of javascript. When you add a script tag that links to that URL, all of that javascript becomes yours to use locally.

The link you clicked on is to the jQuery library, which provides a ton of methods that make writing javascript way easier - like the select `$()` and `.text()` methods that we saw in the Twitter example. jQuery takes a lot of common tasks that require many lines of JavaScript code to accomplish, and wraps them into methods that you can call with a single line of code.

If we want to use the methods from an external library, we first need to include that library into our html file with the `<script>` tag.
```
<body>

...all the html for the body elements…

<script src="http://path/to/library.js"></script>
<script src="your_file.js"></script>
</body>
```

Once the script tag loads that script, all the functions defined in that library are available for us to use - we can use them as if we created them ourselves.

###Libraries Make Things Easier

When we were looking at twitter and replacing names, we used
```
names = $('.fullname');
names.text('Your Name');
```
Without the jQuery library, we would have needed to do all this:
```
names = document.getElementsByClassName("fullname");
for ( i = 0 ; i < names.length() ; i++ ) {
     names[ i ].innerHTML = " [your name] "
}
```
It's a lot easier to use the jQuery library.

In native javascript, first we have to select all the fullname elements, then loop through them and change the innerHTML - now, we can do all that with one line!
```
$(''.fullname').text('Your Name')
```



There are tons of javascript libraries. A good place to find some of the more popular ones is [https://www.javascripting.com/](https://www.javascripting.com/). Today, we’ll practice using jQuery, so you can practice the workflow for using a library. In short, the steps are:
1. Find a library you want to use.
2. Include it with a `<script>` tag
3. Search the documentation for the function you need
4. Try it out
5. Repeat!

<a href='https://learn.co/lessons/cssi-3.3-js-libraries' data-visibility='hidden'>View this lesson on Learn.co</a>

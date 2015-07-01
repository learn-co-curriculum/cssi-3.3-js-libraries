---
tags: cssi, javascript, jquery
level: 2
languages: javascript
---
#Javascript Libraries
Libraries give you access to code that someone else wrote. We’ve been using the javascript standard library a lot - those are the functions that are available everywhere - standard. But what if we want to use code that somebody else wrote?

We have lots of smart friends, and they write awesome javascript all the time! We want to be able to use their code! And, when we write some awesome javascript, we want our friends to be able to use it!

Let’s see how we can borrow a cool function by copying and pasting it above our javascript.

Open up the sample folder and see that there is an index.html page, which links to a javascript file called main.js.

There's some useful javascript here:
```
function addListItem(text){
  list = document.querySelector('ul');
  item = document.createElement('li');
  item.innerText = text;
  list.appendChild(item);
}
```

To use it, copy and paste it into your main.js file, and then call the function for yourself. As you could guess, the code you copied and pasted gets run just like your own code. Fortunately, we don’t have to rely on copying and pasting in order to share code. Javascript, like most widely used languages, lets us rely on external libraries.

We've see that we can save our javascript in external files, then include them via `script` tags. This is a good engineering practice even when we aren’t using someone else’s code. Keeping functions in different files and loading them with `script` lets us see the different pieces of our app in the file structure.

##How do we use libraries?
To include javascript into your html page, use the `script` tag. When you want to use an external library, point the src attribute to the url of the library you want to use. Like this:
```html
<script src=“https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.4/jquery.js”></script>
```
Just like we can include our javascript, we can include someone else's javascript too! If you [navigate to the url above](https://cdnjs.cloudflare.com/ajax/libs/jquery/2.1.4/jquery.js), you’ll find that it gives you a big page of javascript. When you add that script tag, all of that javascript gets evaluated by the browser.

That particular link is to the jQuery library, which provides a ton of methods that make writing javascript way easier - like the select and `.text()` methods that we saw. jQuery takes a lot of common tasks that require many lines of JavaScript code to accomplish, and wraps them into methods that you can call with a single line of code.

If we want to use the methods, we need to make sure that script tag to load the library is included before we try to use it. That means putting the library script tag first in the html:

```
<body>

...all the html for the body elements…

<script src="http://path/to/library.js"></script>
<script src="your_file.js"></script>
</body>
```

Once the script tag loads that script, all the functions defined in that library are available for us to use - we can use them as if we defined them ourselves.

##Libraries make things easy

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
Way easier to use jQuery!

In native javascript, first we have to select all the fullname elements, then loop through them and change the innerHTML - now, we can do all that with one line!
```
$(''.fullname').text('Your Name')
```
Underneath, jQuery is just javascript. Let's find the `.text()` method in the jquery source to see that it's just a normal javascript method, one that we could have defined ourselves.

Open up the jQuery source and use command+f to search for the method. It turns out that jquery's .text() method is called Sizzle.getText() internally, until the name gets updated on line 5348:
```
jQuery.text = Sizzle.getText;
```

We can look up the Sizzle.getText method, and see that it's just javascript. If we wanted to understand what the code is doing for us, we could read it and figure it out.

Using libraries means that we can focus on our application, rather than reinventing the wheel. If there is something complicated that you want to do, and you think that other people needed to do it on their sites, there is probably a library with functions to help you.

There are tons of javascript libraries. A good place to find some of the more popular ones is [https://www.javascripting.com/](https://www.javascripting.com/). Today, we’ll practice using jQuery, so you can practice the workflow for using a library. In short, the steps are:
1. Find a library you want to use.
2. Include it with a <script> tag
3. Search the documentation for the function you need
4. Try it out
5. Repeat!

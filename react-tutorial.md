# what is JSX

JSX is a syntax extension for JavaScript. It was written to be used with React. JSX code looks a lot like HTML.

What does "syntax extension" mean?

In this case, it means that JSX is not valid JavaScript. Web browsers can't read it!

If a JavaScript file contains JSX code, then that file will have to be compiled. That means that before the file reaches a web browser, a JSX compiler will translate any JSX into regular JavaScript.
 
A basic unit of JSX is called a JSX element.

Here's an example of a JSX element:

`<h1>Hello world</h1>`

This JSX element looks exactly like HTML! The only noticeable difference is that you would find it in a JavaScript file, instead of in an HTML file.

JSX elements are treated as JavaScript expressions. They can go anywhere that JavaScript expressions can go.

That means that a JSX element can be saved in a variable, passed to a function, stored in an object or array...you name it.

Here's an example of a JSX element being saved in a variable:

    var navBar = <nav>I am a nav bar</nav>;

Here's an example of several JSX elements being stored in an object:

    var Pistons2004 = {
      center:        <li>Ben Wallace</li>,
      powerForward:  <li>Rasheed Wallace</li>,
      smallForward:  <li>Tayshaun Prince</li>,
      shootingGuard: <li>Richard Hamilton</li>,
      pointGuard:    <li>Chauncey Billups</li>
    };
    
 JSX elements can have attributes, just like HTML elements can.

A JSX attribute is written using HTML-like syntax: a name, followed by an equals sign, followed by a value. The value should be wrapped in quotes, like this:

    my-attribute-name="my-attribute-value"

Here are some JSX elements with attributes:

    <a href="http://www.yahoo.com">Welcome to the Yahoo</a>;

    var title = <h1 id="title">Introduction to React.js: Part I</h1>;

A single JSX element can have many attributes, just like in HTML:

    var panda = <img src="images/panda.jpg" alt="panda" width="500px" height="500px" />;
    
# what is nested JSX elements
 
You can nest JSX elements inside of other JSX elements, just like in HTML.

Here's an example of a JSX `<h1> element, nested inside of a JSX <a> element`:

    <a href="https://www.google.net"><h1>Click me I am Google</h1></a>

To make this more readable, you can use HTML-style line breaks and indentation:

    <a href="https://www.google.net">
      <h1>
        Click me I am Goooogle
      </h1>
    </a>

If a JSX expression takes up more than one line, then you should wrap the multi-line JSX expression in parentheses. This looks strange at first, but you get used to it:

    (
      <a href="https://www.google.net">
        <h1>
          Click me I am Goooooogle
        </h1>
      </a>
    )

Nested JSX expressions can be saved as variables, passed to functions, etc., just like non-nested JSX expressions can! Here's an example of a nested JSX expression being saved as a variable:

     var theGoogle = (
       <a href="https://www.google.net">
         <h1>
           Click me I am Gooooooooooogle
         </h1>
       </a>
     );

# Only one outermost JSX expression 

There's a rule that we haven't mentioned: a JSX expression 
must have exactly one outermost element.

In other words, this code will work:

    var paragraphs = (
      <div id="i-am-the-outermost-element">
        <p>I am a paragraph.</p>
        <p>I, too, am a paragraph.</p>
      </div>
    );

*But this code will not work:*

    var paragraphs = (
      <p>I am a paragraph.</p> 
      <p>I, too, am a paragraph.</p>
    );

you can wrap the same indent code with div tags like this example:

    var blog = (
      <div>
        <img src="pics/192940u73.jpg" />
        <h1>
          Welcome to Dan's Blog!
        </h1>
        <article>
          Wow I had the tastiest sandwich today.  I <strong>literally</strong> almost freaked out.
        </article>
      </div>  
    );
   
# what is ReactDOM

ReactDOM is the name of a JavaScript library. This library contains 
several React-specific methods, all of which deal with the DOM in 
some way or another.

ReactDOM.render is the most common way to render JSX. 
It takes a JSX expression, creates a corresponding tree of DOM nodes, and adds that tree to the DOM. 
That is the way to make a JSX expression appear onscreen.

    var React = require('react');
    var ReactDOM = require('react-dom');
    
    // Write code here:
    ReactDOM.render(<h1>Render me!</h1>, document.getElementById('app'));

`index.html`

You just learned that ReactDOM.render makes its first argument appear onscreen. But where on the screen should that first argument appear?

The first argument is appended to whatever element is selected by the second argument.

In the code editor, select index.html. See if you can find an element that would be selected by document.getElementById('app').

That element acted as a container for ReactDOM.render's first argument! At the end of the previous exercise, this appeared on the screen:

HTML CODE 

<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="utf-8">
	<link rel="stylesheet" href="/styles.css">
	<title>Learn ReactJS</title>
</head>

<body>
  <main id="app"></main>
	<script src="https://s3.amazonaws.com/codecademy-content/courses/React/react-course-bundle.min.js"></script>
  <script src="/app.compiled.js"></script>
</body>

</html>

# ReactDOM.render()

ReactDOM.render()'s first argument should evaluate to a JSX expression, it doesn't have to literally be a JSX expression.

The first argument could also be a variable, so long as that variable evaluates to a JSX expression.

In this example, we save a JSX expression as a variable named toDoList. We then pass toDoList as the first argument to ReactDOM.render:
    
    var toDoList = (
      <ol>
        <li>Learn React</li>
        <li>Become a Developer</li>
      </ol>
    );
    
    ReactDOM.render(
      toDoList, 
      document.getElementById('app')
    );


# ReactDOM rendering elements 
    
    var React = require('react');
    var ReactDOM = require('react-dom');
    
    // Write code here:
    var myList = ( 
                        <ul>
                  <li>Rakesh Sukla</li>
                  <li>Bikash Sukla</li>
                  <li>Ekansh Sukla</li>
                  <li>Ankita Sukla</li>
                        </ul>
                            )
    
    ReactDOM.render(
      myList, 
      document.getElementById('app')
    );

# Why react is so popular 

One special thing about ReactDOM.render is that it only updates DOM elements that have changed.

That means that if you render the exact same thing twice in a row, the second render will do nothing:

    var hello = <h1>Hello world</h1>;
    
    // This will add "Hello world" to the screen:
    
    ReactDOM.render(hello, document.getElementById('app'));
    
    // This won't do anything at all:
    
    ReactDOM.render(hello, document.getElementById('app'));

This is significant! Only updating the necessary DOM elements is a large part of what makes React so successful.

# What is VirtualDOM

When you render a JSX element, every single virtual DOM object gets updated.

This sounds incredibly inefficient, but the cost is insignificant because the virtual DOM can update so quickly.

Once the virtual DOM has updated, then React compares the virtual DOM with a virtual DOM snapshot that was taken right before the update.

By comparing the new virtual DOM with a pre-update version, React figures out exactly which virtual DOM objects have changed. This process is called "diffing."

Once React knows which virtual DOM objects have changed, then React updates those objects, and only those objects, on the real DOM. In our example from earlier, React would be smart enough to rebuild your one checked-off list-item, and leave the rest of your list alone.

This makes a big difference! React can update only the necessary parts of the DOM. React's reputation for performance comes largely from this innovation.

In summary, here's what happens when you try to update the DOM in React:

    The entire virtual DOM gets updated.
    The virtual DOM gets compared to what it looked like before you updated it. React figures out which objects have changed.
    The changed objects, and the changed objects only, get updated on the real DOM.
    Changes on the real DOM cause the screen to change.

If you'd like to learn more about the virtual DOM, here's a good place to star

# Common issues with JSX expression

Grammar in JSX is mostly the same as in HTML, but there are subtle differences to watch out for. Probably the most frequent of these involves the word class.
In HTML, it's common to use class as an attribute name:

    <h1 class="big">Hey</h1>

In JSX, you can't use the word class! You have to use className instead:

    <h1 className="big">Hey</h1>

This is because JSX gets translated into JavaScript, and class is a reserved word in JavaScript.
When JSX is rendered, JSX className attributes are automatically rendered as class attributes.

    var React = require('react');
    var ReactDOM = require('react-dom');
    
    // Write code here:
    var myDiv = <div className="big">I AM A BIG DIV</div>
    
    ReactDOM.render(myDiv, document.getElementById('app'))

# self closing tags in JSX

Most HTML elements use two tags: an opening tag (<div>), and a closing tag (</div>). However, some HTML elements such as <img> and <input> use only one tag. The tag that belongs to a single-tag element isn't an opening tag nor a closing tag; it's a self-closing tag.

When you write a self-closing tag in HTML, it is optional to include a forward-slash immediately before the final angle-bracket:

Fine in HTML with a slash:

      <br />
    
    Also fine, without the slash:
    
      <br>

But!

In JSX, you have to include the slash. If you write a self-closing tag in JSX and forget the slash, you will raise an error:

    Fine in JSX:
    
      <br />
    
    NOT FINE AT ALL in JSX:
    
      <br>

example 

    var profile = (
      <div>
        <h1>I AM JENKINS</h1>
        <img src="images/jenkins.png" >
        <article>
          I LIKE TO SIT
          <br/>
          JENKINS IS MY NAME
          <br/>
          THANKS HA LOT
        </article>
      </div>
    );
            
# Javascript inside JSX Expression
        
    var React = require('react');
    var ReactDOM = require('react-dom');
    
    // Write code here:
    ReactDOM.render(
      <h1>2 + 3</h1>,
      document.getElementById('app')
    );
            
you will see the output `2+3` instead of 5 because:
      
Any code in between the tags of a JSX element will be read as JSX, 
not as regular JavaScript! JSX doesn't add numbers - it reads them as text, 
just like HTML.
        
you should use `curly braces` for rendering javascript code inside a JSX expression
    
use of `curly braces`

    var React = require('react');
    var ReactDOM = require('react-dom');
    
    // Write code here:
    
    var math = <h1>2 + 3 = {2 + 3}</h1>
    
    ReactDOM.render(
        math,
        document.getElementById('app')
    );

# Javascript code from else where

When you inject JavaScript into JSX, that JavaScript is part of the same environment as the rest of the JavaScript in your file.

That means that you can access variables while inside of a JSX expression, even if those variables were declared on the outside.

    // Declare a variable:
    var name = 'Gerdo';
    
    // Access your variable 
    // from inside of a JSX expression:
    var greeting = <p>Hello, {name}!</p>;
 
    -------------------------------------------
    
    var React = require('react');
    var ReactDOM = require('react-dom');
    
    var theBestString = 'tralalalala i am da best';
    
    ReactDOM.render(<h1>{theBestString}</h1>, document.getElementById('app'));
        
# Setting Attributes to Variable

When writing JSX, it's common to use variables to set attributes.

Here's an example of how that might work:

// Use a variable to set the `height` and `width` attributes:

    var sideLength = "200px";
    
    var panda = (
      <img 
        src="images/panda.jpg" 
        alt="panda" 
        height={sideLength} 
        width={sideLength} />
    );

Notice how in this example, the <img />'s attributes each get their own line. This can make your code more readable if you have a lot of attributes on one element.

Object properties are also often used to set attributes:

    var pics = {
      panda: "http://bit.ly/1Tqltv5",
      owl: "http://bit.ly/1XGtkM3",
      owlCat: "http://bit.ly/1Upbczi"
    }; 
    
    var panda = (
      <img 
        src={pics.panda} 
        alt="Lazy Panda" />
    );
    
    var owl = (
      <img 
        src={pics.owl} 
        alt="Unimpressed Owl" />
    );
    
    var owlCat = (
      <img 
        src={pics.owlCat} 
        alt="Ghastly Abomination" />
    );

more examples 

    var React = require('react');
    var ReactDOM = require('react-dom');
    
    var goose = 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-goose.jpg';
    
    // Declare new variable here:
    var gooseImg = <img src={goose}/>
    
    ReactDOM.render(gooseImg, document.getElementById('app') )

# EventListener in React

list of all supported events can be found here 

`https://facebook.github.io/react/docs/events.html#supported-events`

JSX elements can have event listeners, just like HTML elements can. Programming in React means constantly working with event listeners.

You create an event listener by giving a JSX element a special attribute. Here's an example:

    <img onClick={myFunc} />

An event listener attribute's name should be something like onClick or onMouseOver: the word on, plus the type of event that you're listening for. You can see a list of valid event names here.

An event listener attribute's value should be a function. The above example would only work if myFunc were a valid function that had been defined elsewhere:

    function myFunc () {
      alert('Make myFunc the pFunc... omg that was horrible i am so sorry');
    }

    <img onClick={myFunc} />

Note that in HTML, event listener names are written in all lowercase, such as onclick or onmouseover. In JSX, event listener names are written in camelCase, such as onClick or onMouseOver.

    var React = require('react');
    var ReactDOM = require('react-dom');
    
    function makeDoggy (e) {
      // Call this extremely useful function on an <img>.
      // The <img> will become a picture of a doggy.
      e.target.setAttribute('src', 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-puppy.jpeg');
      e.target.setAttribute('alt', 'doggy');
    }
    
    var kitty = (
        <img onClick = {makeDoggy}
            src="https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-kitty.jpg" 
            alt="kitty" />
    );
    
    ReactDOM.render(kitty, document.getElementById('app'));

# If condition in JSX Expression

Here's a rule that you need to know: you can not inject an if statement into a JSX expression.

This code will break:

    (
      <h1>
        { if (purchase.complete) 'Thank you for placing an order!' }
      </h1>
    )

The reason why has to do with the way that JSX is compiled. 
You don't need to understand the mechanics of it for now, but if you're interested then you can learn more here.

What if you want a JSX expression to render, but only under certain circumstances? You can't inject an if statement. What can you do?

# How to define `if` conditionals?

    var React = require('react');
    var ReactDOM = require('react-dom');
    
    if (user.age >= drinkingAge) {
      var message = (
        <h1>
          Hey, check out this alcoholic beverage!
        </h1>
      );
    } else {
      var message = (
        <h1>
          Hey, check out these earrings I got at Claire's!
        </h1>
      );
    }
    
    ReactDOM.render(
      message, 
      document.getElementById('app')
    );

This is the common way to define the if conditionals in react'

# Another way to define the conditionals if else conditions

    var headline = (
      <h1>
        { age >= drinkingAge ? 'Buy Drink' : 'Do Teen Stuff' }
      </h1>
    );

    ----------------------------------------------
    var React = require('react');
    var ReactDOM = require('react-dom');
    
    function coinToss () {
      // Randomly return either 'heads' or 'tails'.
      return Math.random() < 0.5 ? 'heads' : 'tails';
    }
    
    var pics = {
      kitty: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-kitty.jpg',
      doggy: 'https://s3.amazonaws.com/codecademy-content/courses/React/react_photo-puppy.jpeg'
    };
    
    var img = <img src={pics[coinToss() == 'heads' ? 'doggy' : 'kitty']} />;
    
    ReactDOM.render(
        img, 
        document.getElementById('app')
    );

# && use to write conditional operator 

Like the ternary operator, && is not React-specific, but it shows up in React surprisingly often.
In the last two lessons, you wrote statements that would sometimes render a kitty and other times render a doggy. && would not have been the best choice for those lessons.
&& works best in conditionals that will sometimes do an action, but other times do nothing at all.

Here's an example:

    var tasty = (
      <ul>
        <li>Applesauce</li>
        { !baby && <li>Pizza</li> }
        { age > 15 && <li>Brussels Sprouts</li> }
        { age > 20 && <li>Oysters</li> }
        { age > 25 && <li>Grappa</li> }
      </ul>
    );

Every time that you see && in this example, either some code will run, or else no code will run. 

# .map method in react 

If you want to create a list of JSX elements, then .map is often your best bet. It can look odd at first:

    var strings = ['Home', 'Shop', 'About Me'];
    
    var listItems = strings.map(function(string){
      return <li>{string}</li>;
    });
    
    <ul>{listItems}</ul>

another example

    var React = require('react');
    var ReactDOM = require('react-dom');
    
    var people = ['Rowe', 'Prevost', 'Gare'];
    
    var peopleLIs = people.map(function(person){
      // return statement goes here:
        return <li>{person}</li>;
    });
    
    // ReactDOM.render >goes here:
    ReactDOM.render(<ul>{peopleLIs}</ul>, document.getElementById('app'))

# Keys in list in JSX elements

When you make a list in JSX, sometimes your list will need to include something called keys:

    <ul>
      <li key="li-01">Example1</li>
      <li key="li-02">Example2</li>
      <li key="li-03">Example3</li>
    </ul>

A key is a JSX attribute. The attribute's name is key. The attribute's value should be something unique, similar to an id attribute.

keys don't do anything that you can see! React uses them internally to keep track of lists. If you don't use keys when you're supposed to, React might accidentally scramble your list-items into the wrong order.

Not all lists need to have keys. A list needs keys if either of the following are true:

    The list-items have memory from one render to the next. For instance, when a to-do list renders, each item must "remember" whether it was checked off. The items shouldn't get amnesia when they render.

    A list's order might be shuffled. For instance, a list of search results might be shuffled from one render to the next.

If neither of these conditions are true, then you don't have to worry about keys. If you aren't sure then it never hurts to use them!

example of using key elements:

    var React = require('react');
    var ReactDOM = require('react-dom');
    
    var people = ['Rowe', 'Prevost', 'Gare'];
    
    var peopleLIs = people.map(function(person, i){
      // return statement goes here:
        return <li key={'person_' + i}>{person}</li>;
    });
    
    // ReactDOM.render >goes here:
    ReactDOM.render(<ul>{peopleLIs}</ul>, document.getElementById('app'))

# Without using JSX elements

The following JSX expression:

    var h1 = <h1>Hello world</h1>;
    
    can be rewritten without JSX, like this:
    
    var h1 = React.createElement(
      "h1",
      null,
      "Hello, world"
    );

When a JSX element is compiled, the compiler transforms the JSX element into the method that you see above: React.createElement(). Every JSX element is secretly a call to React.createElement().


# Components in ReactJS

The terms "component," "React component," and "component instance" all refer to the same thing.

Take a look at the code below. This code will create and render a new React component:

    var React = require('react');
    var ReactDOM = require('react-dom');
    
    var MyComponentClass = React.createClass({
      render: function () {
        return <h1>Hello world</h1>;
      }
    });
    
    ReactDOM.render(
      <MyComponentClass />,
      document.getElementById('app')
    );


# why we do use `var ReactDOM = require('react-dom');`

    var ReactDOM = require('react-dom');

require('react-dom') is very similar to require('react'). It also returns a JavaScript object, which contains React-related methods.

However, there is a difference!

The methods returned by require('react-dom') are for interacting with the DOM. You'are already familiar with one of them: ReactDOM.render.

The methods returned by require('react') don't deal with the DOM at all. They don't engage directly with anything that isn't part of React. They are for pure React purposes, such as creating components or writing JSX elements.

# Component Class 

A component class is like a factory that creates components. If you have a component class, then you can use that class to produce as many components as you want.

To make a component class, you use one of the methods in the React library: React.createClass.
 
you know that `React.createClass's` job is to create a component class, which is like a factory for building React components. You also know that React.createClass is one of the methods on the object returned by require('react')
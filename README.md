
# PHASE 1

# Ways of using react in application.

1.	By using react cdn links
a.	<script crossorigin src="https://unpkg.com/react@18/umd/react.development.js">
</script>
b.	<script crossorigin src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>

a-> It has react js code by including this cdn our application contains react js code
b->  It is library which is used to modify our dom, it has react dom element.

Hello world program by using React CDN

<script>
        const heading = React.createElement('h1', {}, "Hello world by React");
        const root =  ReactDOM.createRoot(document.getElementById('root'));
        root.render(heading);
    </script>

createElement is react function which is used to create react  element not html element tag, this function return the object which is react element, it takes three params
a.	Tag which which you want to create
b.	Props object here we pass the attributes of the tag
c.	Content which want to show in inside created element


# CreateRoot is React DOM function which is used to create the root where all the react dom element will get rendered.




App.js


const heading = React.createElement('h1', {id: "heading", value: 10}, "Hello world by React"); //in last param we can pass any thing whihc we want to place inside this h1 element

console.log(heading); //return the react object , it is not a html h1 element, createElement function will create the react object not HTML dom element

const root = ReactDOM.createRoot(document.getElementById('root'));

root.render(heading); //render function is responsible for converting the react object into browser understanable dom element like <h1></h1>

 # Creating Nested element inside React

Suppose we want to create nested element like /**
 * <div id='parent'>
 *  <div id = 'child'>
 *      <h1>I am h1 tag </h1>
 *  </div>
 * </div>
 */

const parent = React.createElement(
    'div', 
    {id: 'parent'}, 
    React.createElement(
        'div', 
        {id: 'child'}, 
    React.createElement(
        'h1', 
        {}, 
        'I am h1 tag'
        )
    )
);

const root =  ReactDOM.createRoot(document.getElementById('root'));

root.render(parent);
Like this we can create nested elements.

# Creating Nested element inside React Having Siblings
/**
 * <div id='parent'>
 *  <div id = 'child'>
 *      <h1>I am h1 tag </h1>
 *      <h2>I am h2 tag </h2>
 *  </div>
 * </div>
 */

In this child div have two h1 tag which are siblings for this we can pass array of react.createElement in the last argument of createElemet function.

const parent = React.createElement(
    'div', 
    {id: 'parent'}, 
    React.createElement('div', {id: 'child'}, [ 
React.createElement('h1', {}, 'I am h1 tag'),
    	React.createElement('h2', {}, 'I am h2 tag')
   	]
   )
);

This will create the nested structure with siblings, but it will give an error
**Each child in a list should have a unique "key" prop**
Will look this later






# Creating More Nested element inside React Having Siblings
 * <div id='parent'>
 *  <div id = 'child1'>
 *      <h1>I am h1 tag </h1>
 *      <h1>I am h2 tag </h1>
 *  </div>
 * <div id = 'child2'>
 *      <h1>I am h1 tag </h1>
 *      <h1>I am h2 tag </h1>
 *  </div>
 * </div>

Code will be 
const parent = React.createElement(
    'div', 
    {id: 'parent'}, 
    React.createElement('div', {id: 'child1'}, [ 
        React.createElement('h1', {}, 'I am h1 tag'),
        React.createElement('h2', {}, 'I am h2 tag')
    ]),
    React.createElement('div', {id: 'child2'}, [ 
        React.createElement('h1', {}, 'I am h1 tag'),
        React.createElement('h2', {}, 'I am h2 tag')
    ])
);

const root =  ReactDOM.createRoot(document.getElementById('root'));

root.render(parent);

This is very messy and tedious to understand this nested type sturcuture.

In application will have more nested and complicated structure, to overcome this React introduces JSX.


# NOTE: The above things only explain that by using react CDN we can write react applications.

# Pointers:
1.	React.createElement is an object not html element
2.	createElement takes 3 arguments 
a.	Name of the tag
b.	Attributes of the tag in object
c.	Children or content or another element
Const heading = React.createElement(‘h1’, {id: ‘heading’, attribute1: ‘my value’}, ‘I am heading’)
Heading is an object not element
3.	If need multiple children then syntax will be 
const parent = React.createElement(
    'div', 
    {id: 'parent'}, [
    React.createElement('div', {id: 'child1'}, [ 
        React.createElement('h1', {}, 'I am h1 tag'),
        React.createElement('h2', {}, 'I am h2 tag')
    ]),
    React.createElement('div', {id: 'child2'}, [ 
        React.createElement('h1', {}, 'I am h1 tag'),
        React.createElement('h2', {}, 'I am h2 tag')
    ])]
);

4.	ReactDOM.createRoot is responsible for creating  the root of the react where react object will get rendered.
5.	Const root = ReactDOM.createRoot(document.getElementById(‘root’)) will return root
6.	Root.render(react object) this will convert react createment object to HTML element which browser understands
7.	<div id="root"><h1>hi</h1></div> when render called it will get replaced by react object






# What is React?
React is a JavaScript library for building user interfaces `UI`.</br>
React leverages the **virtual DOM** concept to make building `web applications` easier and more efficient.</br>
And the code more manageable and easier to maintain.</br>
![reactjs-rectange-01](https://github.com/danielurra/react/assets/51704179/0d922685-c057-4090-8292-2bd5be2c9417)</br>
# Visualizing the Virtual DOM
One nice feature provided by the `"React Developer Tools"` extension of your **Google Chrome browser** is that it'll allows you to see the virtual DOM</br>
![google-chrome-react-extension](https://github.com/danielurra/react/assets/51704179/bb9713bc-b024-4169-b52b-339a8c658e87)</br>
![3 google-chrome-enable-access](https://github.com/danielurra/react/assets/51704179/e39d9d79-51fb-49c1-890d-35aa7b81a9cb)</br>
## Unhide simple components (hidden by default)
Be sure you change the following setting to be able to see simple elements like `div,ul,li`</br>
![4 do-not-hide-components](https://github.com/danielurra/react/assets/51704179/ed6beaae-ae54-4198-90d4-69351ba1a4da)</br>
## Open Browser Dev Tools with F12
Once the extension is properly configured you can press `F12` and go to **Components**, see image below:</br>
![5 virtual-DOM-tree](https://github.com/danielurra/react/assets/51704179/89454a93-3bf7-4808-bb06-db5943229d48)</br>
## Grab the code
The following code can (and will) be optimized, by now is good enough for the purpose of showing the virtual DOM components.</br>
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <title>Creating Elements</title>
</head>
<body>

<div id='toBeRendered'></div>

<script src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>

<script>

    const groceries = React.createElement('div', {id: 'groceries'},
        React.createElement('h1', null, 'Fruits'),
        React.createElement('ul', null,
            React.createElement('li', null, 'Banana'),
            React.createElement('li', null, 'Orange'),
            React.createElement('li', null, 'Strawberry'),
            React.createElement('li', null, 'Grapes'),
            React.createElement('li', null, 'Mango')
         ),
        )
       
    const toBeRendered = ReactDOM.createRoot(document.getElementById('toBeRendered'))
    toBeRendered.render(groceries)

</script>

</body>
</html>

```
## Code optimization
Having hardcoded things doesn't count between the coding best practices, let's see how we can optimize our code.</br>
Once simple thing that can be is to make use of an **Array** and convert it to a **map**, see code below:
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <title>Array to Map</title>
</head>
<body>

<div id='toBeRendered'></div>

<script src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>

<script>

    const fruArray = [
        'Banana',
        'Orange',
        'Strawberry',
        'Grapes',
        'Mango'
    ]
    
    const fruMap = React.createElement(
        'ul', 
        null, 
        fruArray.map((f, i) => React.createElement("li", {key: i}, f))
    )
    
    const favFruits = React.createElement('div', null,
        React.createElement('h1', null, 'Favorite Fruits'),
        fruMap
    )
    
    const toBeRendered = ReactDOM.createRoot(document.getElementById('toBeRendered'))
    toBeRendered.render(favFruits)

</script>

</body>
</html>

```
![6 after-optimization](https://github.com/danielurra/react/assets/51704179/c9621244-26b1-44ee-88b4-62c683937fa4)</br>
## Define your own component as a class
React has a built-in class that has common capabilities needed by all components, that class is named `React.Component`.</br>
We can extends that class (inheritance) to create our own components.</br>
Making use of classes we can take advantage and save lines of code by just using different instances of the same class, see below:</br>
```html
<!DOCTYPE html>
<html>
<head>
    <meta charset='utf-8'>
    <title>Class Components</title>
</head>
<body>

<div id='toBeRendered'></div>

<script src="https://unpkg.com/react@18/umd/react.development.js"></script>
<script src="https://unpkg.com/react-dom@18/umd/react-dom.development.js"></script>

<script>

    const fruArray = [
        'Banana',
        'Orange',
        'Strawberry',
        'Grapes',
        'Mango'
    ]

    const vegeArray = [
        'Cucumber',
        'Letuce',
        'Broccoli',
        'Cilantro'
    ]

    class ListClass extends React.Component {
        render() {
            return React.createElement(
                "ul", 
                null,
                this.props.items.map((item, i) => React.createElement("li", {key: i}, item))
            )
        }
    }

    class TopLevel extends React.Component {
        render() {
            return React.createElement('div', null,
                React.createElement('h1', null, 'Favorite Fruits'),
                React.createElement(ListClass, {items: fruArray}, null),
                React.createElement('h1', null, 'Favorite Vegetables'),
                React.createElement(ListClass, {items: vegeArray}, null)
            )
        }
    }

    const toplevel = React.createElement(TopLevel, null, null)

	const toBeRendered = ReactDOM.createRoot(document.getElementById('toBeRendered'))
    toBeRendered.render(toplevel)

</script>

</body>
</html>
```
## Two instances of the class are being used on our example
![react-component-class](https://github.com/danielurra/react/assets/51704179/a0410ff0-bffd-4f1e-8d74-714a14909be2)





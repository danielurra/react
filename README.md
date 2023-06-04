# Visualizing the Virtual DOM
One nice feature provided by the `"React Developer Tools"` extension of your **Google Chrome browser** is that it'll allows you to see the virtual DOM</br>
![google-chrome-react-extension](https://github.com/danielurra/react/assets/51704179/bb9713bc-b024-4169-b52b-339a8c658e87)</br>
![3 google-chrome-enable-access](https://github.com/danielurra/react/assets/51704179/e39d9d79-51fb-49c1-890d-35aa7b81a9cb)</br>
## Unhide simple components (hidden by default)
Be sure you change the following setting to be able to see simple elements like `div,ul,li`</br>
![4 do-not-hide-components](https://github.com/danielurra/react/assets/51704179/ed6beaae-ae54-4198-90d4-69351ba1a4da)</br>
## Open Browser Dev Tools with F12
Once the extension is properly configured you can press F12 and go to **Components**, see image below:</br>
![5 virtual-DOM-tree](https://github.com/danielurra/react/assets/51704179/89454a93-3bf7-4808-bb06-db5943229d48)</br>
## Grab the code
```javascript
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


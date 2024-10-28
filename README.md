---

# NewGen Client Plugin Documentation

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
   - [Installation](#installation)
3. [Creating Your First Plugin](#creating-your-first-plugin)
   - [Plugin Structure](#plugin-structure)
   - [Linking Other JavaScript Files](#linking-other-javascript-files)
4. [Loading Your Plugin](#loading-your-plugin)
5. [Important Notes](#important-notes)
6. [Best Practices](#best-practices)
7. [Examples](#examples)
8. [Conclusion](#conclusion)


## Getting Started

### Installation
1. **Download NewGen Client**: Visit the [NewGen Client download page](https://bytarch.github.io/newgen_browser/publish.htm) to download the latest windows version.
2. **Install**: Follow the installation instructions specific to your operating system to set up NewGen Client on your device.

## Creating Your First Plugin

### Plugin Structure

1. **Create a New JavaScript File**: Begin by creating a new `.js` file for your plugin.

2. **Define Your Plugin**: In this file, you will define the main functionality of your plugin. Here is a basic template to follow:

   ```javascript
   // Plugin Name: MyFirstPlugin
   // Description: A simple plugin to demonstrate functionality
   // Author: Your Name

   // The function wrapping is optional
   (function() {
       // Your plugin code goes here
       console.log('Plugin Loaded!');
   })();
   ```

### Linking Other JavaScript Files

You can extend the functionality of your plugins by linking other JavaScript files. Use the following code snippet to include an external JavaScript file:

```javascript
const script = document.createElement('script');
script.src = 'URL_TO_YOUR_SCRIPT.js'; // Replace with the URL of the JS file
document.head.appendChild(script);
```

## Loading Your Plugin

To load your plugin in NewGen Client:

1. Open NewGen Client.
2. Navigate to the "Plugins" section from the main menu.
3. Click on "Load Plugin" and select your `.js` file.

## Important Notes

- **Function Wrapping**: The wrapping function (IIFE) is optional. For simple scripts, you can write your code directly without enclosing it in a function.
  
- **Script Inclusions**: Some websites block the inclusion of scripts within scripts, such as module scripts. This may limit certain functionalities, so ensure your plugin adheres to the restrictions of the target website.

## Best Practices

- **Keep It Modular**: If your plugin grows complex, consider breaking it into smaller functions for better organization and readability.
- **Error Handling**: Implement error handling to manage unexpected issues effectively.
- **Performance Optimization**: Ensure your code is efficient to avoid negatively impacting the browser’s performance.

## Examples

### Example 1: Changing the Background Color

This example changes the background color of the current webpage.

```javascript
(function() {
    document.body.style.backgroundColor = 'lightblue';
})();
```

### Example 2: Custom Alert Button

This example adds a button that shows an alert when clicked.

```javascript
(function() {
    const alertButton = document.createElement('button');
    alertButton.textContent = 'Show Alert';
    alertButton.onclick = function() {
        alert('Hello from NewGen Client!');
    };
    document.body.appendChild(alertButton);
})();
```

### Example 3: Hiding Elements

This example hides all elements with a specific class name.

```javascript
(function() {
    const elements = document.querySelectorAll('.hide-me');
    elements.forEach(element => {
        element.style.display = 'none';
    });
})();
```

### Example 4: Modifying Text Content

This example changes the text content of a specific element.

```javascript
(function() {
    const heading = document.querySelector('h1');
    if (heading) {
        heading.textContent = 'Welcome to My Custom Page!';
    }
})();
```

### Example 5: Adding a CSS Class

This example adds a CSS class to an element to change its appearance.

```javascript
(function() {
    const element = document.querySelector('.highlight');
    if (element) {
        element.classList.add('new-class');
    }
})();
```

### Example 6: Fetching Data from an API

This example fetches data from an API and displays it on the webpage.

```javascript
(function() {
    fetch('https://api.example.com/data')
        .then(response => response.json())
        .then(data => {
            const output = document.createElement('div');
            output.textContent = JSON.stringify(data);
            document.body.appendChild(output);
        })
        .catch(error => console.error('Error fetching data:', error));
})();
```

### Example 7: Keyboard Shortcut to Change Background Color

This example adds a keyboard shortcut (Ctrl + B) to change the background color.

```javascript
(function() {
    document.addEventListener('keydown', function(event) {
        if (event.ctrlKey && event.key === 'b') {
            document.body.style.backgroundColor = 'yellow';
        }
    });
})();
```

### Example 8: Creating a Simple Modal

This example creates a simple modal that can be opened and closed.

```javascript
(function() {
    // Create modal
    const modal = document.createElement('div');
    modal.style.position = 'fixed';
    modal.style.top = '50%';
    modal.style.left = '50%';
    modal.style.transform = 'translate(-50%, -50%)';
    modal.style.backgroundColor = 'white';
    modal.style.padding = '20px';
    modal.style.boxShadow = '0 0 10px rgba(0,0,0,0.5)';
    modal.style.zIndex = '1000';
    modal.style.display = 'none';
    
    const modalContent = document.createElement('p');
    modalContent.textContent = 'This is a simple modal!';
    modal.appendChild(modalContent);
    
    const closeButton = document.createElement('button');
    closeButton.textContent = 'Close';
    closeButton.onclick = function() {
        modal.style.display = 'none';
    };
    modal.appendChild(closeButton);
    
    document.body.appendChild(modal);

    // Open modal button
    const openModalButton = document.createElement('button');
    openModalButton.textContent = 'Open Modal';
    openModalButton.onclick = function() {
        modal.style.display = 'block';
    };
    document.body.appendChild(openModalButton);
})();
```

### Example 9: Adding a Tooltip

This example adds a tooltip that appears when hovering over an element.

```javascript
(function() {
    const tooltip = document.createElement('div');
    tooltip.style.position = 'absolute';
    tooltip.style.backgroundColor = 'black';
    tooltip.style.color = 'white';
    tooltip.style.padding = '5px';
    tooltip.style.borderRadius = '5px';
    tooltip.style.display = 'none';
    document.body.appendChild(tooltip);

    const targetElement = document.querySelector('.hover-target');
    if (targetElement) {
        targetElement.addEventListener('mouseenter', function(event) {
            tooltip.textContent = 'This is a tooltip!';
            tooltip.style.left = event.pageX + 'px';
            tooltip.style.top = event.pageY + 'px';
            tooltip.style.display = 'block';
        });
        targetElement.addEventListener('mouseleave', function() {
            tooltip.style.display = 'none';
        });
    }
})();
```

### Example 10: Dynamic Style Injection

This example dynamically injects a CSS style into the webpage.

```javascript
(function() {
    const style = document.createElement('style');
    style.textContent = `
        body {
            font-family: Arial, sans-serif;
        }
        .custom-class {
            color: green;
            font-weight: bold;
        }
    `;
    document.head.appendChild(style);
})();
```


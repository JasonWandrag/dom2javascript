# HTML to Markdown Converter

This is a utility module that allows you to convert HTML elements into a JavaScript Object representation with Markdown-like structure.

## Installation

No installation is required for this module. Simply include the code in your project and start using it.

## Usage

To use the `createMarkdownForElement` function to create a JavaScript Object representation of an HTML element, follow these steps:

1. Select the HTML element you want to copy:
```javascript
const page = document.querySelector("html");
```
2. Call the `createMarkdownForElement` function, passing the HTML element's tag name and the element itself as parameters:
```javascript
const markdown = createMarkdownForElement(page.tagName.toLowerCase(), page);
```
3. Optional: If you want to download the resulting JavaScript Object as a JSON file, use the following code:
```javascript
const dataStr = "data:text/json;charset=utf-8," + encodeURIComponent(JSON.stringify(markdown));
const downloadAnchorNode = document.createElement("a");
downloadAnchorNode.setAttribute("href", dataStr);
downloadAnchorNode.setAttribute("download", "markdown.json");
document.body.appendChild(downloadAnchorNode); // Required for Firefox
downloadAnchorNode.click();
downloadAnchorNode.remove();
```

This code creates a download link for the generated JavaScript Object in JSON format. When clicked, it triggers the download of the JSON file named "markdown.json".

Make sure to adjust the code according to your specific requirements, such as selecting the desired HTML element and providing the appropriate file name for the download.

##Note
The resulting JavaScript Object representation of the HTML element will have a structure that resembles Markdown. It includes the element's tag name, attributes, and child elements, recursively for nested elements.

This module relies on the functions `componentIdGenerator`, `createElement`, `createText`, and `hasTextChild` to generate unique component IDs, create element objects, handle text content, and check if an element has text children, respectively. Ensure that these functions are available and accessible within your project.

Please be aware of the cross-browser compatibility when using the download functionality, as the code provided may require adjustments for specific browsers.
# HTML DOM Race Condition Bug

This repository demonstrates an uncommon bug in HTML related to a race condition between the HTML parsing and JavaScript execution. The script attempts to manipulate the DOM element before it has been fully loaded by the browser, resulting in a silent failure.

## Bug Description:
The primary issue lies in the script that tries to access and modify the `myDiv` element *before* the browser has completely finished rendering the HTML.  This can happen because JavaScript executes asynchronously and may attempt to access elements that haven't yet been fully added to the DOM tree.

## Solution:
The solution involves using the `DOMContentLoaded` event listener to ensure the script executes only after the DOM has been fully parsed and is ready for manipulation.

## How to run:
1. Clone this repository
2. Open `bug.html` in a web browser. You'll notice that the text inside `myDiv` is visible despite the JavaScript code attempting to hide it.
3. Open `solution.html` to see the corrected code where the `DOMContentLoaded` event ensures the element is manipulated only after the browser is ready.

## Additional Notes
This type of error is subtle and can be difficult to debug because it doesn't necessarily throw an error, it just behaves unexpectedly. Always ensure your JavaScript DOM manipulations occur within the appropriate lifecycle events of the page.
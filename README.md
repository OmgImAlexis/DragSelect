```
    ____                   _____      __          __ 
   / __ \_________ _____ _/ ___/___  / /__  _____/ /_
  / / / / ___/ __ `/ __ `/\__ \/ _ \/ / _ \/ ___/ __/
 / /_/ / /  / /_/ / /_/ /___/ /  __/ /  __/ /__/ /_  
/_____/_/   \__,_/\__, //____/\___/_/\___/\___/\__/  
                 /____/                              
```

# DragSelect
easily add a selection algorythm to your application/website.

# Project Page: Demo & Info

https://thibaultjanbeyer.github.io/DragSelect/

# Key-Features

- No dependencies
- Accessibility (a11y)
- Add drag selection
- Choose which elements can be selected.
- Great browser support, works even like a charm on IE9
- Lightweight, only ~1KB gzipped
- DragSelect was written with Performance in mind.
- Free & open source under MIT License
- Ease of use

# Why?

Because apparently there is nothing that does not require jquery out there yet.  
This is better than https://jqueryui.com/selectable/ and has no dependencies.
We use it currently in a professional rich interface application where we have a file management system. The user can select files to organize them and change their metadata, with this plugin our users are able to select multiple files and perform batch/bulk-operations (applying changes to multiple files at once). I can easily think of dozens other possibilites this can be used for. I’m really keen to know how you use it in your projects, please let me know.

# Installation
## easy

Just download the file (minified) and add it to your document:

```html
<script src="https://thibaultjanbeyer.github.io/DragSelect/ds.min.js"></script>
```

## npm
```console
npm install --save-dev dragselect
```

## bower
```console
bower install --save-dev dragselect
```

That's it, you're ready to rock!  
Of course you can also just include the code within your code to save a request.

# Usage

Now in your JavaScript you can simply pass elements to the function like so:

## simple

Choose which elements can be selected:

```javascript
new DragSelect({
  selectables: document.getElementsByClassName('selectable-nodes')
});
```

## complete

All options are optional. You could also just initiate the Dragselect by `new DragSelect();` without any option.

```javascript
var ds = new DragSelect({
  selectables: document.getElementsByClassName('selectable-nodes'), // node/nodes that can be selected. This is also optional, you could just add them later with .addSelectables.
  selector: document.getElementById('rectangle'), // draggable element. By default one will be created.
  area: document.getElementById('area'), // area in which you can drag. If not provided it will be the whole document.
  customStyles: false,  // If set to true, no styles (except for position absolute) will be applied by default.
  multiSelectKeys: ['ctrlKey', 'shiftKey', 'metaKey'],  // special keys that allow multiselection.
  onElementSelect: function(element) {}, // fired every time an element is selected. (element) = just selected node
  onElementUnselect: function(element) {}, // fired every time an element is de-selected. (element) = just de-selected node.
  callback: function(elements) {} // fired once the user releases the mouse. (elements) = selected nodes.
});

// if you add the function to a variable like we did, you have access to all its functions
// and can now use start() and stop() like so:
ds.getSelection();  // returns all currently selected nodes
ds.addSelectables(document.getElementsByClassName('selectable-node'));  // adds elements that can be selected. Intelligent algorythm never adds elements twice.
ds.stop();  // will teardown/stop the whole functionality
ds.start();  // reset the functionality after a teardown
```  

You can also use the "shift", "ctrl" or "command" key to make multiple independent selections.


## Accessibility (a11y)

DragSelect is accessibly by default:  

TLDR; => Your `selectables` should be buttons: `<button type="button"></button>`.  

Obviously, keyboard users won’t get the full visual experience but it works similarely to the OS default behaviour. You can select items using the default select keys (usually space or enter) and also multiselect when using a modifier key at the same time. There is one little thing you have to do tho’: the `selectables` have to be pressable (clickable)! To achieve this, they should be of type `<button type="button"></button>`.  



# Properties:
| property | type | usage |
|--- |--- |--- |
|selectables |DOM elements (nodes) |OPTIONAL. The elements that can be selected |
|selector |single DOM element (node) |OPTIONAL. The square that will draw the selection. Autocreated by default |
|area |single DOM element (node) |OPTIONAL. The square in which you are able to select |
|customStyles |boolean |OPTIONAL. If true, no styles will be automatically applied (except position: absolute). Default: `false` |
|multiSelectKeys |array |OPTIONAL. These key will allow the user add more elements to the selection instead of clearing the selection. The only possible values are keys that are provided via the event object. So far: <kbd>ctrlKey</kbd>, <kbd>shiftKey</kbd>, <kbd>metaKey</kbd> and <kbd>altKey</kbd>. Provide an empty array `[]` if you want to turn off the funcionality. Default: `['ctrlKey', 'shiftKey', 'metaKey']` |
|onElementSelect |function |OPTIONAL. Fired every time an element is selected. This callback gets a property which is the selected node |
|onElementUnselect |function |OPTIONAL. Fired every time an element is de-selected. This callback gets a property which is the de-selected node |
|callback |function |OPTIONAL. Callback function that gets fired when the selection is released. This callback gets a property which is an array that holds all selected nodes |

# Methods:
When the function is saved into a variable `var foo = new DragSelect()` you have access to all its inner functions. There are way more than listed here. Here are just the most usable:  

| method | properties | usage |
|--- |--- |--- |
|stop |/ |Will teardown/stop the whole functionality |
|start |/ |Reset the functionality after a teardown |
|getSelection |/ |Returns all currently selected nodes |
|addSelectables |DOM elements (nodes), Boolean (addToSelection) |Adds elements that can be selected. Don’t worry, a smart algorythm makes sure that nodes are never added twice. If boolean is set to true: elements will also be added to current selection. |
|removeSelectables |DOM elements (nodes), Boolean (removeFromSelection) |Remove elements that can be selected. If boolean is set to true: elements will also be removed from current selection. |
|getSelectables |/ |Returns array with all nodes that can be selected. |

# Classes
| name | trigger |
|--- |--- |
|.ds-selected |On elements that are selected
|.ds-hover |On elements that are currently hovered
|.ds-selector |On the selector element
|.ds-selectable |On elements that can be selected

# Have Fun!

[![Typewriter Gif](https://thibaultjanbeyer.github.io/DragSelect/typewriter.gif)](http://thibaultjanbeyer.com/)

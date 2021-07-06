# DOM

The **Document Object Model** (**DOM**) connects web pages to scripts or programming languages by representing the structure of a document in memory.

The DOM represents a document with a logical tree. Each branch of the tree ends in a node, and each node contains objects. DOM methods allow programmatic access to the tree. With them, you can change the document's structure, style, or content.

**Document:** The Document interface represents any web page loaded in the browser and serves as an entry point into the web page's content, which is the DOM tree.

 https://developer.mozilla.org/en-US/docs/Web/API/Document

## Adding and Deleting Elements

<table>
 <tr>
     <th>
         Method
     </th>
     <th>
         Description
     </th>
 </tr>
    <tr>
        <td>
            document.createElement(element)
        </td>
        <td>
            Create an HTML element
        </td>
    </tr>
    <tr>
         <td>
            document.removeChild(element)
        </td>
        <td>
            Remove an HTML element
        </td>        
    </tr>
     <tr>
         <td>
            document.appendChild(element)
        </td>
        <td>
            Add an HTML element
        </td>        
    </tr>
    <tr>
         <td>
            document.replaceChild(new, old)
        </td>
        <td>
            Replace an HTML element
        </td>        
    </tr>
    <tr>
         <td>
            document.write(text)
        </td>
        <td>
            Write into the HTML output stream
        </td>        
    </tr>
</table>

## Finding HTML Elements

<table>
 <tr>
     <th>
         Method
     </th>
     <th>
         Description
     </th>
 </tr>
    <tr>
        <td>
            document.getElementById(id)
        </td>
        <td>
            Find an element by element id
        </td>
    </tr>
    <tr>
         <td>
            document.getElementsByTagName(name)
        </td>
        <td>
            Find elements by tag name
        </td>        
    </tr>
     <tr>
         <td>
            document.getElementsByClassName(name)
        </td>
        <td>
            Find elements by class name
        </td>        
    </tr>
    <tr>
         <td>
            document.querySelector(selector)
        </td>
        <td>
            Returns the first Element node within the document, in document order, that matches the specified selectors
        </td>        
    </tr>
    <tr>
         <td>
            document.querySelectorAll(selector)
        </td>
        <td>
            Returns a list of all the Element nodes within the document that match the specified selectors.
        </td>        
    </tr>
</table>

**Element:** is the most general base class from which all element objects (i.e. objects that represent elements) in a Document inherit. It only has methods and properties common to all kinds of elements.

https://developer.mozilla.org/en-US/docs/Web/API/Element

## Changing HTML Elements

<table>
 <tr>
     <th>
         Property
     </th>
     <th>
         Description
     </th>
 </tr>
    <tr>
        <td>
            element.innerHTML = new html content
        </td>
        <td>
           Change the inner HTML of an element
        </td>
    </tr>
    <tr>
         <td>
            element.attribute = new value
        </td>
        <td>
            Change the attribute value of an HTML element
        </td>        
    </tr>
     <tr>
         <td>
            element.style.property = new style
        </td>
        <td>
            Change the style of an HTML element
        </td>        
    </tr>
    <tr>
         <td>
            element.id
        </td>
        <td>
            Is a DOMString representing the id of the element.
        </td>        
    </tr>
    <tr>
         <td>
            element.className
        </td>
        <td>
           Is a DOMString representing the class of the element.
        </td>        
    </tr>
    <tr>
         <th>
             Method
         </th>
         <th>
             Description
         </th>
   </tr>
    <tr>
         <td>
           element.setAttribute(attribute, value)
        </td>
        <td>
           Change the attribute value of an HTML element
        </td>        
    </tr>
    <tr>
         <td>
           element.before()
        </td>
        <td>
           Inserts a set of Node or DOMString objects in the children list of the Element's parent, just before the Element.
        </td>        
    </tr>
    <tr>
         <td>
          element.after()
        </td>
        <td>
           Inserts a set of Node or DOMString objects in the children list of the Element's parent, just after the Element.
        </td>        
    </tr>
    <tr>
         <td>
          element.prepend()
        </td>
        <td>
           Inserts a set of Node objects or DOMString objects before the first child of the element.
        </td>        
    </tr>
    <tr>
         <td>
          element.append()
        </td>
        <td>
           Inserts a set of Node objects or DOMString objects after the last child of the element.
        </td>        
    </tr>
</table>

## Bibliography:

[https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model)

https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model/Introduction

https://developer.mozilla.org/en-US/docs/Web/API/HTML_DOM_API 

https://www.w3schools.com/js/js_htmldom_document.asp


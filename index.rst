===============
 jQuery Level 1
===============

- Course: jQuery Level 1 (EDTECH 533)
- Author: Christer Edwards
- Revision: 2013-02-17

Welcome
=======

- Schedule
- Facilities
- Introductions

Requirements
============

- HTML
- CSS
- JavaScript

Overview
========

- History
- Resources & Help
- Development Environment
- Installation
- Basic CSS Selectors
- Pseudo-Selectors (jQuery Extensions)
- Traversing the DOM
- DOM Manipulation
- Events
- Hands-On Projects

What is jQuery
==============

jQuery is a multi-browser JavaScript library designed to simplify the client-side scripting of HTML.

History
=======

- `Idea formed`_ in 2005
- `Formally announced`_ in early 2006
- Author: `John Resig`_

.. _`Idea formed`: http://ejohn.org/blog/selectors-in-javascript/
.. _`Formally announced`: http://ejohn.org/blog/barcampnyc-wrap-up/
.. _`John Resig`: http://ejohn.org/about/

Local Resources
===============

.. ifslides::

- `utahjs.com`_
- `#utahjs`_ IRC (freenode)
- Monthly Presentations

.. _`utahjs.com`: http://utahjs.com
.. _`#utahjs`: http://webchat.freenode.net/?channels=utahjs

.. ifnotslides::

    The UtahJS User Group holds meetings in both Salt Lake and Utah County.
      - First Thursday in SLC
      - Third Tuesday in Utah County 

Online Help
===========

- `jQuery Forum`_
- `jQuery Blog`_
- `jQuery Docs`_
- `jQuery Tutorials`_

.. _`jQuery Forum`: http://forum.jquery.com
.. _`jQuery Blog`: http://blog.jquery.com
.. _`jQuery Docs`: http://docs.jquery.com
.. _`jQuery Tutorials`: http://docs.jquery.com/Tutorials

Troubleshooting
===============

The ``console.log`` method allows you to send log output to the JavaScript
console within the browser. This can be very helpful in troubleshooting your
jQuery code.

Development Environment
=======================

- Text Editor
- Web Browser

Installation
============

- Local Source
- CDN (Content Delivery Network)

Local (Production vs Development)
=================================

`Download jQuery`_

Which one should I use? Production or Development?

.. _`Download jQuery`: http://jquery.com/download/

Installation - Local
====================

.. code-block:: html

    <script src="jquery.js"></script>

Installation - CDN (Google)
===========================

Use `Google Hosted Libraries`_ CDN service.

.. _`Google Hosted Libraries`: https://developers.google.com/speed/libraries/devguide#jquery

.. code-block:: html

    <script src="//ajax.googleapis.com/ajax/libs/jquery/1.9.0/jquery.min.js"></script>

Installation - CDN (Microsoft)
==============================

Use `Microsoft Ajax CDN`_

.. _`Microsoft Ajax CDN`: http://www.asp.net/ajaxlibrary/cdn.ashx#jQuery_Releases_on_the_CDN_0

.. code-block:: html

     <script src="http://ajax.aspnetcdn.com/ajax/jquery/jquery-1.9.0.js"></script> 

Installation - CDN (jQuery)
===========================

Use `jQuery CDN`_

.. _`jQuery CDN`: http://jquery.com/download/

.. code-block:: html

    <script src="http://code.jquery.com/jquery-1.9.0.min.js"></script>

Getting Started
===============

.. code-block:: html

    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8">
        <title>Example</title>
    </head>
    <body>
        <p>Hello World!</p>
        <script src="http://code.jquery.com/jquery-1.9.0.min.js"></script>
    </body>
    </html>

Head vs Body
============

Should you place your jQuery code in the ``head`` or ``body`` of your HTML document? Why?

$(document).ready
=================

If you need to load jQuery in the ``head`` of your document, you'll need to use
the ``$(document).ready`` method. This tells jQuery to wait until the full
document (the page) is loaded before executing the code.

$(document).ready (Example)
===========================

.. code-block:: html

    <!DOCTYPE html>
    <html>
    <head>
        <meta charset="utf-8">
        <title>Example</title>
        <script src="http://code.jquery.com/jquery-1.9.0.min.js"></script>

        <script>
            $(document).ready(function() {
                alert("Hello World!");
            });
        </script>

    </head>
    <body>
        <p>Hello World</p>
    </body>
    </html>

Best practice?
==============

It is generally best practice to load jQuery in the body of your document, in
which case it is not required to use ``$(document).ready``.

jQuery() vs $()
===============

``$()`` is a shortcut for ``jQuery()``. It is very common to see ``$()`` used in jQuery scripts.

Lab 1
=====

- Create a template HTML document
- Include the latest jQuery via CDN

===================
Basic CSS selectors
===================

All Selector ("*")
==================

Selects all elements.

Find every element (including head, body, etc) in the document.

.. code-block:: html

    <script>
        var elementCount = $("*").length;
        console.log(elementCount);
    </script>

Class Selector (".class")
=========================

Selects all elements with the given class. An element can have multiple
classes; only one of them must match. For class selectors, jQuery uses
JavaScript's native ``getElementsByClassName()`` function if the browser
supports it.

.. code-block:: html

    <div class="emphasis">This content should be emphasised</div>
    <script>
        $(".emphasis").css("font-style", "italic");
    </script>

Element Selector ("element")
============================

Selects all elements with the given tag name.

JavaScript's ``getElementsByTagName()`` function is called to return the
appropriate elements when this expression is used.

.. code-block:: html

    <div>This content should be bold</div>
    <script>
        $("div").css("font-weight", "bold");
    </script>
    
ID Selector ("#id")
===================

Selects a single element with the given id attribute.

Each id value must be used only once within a document. If more than one
element has been assigned the same ID, queries that use that ID will only
select the first matched element in the DOM. This behavior should not be relied
on, however; a document with more than one element using the same ID is
invalid.

.. code-block:: html

    <div id="underline">This content should be underlined</div>
    <script>
        $("#underline").css("text-decoration", "underline");
    </script>

Attribute Selector
==================

Selects elements that have the specified attribute with a value exactly equal
to a certain value.

.. code-block:: html

    <form>
    First Name: <input type="text" name="firstname"></br>
    Last Name: <input type="text" name="lastname">
    </form>
    <script>
    $('input[name="firstname"]').css("background-color", "green");
    </script>

Multiple Selector ("selector1, selector2")
=====================================================

Selects the combined results of all the specified selectors.

.. code-block:: html

    <div class="emphasis">This will be green</div>
    <div>This will be normal</div>
    <div id="underline">This will be green</div>
    <script>
        $("div.emphasis,div#underline").css("color", "green");
    </script>

Lab 2
=====

- Create document(s) using 3 of the 6 Basic CSS Selectors.

 - All Selector
 - Class Selector
 - Element Selector
 - ID Selector
 - Attribute Selector
 - Multiple Selectors

====================================
Pseudo Selectors (jQuery Extensions)
====================================

Performance Note
================

Because these are jQuery extensions and not part of the CSS specification,
queries using pseudo-selectors cannot take advantage of the performance boost
provided by the native DOM ``querySelectorAll()`` method. To achieve the best
performance when using pseudo-selectors to select elements, first select the
elements using a pure CSS selector, then use ``.filter("selector")``.

.css() vs .addClass()
=====================

HTML, CSS and JavaScript each have specific roles to play in the browser. Using
the ``.css()`` method applies style using JavaScript, where it should be
managed directly in the CSS. Using ``.addClass()`` allows us to update styling,
while keeping style declarations out of our JavaScript.

:animated
=========

Select all elements that are in the progress of an animation at the time the
selector is run.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("div").on("click", function() {
        $("div").filter(":animated").addClass("highlight");
    });
    </script>

:button
=======

Selects all button elements and elements of type button.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("body").filter(":button").addClass("green");
    </script>

:checkbox
=========

Selects all elements of type checkbox.

**jQuery >=1.6**

.. code-block:: html

    <script>
    $("form input").filter(":checkbox").prop("checked", true);
    $("form input").filter(":checkbox").prop("checked", false);
    </script>

**jQuery <=1.5**

.. code-block:: html

    <script>
    $("form input").filter(":checkbox")
        .attr("checked", "checked");
    </script>

:eq(n)
======

Select the element at index n within the matched set.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("li").filter(":eq(2)").addClass("highlight");
    </script>

:even
=====

Selects even elements, zero-indexed. See also odd.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("li").filter(":even").addClass("highlight");
    </script>

:file
=====

Selects all elements of type file.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("input").filter(":file").addClass("highlight");
    </script>

:first
======

Selects the first matched element.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("li").filter(":first").addClass("highlight");
    </script>

:gt(n)
======

Select all elements at an index greater than index within the matched set.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("li").filter(":gt(4)").addClass("highlight");
    </script>

:has(n)
=======

Selects elements which contain at least one element that matches the specified
selector.

.. code-block:: html

    <style>
    .border { background-color: yellow; }
    </style>
    <script>
    $("div").filter(":has(p)").addClass("highlight");
    </script>

:header
=======

Selects all elements that are headers, like h1, h2, h3 and so on.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("div").filter(":header").addClass("highlight");
    </script>

:hidden
=======

Selects all elements that are hidden.

.. code-block:: html

    <script>
    $("div").filter(":hidden").show();
    </script>

:image
======

Selects all elements of type image.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("input").filter(":image").addClass("highlight");
    </script>

:input
======

Selects all input, textarea, select and button elements.

.. code-block:: html

    <script>
    var totalInput = $("form").filter(":input");
    console.log( totalInput );
    </script>

:last
=====

Selects the last matched element.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("li").filter(":last").addClass("highlight");
    </script>

:lt(n)
======

Select all elements at an index less than index within the matched set.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("li").filter(":lt(4)").addClass("highlight");
    </script>

:odd
====

Selects odd elements, zero-indexed. See also even.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("li").filter(":odd").addClass("highlight");
    </script>

:parent
=======

Select all elements that have at least one child node (either an element or 
text).

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("li").filter(":parent").addClass("highlight");
    </script>

:password
=========

Selects all elements of type password.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("form input").filter(":password").addClass("highlight");
    </script>

:radio
======

Selects all elements of type radio.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("form input").filter(":radio").addClass("highlight");
    </script>

:reset
======

Selects all elements of type reset.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("form input").filter(":reset").addClass("highlight");
    </script>

:selected
=========

Selects all elements that are selected.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("select option").filter(":selected").addClass("highlight");
    </script>

:submit
=======

Selects all elements of type submit.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("form").filter(":submit").addClass("highlight");
    </script>

:text
=====

Selects all elements of type text.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $("form input").filter(":text").addClass("highlight");
    </script>

:visible
========

Selects all elements that are visible.

.. code-block:: html

    <style>
    .hidden { display: none; }
    </style>
    <script>
    $("div").filter(":visible").addClass("hidden");
    </script>

Lab 3
=====

- Expand your HTML template to include a form and list.
- Use jQuery to highlight selected elements within your document.
- Implement ten of the pseudo-selectors outlined in this section.

 - :animated, :button, :checkbox, :eq(), :even, :file, :first, :gt(), :has(), :header, :hidden, :image, :input, :last, :lt(), :odd, :parent, :password, :radio, :reset, :selected, :submit, :text, :visible 

==================
Traversing the DOM
==================

.children()
===========

Get the children of each element in the set of matched elements, optionally
filtered by a selector.

.children() - Example
=====================

.. code-block:: html
   :emphasize-lines: 5-6

    <ul class="level 1">
        <li>parent</li>
        <li>parent</li>
            <ul class="level 2">
                <li>child</li>
                <li>child</li>
            </ul>
            <ul class="level 3">
                <li>sibling</li>
                <li>sibling</li>
            </ul>
    </ul>
    <script>
        $("ul.level-2").children().css('background-color', 'green');
    </script>

.closest()
==========

For each element in the set, get the first element that matches the selector by
testing the element itself and traversing up through its ancestors in the DOM
tree.

.closest() - Example
====================

.. code-block:: html
   :emphasize-lines: 6

    <ul class="level-1">
        <li id="parent-1">parent</li>
        <li id="parent-2">parent</li>
            <ul class="level-2">
                <li id="child-1">child</li>
                <li id="child-2">child</li>
                    <ul class="level-3">
                        <li id="grandchild-1">grandchild</li>
                        <li id="grandchild-2">grandchild</li>
                    </ul>
            </ul>
    </ul>

    <script>
        $('li#child-2').closest('li').css('background-color', 'green');
    </script>

.find()
=======

Get the descendants of each element in the current set of matched elements,
filtered by a selector, jQuery object, or element.

.find() - Example
=================

.. code-block:: html
   :emphasize-lines: 5-6, 8-9

    <ul class="level-1">
        <li id="parent-1">parent</li>
        <li id="parent-2">parent</li>
            <ul class="level-2">
                <li id="child-1">child</li>
                <li id="child-2">child</li>
                    <ul class="level-3">
                        <li id="grandchild-1">grandchild</li>
                        <li id="grandchild-2">grandchild</li>
                    </ul>
            </ul>
    </ul>

    <script>
        $('ul.level-2').find('li').css('background-color', 'green');
    </script>

.next()
=======

Get the immediately following sibling of each element in the set of matched
elements. If a selector is provided, it retrieves the next sibling only if it
matches that selector.

.next() - Example
=================

.. code-block:: html
   :emphasize-lines: 6

    <ul class="level-1">
        <li id="parent-1">parent</li>
        <li id="parent-2">parent</li>
            <ul class="level-2">
                <li id="child-1">child</li>
                <li id="child-2">child</li>
                    <ul class="level-3">
                        <li id="grandchild-1">grandchild</li>
                        <li id="grandchild-2">grandchild</li>
                    </ul>
            </ul>
    </ul>

    <script>
        $('li#child-1').next('li').css('background-color', 'green');
    </script>

.nextAll()
==========

Get all following siblings of each element in the set of matched elements,
optionally filtered by a selector.

.nextAll() - Example
====================

.. code-block:: html
   :emphasize-lines: 3-12

    <ul class="level-1">
        <li id="parent-1">parent</li>
        <li id="parent-2">parent</li>
            <ul class="level-2">
                <li id="child-1">child</li>
                <li id="child-2">child</li>
                    <ul class="level-3">
                        <li id="grandchild-1">grandchild</li>
                        <li id="grandchild-2">grandchild</li>
                    </ul>
            </ul>
    </ul>

    <script>
        $('li#parent-1').nextAll().css('background-color', 'green');
    </script>

.nextUntil()
============

Get all following siblings of each element up to but not including the element
matched by the selector, DOM node, or jQuery object passed.

.nextUntil() - Example
======================

.. code-block:: html
   :emphasize-lines: 5-12

    <ul class="level-1">
        <li id="level-1a">level 1</li>
        <li id="level-1b">level 1</li>
    </ul>
    <ul class="level-2">
        <li id="level-2a">level 2</li>
        <li id="level-2b">level 2</li>
    </ul>
    <ul class="level-3">
       <li id="level-3a">level 3</li>
       <li id="level-3b">level 3</li>
    </ul>

    <script>
        $('ul.level-1').nextUntil('li').css('background-color', 'green');
    </script>

.offsetParent()
===============

Get the closest ancestor element that is positioned.

.offsetParent() - Example
=========================

.. code-block:: html
   :emphasize-lines: 4-11

    <ul class="level-1">
        <li id="parent-1">parent</li>
        <li id="parent-2">parent</li>
            <ul class="level-2" style="position: relative;">
                <li id="child-1">child</li>
                <li id="child-2">child</li>
                    <ul class="level-3">
                        <li id="grandchild-1">grandchild</li>
                        <li id="grandchild-2">grandchild</li>
                    </ul>
            </ul>
    </ul>

    <script>
        $('ul.level-3').offsetParent().css('background-color', 'green');
    </script>

.parent()
=========

Get the parent of each element in the current set of matched elements,
optionally filtered by a selector.

.parent() - Example
===================

.. code-block:: html
   :emphasize-lines: 4-6, 11

    <ul class="level-1">
        <li id="parent-1">parent</li>
        <li id="parent-2">parent</li>
            <ul class="level-2">
                <li id="child-1">child</li>
                <li id="child-2">child</li>
                    <ul class="level-3">
                        <li id="grandchild-1">grandchild</li>
                        <li id="grandchild-2">grandchild</li>
                    </ul>
            </ul>
    </ul>

    <script>
        $('li#child-1').parent().css('background-color', 'green');
    </script>

.parents()
==========

Get the ancestors of each element in the current set of matched elements,
optionally filtered by a selector.

The .parents() and .parent() methods are similar, except that the latter only 
travels a single level up the DOM tree.

.parents() - Example
====================

.. code-block:: html
   :emphasize-lines: 1-12

    <ul class="level-1">
        <li id="parent-1">parent</li>
        <li id="parent-2">parent</li>
            <ul class="level-2">
                <li id="child-1">child</li>
                <li id="child-2">child</li>
                    <ul class="level-3">
                        <li id="grandchild-1">grandchild</li>
                        <li id="grandchild-2">grandchild</li>
                    </ul>
            </ul>
    </ul>

    <script>
        $('li#grandchild-1').parents().css('background-color', 'green');
    </script>

.parentsUntil()
===============

Get the ancestors of each element in the current set of matched elements, up to
but not including the element matched by the selector, DOM node, or jQuery
object.

.parentsUntil() - Example
=========================

.. code-block:: html
   :emphasize-lines: 7-10

    <ul class="level-1">
        <li id="parent-1">parent</li>
        <li id="parent-2">parent</li>
            <ul class="level-2">
                <li id="child-1">child</li>
                <li id="child-2">child</li>
                    <ul class="level-3">
                        <li id="grandchild-1">grandchild</li>
                        <li id="grandchild-2">grandchild</li>
                    </ul>
            </ul>
    </ul>

    <script>
        $('li#grandchild-1').parentsUntil('ul.level-2').css('background-color', 'green');
    </script>

.prev()
=======

Get the immediately preceding sibling of each element in the set of matched
elements, optionally filtered by a selector.

.prev() - Example
=================

.. code-block:: html
   :emphasize-lines: 4-6, 11

    <ul class="level-1">
        <li id="parent-1">parent</li>
        <li id="parent-2">parent</li>
            <ul class="level-2">
                <li id="child-1">child</li>
                <li id="child-2">child</li>
                    <ul class="level-3">
                        <li id="grandchild-1">grandchild</li>
                        <li id="grandchild-2">grandchild</li>
                    </ul>
            </ul>
    </ul>

    <script>
        $('ul.level-3').prev('ul.level-2').css('background-color', 'green');
    </script>

.prevAll()
==========

Get all preceding siblings of each element in the set of matched elements,
optionally filtered by a selector.

.prevAll() - Example
====================

.. code-block:: html
   :emphasize-lines: 8

    <ul class="level-1">
        <li id="parent-1">parent</li>
        <li id="parent-2">parent</li>
            <ul class="level-2">
                <li id="child-1">child</li>
                <li id="child-2">child</li>
                    <ul class="level-3">
                        <li id="grandchild-1">grandchild</li>
                        <li id="grandchild-2">grandchild</li>
                    </ul>
            </ul>
    </ul>

    <script>
        $('li#grandchild-2').prevAll().css('background-color', 'green');
    </script>

.prevUntil()
============

Get all preceding siblings of each element up to but not including the element
matched by the selector, DOM node, or jQuery object.

.prevUntil() - Example
======================

.. code-block:: html
   :emphasize-lines: 5-8

    <ul class="level-1">
        <li id="level-1a">level 1</li>
        <li id="level-1b">level 1</li>
    </ul>
    <ul class="level-2">
        <li id="level-2a">level 2</li>
        <li id="level-2b">level 2</li>
    </ul>
    <ul class="level-3">
       <li id="level-3a">level 3</li>
       <li id="level-3b">level 3</li>
    </ul>

    <script>
        $('ul.level-3').prevUntil('ul.level-1').css('background-color', 'green');
    </script>

.siblings()
===========

Get the siblings of each element in the set of matched elements, optionally
filtered by a selector.

.siblings() - Example
=====================

.. code-block:: html
   :emphasize-lines: 8-11

    <ul class="level 1">
        <li>parent</li>
        <li>parent</li>
            <ul class="level 2">
                <li>child</li>
                <li>child</li>
            </ul>
            <ul class="level 3">
                <li>sibling</li>
                <li>sibling</li>
            </ul>
    </ul>
    <script>
        $("ul.level-2").siblings('ul').css('background-color', 'green');
    </script>

Lab 4
=====

- Practice using the following DOM traversal methods.

  - .children()
  - .closest()
  - .find()
  - .next(), .nextAll(), .nextUntil()
  - .offsetParent()
  - .parent(), .parents(), .parentsUntil()
  - .prev(), .prevAll(), .prevUntil()
  - .siblings()

================
DOM Manipulation
================

.addClass()
===========

Adds the specified class(es) to each of the set of matched elements.

.. code-block:: html

    <script>
    $(".content").children("p")
        .addClass("highlight");
    </script>

.after()
========

Insert content, specified by the parameter, after each element in the set of
matched elements.

.. code-block:: html

    <p>Hello</p>
    <script>
    $("p").after("World!");
    </script>

.append()
=========

Insert content, specified by the parameter, to the end of each element in the
set of matched elements.

.. code-block:: html

    <p>Hello</p>
    <script>
    $("p").append(" World!");
    </script>

.appendTo()
===========

Insert every element in the set of matched elements to the end of the target.

.. code-block:: html

    <div class="content">
    <p>Hello</p>
    <script>
    $("World!").appendTo("p");
    </script>

.attr()
=======

Get the value of an attribute for the first element in the set of matched
elements or set one or more attributes for every matched element.

.. code-block:: html

   <img id="jquery-logo" src="jquery.jpg" />
   <script>
   $("#jquery-logo").attr("alt", "jQuery Logo");
   </script>

.before()
=========

Insert content, specified by the parameter, before each element in the set of
matched elements.

.. code-block:: html

   <p>World!</p>
   <script>
   $("p").before("Hello ");
   </script>

.clone()
========

Create a deep copy of the set of matched elements.

.. code-block:: html

    <p>Hello</p>
    <b>World!</b>
    <script>
    $("b").clone().appendTo("p");
    </script>

.css()
======

Get the value of a style property for the first element in the set of matched
elements or set one or more CSS properties for every matched element.

.. code-block:: html

    <style>
    .highlight { background-color: yellow; }
    </style>
    <script>
    $(".content").css("highlight");
    </script>

.empty()
========

Remove all child nodes of the set of matched elements from the DOM.

.. code-block:: html

    <div class="content">
        <p>Hello</p>
        <p>World</p>
    </div>
    <script>
    $(".content").empty();
    </script>

.height()
=========

Get the current computed height for the first element in the set of matched
elements or set the height of every matched element.

.. code-block:: html

    <style>
    div { width: 50px; height: 50px; float: left; margin: 5px; background: red; }
    </style>
    <div></div>
    <div></div>
    <script>
    $("div").on("click", function() {
        $(this).height(30)
            .css("background-color", "green");
        });
    </script>

.html()
=======

Get the HTML contents of the first element in the set of matched elements or
set the HTML contents of every matched element.

.. code-block:: html

    <div class="foo"></div>
    <script>
    $("div.foo").html("Hello World");
    </script>

.insertAfter()
==============

Insert every element in the set of matched elements after the target.

.. code-block:: html

    <p id="world">World!</p>
    <p id="hello">Hello</p>
    <script>
    $("p#world").insertAfter("p#hello");
    </script>

.insertBefore()
===============

Insert every element in the set of matched elements before the target.

.. code-block:: html

    <p id="world">World!</p>
    <p id="hello">Hello</p>
    <script>
    $("p#hello").insertBefore("p#world");
    </script>

.prepend()
==========

Insert content, specified by the parameter, to the beginning of each element in
the set of matched elements.

.. code-block:: html

    <p>World</p>
    <script>
    $("p").prepend("Hello ");
    </script>

.prependTo()
============

Insert every element in the set of matched elements to the beginning of the
target.

.. code-block:: html

   <p id="world">World</p>
   <p id="hello">Hello </p>
   <script>
   $("p#hello").prependTo("p#world");
   </script>

.prop()
=======

Get the value of a property for the first element in the set of matched
elements or set one or more properties for every matched element.

.. code-block:: html

    <input type="checkbox" />
    <input type="checkbox" />
    <script>
    $("form input").filter(":checkbox").prop("checked", true);
    </script>

.remove()
=========

Remove the set of matched elements from the DOM.

.. code-block:: html

    <button>Click to Remove paragraphs</button>
    <p>Hello World!</p>
    <script>
    $("button").on("click", function() {
        $("p").remove()
    });
    </script>

.removeAttr()
=============

Remove an attribute from each element in the set of matched elements.

.. code-block:: html

    Name: <input type="text" name="name" value="John Doe" />
    <script>
    $("input").filter(":text").removeAttr("value");  
    </script>

.removeClass()
==============

Remove a single class, multiple classes, or all classes from each element in
the set of matched elements.

.. code-block:: html

    <p class="highlight">Hello World</p>
    <p class="highlight">Hello World</p>
    <p class="highlight">Hello World</p>
    <p class="highlight">Hello World</p>
    <script>
    $("p").filter(":even").removeClass("highlight");
    </script>

.replaceAll()
=============

Replace each target element with the set of matched elements.

.. code-block:: html

    <p>Goodbye World</p>
    <p>Goodbye World</p>
    <p>Goodbye World</p>
    <script>
    $("Hello World").replaceAll("p");
    </script>

.replaceWith()
==============

Replace each element in the set of matched elemesnt with the provided new
content and return the set of elements that was removed.

.. code-block:: html

    <p>Goodbye World</p>
    <p>Goodbye World</p>
    <p>Goodbye World</p>
    <script>
    $("p").replaceWith("Hello World");
    </script>

.text()
=======

Get the combined text contents of each element in the set of matched elements,
including their descendants, or set the text contents of the matched elements.

.. code-block:: html

    <script>
    $("p").text("Hello World");
    </script>

.toggleClass()
==============

Add or remove one or more classes from each element in the set of matched
elements, depending on either the class's presence or the value of the switch
argument.

.. code-block:: html

    <p class="highlight">Hello World</p>
    <p class="">Hello World</p>
    <p class="">Hello World</p>

    <button>Click to Toggle</button>
    <script>
    $("p").on("click", function() {
        $(this).toggleClass("highlight");
    });
    </script>

.unwrap()
=========

Remove the parents of the set of matched elements from the DOM, leaving the
matched elements in their place.

.. code-block:: html

    <div>
        <p>Hello</p>
        <p>World</p>
    </div>
    <script>
    $("p").unwrap();
    </script>

.width()
========

Get the current computed width for the first element in the set of matched
elements or set the width of every matched element.

.. code-block:: html

    <style>
    div { width: 50px; height: 50px; float: left; margin: 5px; background: red; }
    </style>
    <div></div>
    <div></div>
    <script>
    $("div").on("click", function() {
        $(this).width(30)
            .css("background-color", "green");
        });
    </script>

.wrap()
=======

Wrap an HTML structure around each element in the set of matched elements.

.. code-block:: html

    <p>Hello</p>
    <p>World</p>
    <script>
    $("p").wrap("<div></div>");
    </script>


.wrapAll()
==========

Wrap an HTML structure around all elements in the set of matched elements.

.. code-block:: html

    <p>Hello</p>
    <p>World</p>
    <script>
    $("p").wrapAll("div");
    </script>

.wrapInner()
============

Wrap an HTML structure around the content or each element in the set of matched
elements.

.. code-block:: html

    <p>Hello</p>
    <p>World</p>
    <script>
    $("p").wrappInner("<strong></strong>");
    </script>

Lab 5
=====

- Use jQuery to manipulate selected elements within your document.
- Implement 10 of the following DOM manipulation methods.

 - .addClass(), .after(), .append(), .appendTo(), .attr(), .before(), .clone(), .css(), .empty(), .height(), .html(), .insertAfter(), .insertBefore(), .prepend(), .prependTo(), .prop(), .remove(), .removeAttr(), .removeClass(), .replaceAll(), .replaceWith, .text(), .toggleClass(), .unwrap(), .width(), .wrap(), .wrapAll(), .wrapInner()

======
Events
======

.click()
========

Bind an event handler to the "click" JavaScript event, or trigger that event 
on an element.

.. code-block:: html

    <button>Click Me</button>
    <script>
    $('button').on('click', function() {
        alert('Handler for .click() called.");
    });
    </script>

.dblclick()
===========

Bind an event handler to the "dblclick" JavaScript event, or trigger that event 
on an element.

.. code-block:: html

    <button>Click Me</button>
    <script>
    $('button').on('dblclick', function() {
        alert('Handler for .dblclick() called.");
    });
    </script>

.focusin()
==========

Bind an event handler to the "focusin" event.

.. code-block:: html

    <style>
    span { display: none; }
    </style>
    <p><input type="text" /><span>.focusin() triggered</span></p>
    <p><input type="text" /><span>.focusin() triggered</span></p>
    <script>
    $("p").on("focusin", function() {
        $(this).find("span").css("display", 'inline').fadeOut(1000);
    });
    </script>

.hover()
========

Bind two handlers to the matched elements, to be executed when the mouse
pointer enters and leaves the elements.

.. code-block:: html

    <script>
    $('h2').hover(function() {
        $('p').slideToggle();
    });
    </script>

.mousedown()
============

Bind an event handler to the "mousedown" JavaScript event, or trigger that
event on an element.

.. code-block:: html

    <script>
    $('#target').mousedown(function() {
        alert('Handler for .mousedown() called.');
    });
    </script>

.mouseenter()
=============

Bind an event handler to be fired when the mouse enters an element, or trigger
that handler on an element.

.. code-block:: html

    <script>
    $('#target').mouseenter(function() {
        alert('Handler for .mouseenter called.');
    });
    </script>

.mouseleave()
=============

Bind an event handler to be fired when the mouse leaves an element, or trigger
that handler on an element.

.. code-block:: html

    <script>
    $('#target').mouseleave(function() {
        alert('Handler for .mouseleave called.');
    });
    </script>

.mouseout()
===========

Bind an event handler to the "mouseout" JavaScript event, or trigger that event
on an element.

.. code-block:: html

    <div id="outer">Mouse Out</div>
    <script>
    $('#outer').mouseout(function() {
        alert('Handler for .mouseout() called.');
    });
    </script>

.mouseup()
============

Bind an event handler to the "mousedown" JavaScript event, or trigger that
event on an element.

.. code-block:: html

    <script>
    $('#target').mouseup(function() {
        alert('Handler for .mouseup() called.');
    });
    </script>

.select()
=========

Bind an event handler to the "select" JavaScript event, or trigger that event
on an element.

.. code-block:: html

    Username: <input type="text" name="username" value="username" /><br />
    Password: <input type="password" name="password" value="password" />
    <div></div>
    <script>
        $(":input").select(function() {
            $("div").text("Something was selected").show().fadeOut(1000);
        });
    </script>

.submit()
=========

Bind an event handler to the "submit" JavaScript event, or trigger that event
on an element.

.. code-block:: html

    <script>
    $("form").submit(function() { 
        return false; 
    });
    </script>

Lab 6
=====

- Use jQuery to monitor selected events within your document.
- Implement 5 of the following event methods.

 - .click(), .dblclick(), .focusin(), .hover(), .mousedown(), .mouseenter(), .mouseleave(), .mouseout(), .mouseup(), .select(), .submit()

Lab 7
=====

- CSS Switcher
- Dynamic Content

Lab 8
=====

- FAQ
- Contact Form
- Image Slider

============
Class Review
============

Please take five minutes to review the course.

Contact Me
==========

Christer Edwards

- christer.edwards@gmail.com

====================
Working with the DOM
====================

Modifying the DOM
-----------------

The DOM is built starting with an element, typically the BodyElement which is obtained easily as follows:

.. code-block:: kotlin

   import io.kweb.*
   import io.kweb.dom.element.*

   fun main() {
     Kweb(port = 8091) {
        val body : BodyElement = doc.body
    }
   }

Let's create a button element as a child of the body element, we do this using the *.new* function (which is
supported by all Element types):

.. code-block:: kotlin

        val body : BodyElement = doc.body
        body.new {
            val clickMe = button().text("Click Me!")
        }

As you can see, it's easy to set the text of an element, you can also modify its attributes:

.. code-block:: kotlin

            clickMe.setAttribute("class", "bigbutton")

Or delete it:

.. code-block:: kotlin

    clickMe.delete()

Reading the DOM
---------------

You can read values from the DOM too:

.. code-block:: kotlin

    doc.body.new {
        val label = h1().text("What is your name?")
        val clickMe = input(type = text, placeholder = "Enter your name")
        clickMe.on.blur {
            GlobalScope.launch {
                label.text(clickMe.getValue().await())
            }
        }
    }

Notice that *clickMe.getValue() doesn't return a String, it returns a *CompletableFuture<String>.
This is because retrieving something from the DOM requires some communication with the browser and
will take some time - and we don't want to block while we wait.

This allows us to take advantage of Kotlin's `coroutines <https://kotlinlang.org/docs/reference/coroutines/basics.html>`_
functionality to make this fairly seamless to the programmer (using *GlobalScope.launch* and *await()*.

Listening for events
--------------------

(TODO) Explain how to attach DOM listeners and handle them.

Immediate events
----------------

(TODO) Explain how to respond to DOM events without a server round trip
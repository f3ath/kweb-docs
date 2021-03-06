===========
CSS & Style
===========

Kweb has out-of-the-box support for the excellent `Fomantic UI <https://fomantic-ui.com>`_
framework, which helps create beautiful, responsive layouts using human-friendly HTML.

Getting started
---------------

First tell Kweb to use the Fomantic UI plugin:

.. code-block:: kotlin

    import io.kweb.plugins.fomanticUI.*

    fun main() {
        Kweb(port = 16097, plugins = listOf(fomanticUIPlugin)) {
            // ...
        }
    }

Now the plugin will add the Fomantic CSS and JavaScript code to your website automatically.

Let's look at one of the simple examples from the `Fomantic UI <https://Fomantic-ui.com/elements/input.html>`_
documentation:

.. code-block:: html

    <div class="ui icon input">
      <input type="text" placeholder="Search...">
      <i class="search icon"></i>
    </div>

This translates to the Kotlin:

.. code-block:: kotlin

    import io.kweb.plugins.fomanticUI.*
    import io.kweb.dom.element.creation.tags.InputType.*

    fun main() {
        Kweb(port = 16097, plugins = listOf(fomanticUIPlugin)4) {
            div(fomantic.ui.icon.input).new {
                input(type = text, placeholder = "Search...")
                i(fomantic.search.icon)
            }
        }
    }

Take a look at the `Fomantic UI documentation <https://fomantic-ui.com>`_ to see everything else it can do.

Other UI Frameworks
-------------------

It's easy to create Kweb plugins for many JavaScript tools and frameworks, taking full advantage of Kotlin's DSL
capabilities.

The `Fomantic UI plugin implementation <https://github.com/kwebio/kweb-core/tree/master/src/main/kotlin/io/kweb/plugins/fomanticUI>`_
itself can serve as an example.

Example and Demo
----------------

See a simple app built using Fomantic UI and Kweb (with source): http://demo.kweb.io:7659/
---
title: Overview
meta_title: Kendo UI Menu for PHP widget documentation
meta_description: How to add and bind Kendo UI Menu for PHP widget.
slug: php-menu-overview
publish: true
relatedDocs: php-ui-menu
---

# Menu

The Menu class is a server-side wrapper for the [Kendo UI Menu](/kendo-ui/api/web/menu) widget.

## Getting Started

Here is how to configure a simple Kendo Menu:

1. Follow the steps from the [introduction](/kendo-ui/getting-started/using-kendo-with/php/introduction) - include the autoloader, JavaScript and CSS files.

1. Create a [menu](/kendo-ui/api/wrappers/php/Kendo/UI/Menu) and set its [items](/kendo-ui/api/wrappers/php/Kendo/UI/Menu#additem)

        <?php
        $menu = new \Kendo\UI\Menu('menu');
        $item1 = new \Kendo\UI\MenuItem();
        $item1->text("Item 1")
                ->startContent();
        ?>

        First Item Static Content

        <?php
        $item1->endContent();
        $item2 = new \Kendo\UI\MenuItem();
        $item2->text("Item 2")
                ->startContent();
        ?>
            Second Item Static Content
        <?php
        $item2->endContent();

        $menu.addItem($item1, $item2);
        ?>

1. Output the menu by echo-ing the result of the [render](/kendo-ui/api/wrappers/php/Kendo/UI/Widget#render) method.

        <?php
        echo $menu->render();
        ?>

## Getting Client-side Reference

You can reference the client-side Kendo Menu instance via [jQuery.data()](http://api.jquery.com/jQuery.data/).
Once a reference has been established, you can use the [API](/kendo-ui/api/web/menu#methods) to control its behavior.

### Example

    <?php
    $menu = new \Kendo\UI\Menu('menu');
    echo $menu->render();
    ?>
    <script>
    $(function() {
        // The constructor parameter is used as the 'id' HTML attribute of the menu
        var menu = $("#menu").data("kendoMenu");
    });
    </script>

## Handling Events

You can subscribe to all menu [events](/kendo-ui/api/web/menu#events).

### Example - subscribing by specifying JavaScript function name

    <?php
    $menu = new \Kendo\UI\Menu('menu');

    // The 'menu_select' JavaScript function will handle the 'select' event of the menu
    $menu->expand('menu_select');

    echo $menu->render();
    ?>
    <script>
    function menu_select() {
        // Handle the select event
    }
    </script>

### Example - providing inline JavaScript code

    <?php
    $menu = new \Kendo\UI\Menu('menu');

    // Provide inline JavaScript code that will handle the 'select' event of the menu
    $menu->select('function() { /* Handle the select event */ }');

    echo $menu->render();
    ?>



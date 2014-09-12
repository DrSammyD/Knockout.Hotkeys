About
=====
**Knockout.Hotkeys** is a hotkeys plugin for **Knockout.js** allowing you to define global hotkey bindings.

Syntax
------
You can define a hotkey by using one of three binding attributes

* hotkeydown
* hotkeyup
* hotkeypress

The actual syntax is then as follows:

    <input type="text" data-bind="hotkeydown: { shift1 : doSomething }" />

If you would prefer your keys to be a little more readable, you can also define them in the following format:

    <input type="text" data-bind="hotkeydown: { 'shift+1' : doSomething }" />

You can also register multiple hotkey combos within a single binding statement as follows:

    <input type="text" data-bind="hotkeydown: [{ 'shift+1' : doSomething }, { 'shift+2' : doSomethingElse }]" />

In addition to the key combination option, you can also provide an if statement which must be met to allow the hotkey to trigger:

    <input type="text" data-bind="hotkeydown: { 'shift+1' : doSomething, if: currentItem() == $data }" />

Lastley, you can also use a more verbose definition syntax to allow the creating of dynamic key combinations:

    <input type="text" data-bind="hotkeydown: { key: 'shift+' + $data.substr(0,1).toLowerCase(),  do: doSomething }" />

Options
-------
By default the hotkey event handlers are bound to the window object, you can override this by setting the ko.hotkeys.defaultOptions.bindElement, to the element you wish to bind to (this must be done before ko.applyBindings is called):

    ko.hotkeys.defaultOptions.bindElement = document;
    
Updates
-------
09/11/2014 - Enhanced parsing of hotkey to allow multiple special characters (previous replace function only replaced first "+" symbol, now replaces all "+" that are followed by another "+", word, or digit)

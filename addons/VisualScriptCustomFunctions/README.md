VisualScriptCustomFunc
===
The VisualScript Node between languages
 
## Table of Contents
[TOC]

## Getting started

Drag a `VisualScriptCustomFunc` in a VisualScript

### Examples

addons\VisualScriptCustomFunc\Examples
Feel free to duplicate

### Creating a new node

1. To create a new node you have to create a new `tool` script.
2. `extends VisualScriptCustomFunc`
3. Overwrite function `_custom_function()`
4. Node_name is the same as the script_name.
```
tool
extends VisualScriptCustomFunc

func _custom_function():
	return "value"
```
5. Drag this script in your VisualScript
Alternatively you are able to create a `VisualScriptCustomNode` and assign the script to it.

## advanced users

### _input_clues _output_clues
You probably now how to typecast a type string to a variable. Just like in other scripts you would like to expose more details about your variable to the editor so that the editor in return will help you specifie that information.

Therefore `VisualScriptCustomFunc` has two arrays `_input_clues` `_output_clues` which you may populate on `_init()` wit property dictionary’s to help the editor, colleagues or when future you will read the intent.

Property dictionary’s are able to hold 5 key values.
* "name" = String
* "type" = int `Variant.Type`
* "value" = any
* "hint" = int `PropertyHint`
* "hint_string" = String

By default the node will try to guess as many clues as possible.
The specified hints overrule this automated guess. 
:::info
Name and value are **not yet** working as intended so always specify them by using `_input_clues` `_output_clues`
:::

### _output_clues extra

The return type will be used to for `_output_clues`.
When there is no return type or type Array. You are able to hint and use multiple output ports.
1. Return type is `Array` or nothing.
2. `_output_clues` needs multiple property dictionary’s
3. Function **must** return array of values

## Sequencing
The sequence port of `VisualScriptCustomFunc` is optional.
By default `sequenced` is `false`.
When you have a function that is not returning any value it will be best to default `sequenced` to `true` on `_init()`.

## warning

Please do not overwrite `VisualScriptCustomNode` functions.

## Known issues

property dictionary’s not able to get `name`, `value` from function definition.

## Appendix and FAQ
:::info
**Want to contribute to the library?** Leave a comment!
**Find this document incomplete?** Leave a comment!
:::
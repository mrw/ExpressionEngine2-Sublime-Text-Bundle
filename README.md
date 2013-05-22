ExpressionEngine 2.0 Sublime Text 3 Bundle
==========================================

ExpressionEngine support package for Sublime Text 2 &amp; 3 that also supports the [jQuery bundle](https://github.com/mrmartineau/jQuery) syntax when inside of `<script>` tags.

PLUS:

* Highlighting for built-in EE adddon tags (exp:channel:entries)

* Improved handling of EE comments:
* (does not highlight/color code blocks contained within EE comments)
* (recognizes EE comments within quoted strings)
* (recognizes EE comments and tags within Javascript blocks)
* (recognizes EE comments and tags within PHP blocks)

* Highlighting for EE module attributes (channel=, limit=, etc)

* Highlighting for EE global variables ({site_name}, {user_name}, etc)

* Highlighting for deprecated EE tags (marked as "invalid.illegal")



NOTES:

You must install a jQuery support package to take full avantage of this package.

The HTML5 package for ST may override this package and prevent proper highlighting.

To take full advantage of the extended syntax highlighting made available with this package, you will want to use a full-featured Sublime Text color theme. Specifically, your theme should assign unique styling to the following scopes:

* entity.function
* entity.other
* invalid
* keyword.control
* keyword.operator
* support.constant
* support.function
* support.variable
* variable
* variable.parameter

More comprehensive coloring can be accomplished by also assigning styling to these more specific scopes:

* ee.tag.html
* entity.function.addon.ee
* entity.other.attribute-name.user.ee
* entity.other.attribute-name.predefined.ee
* invalid.illegal
* invalid.deprecated
* keyword.control.ee
* keyword.operator.logical
* support.constant.ee
* support.function.addon.ee
* support.variable.language.ee
* variable.parameter.ee
* variable.other.ee


Forked and modified from [imjared's ExpressionEngine2-Sublime-Text-Bundle][https://github.com/imjared/ExpressionEngine2-Sublime-Text-Bundle], which had this note:

Forked and only slightly modified from [Wes Baker's EE 2 TextMate Bundle][https://github.com/wesbaker/ExpressionEngine2.tmbundle], which had this note:

A reworked version of [Tim Kelty's ExpressionEngine bundle](http://github.com/timkelty/expressionengine-tweaked-tmbundle), updated to work with ExpressionEngine 2.0.

Installation
------------

1. Click the Downloads button at the top right of this page.
2. Choose the zip file.
3. Once downloaded, unzip the the zip file.
4. If you're looking at a folder, rename it to ExpressionEngine. If you're looking at a set of files, create a new folder named ExpressionEngine and put the files in.
5. Copy the folder to ~/Library/Application Support/Sublime Text 2/Packages/ (make sure this is the Library inside your home folder, not the one in the root of your hard drive)





REMAINING PROBLEMS WITH THIS SYNTAX
-----------------------------------

A list of shortcomings with this syntax definition (and test cases for each) is included in the file "known_problems.html".

Many of the problems below have to do with nesting multiple syntaxes, and could probably be fixed with grammar injection if Sublime Text supports it.

I'd be happy to incorporate solutions to these problems (and any other improvements); please initiate a pull request, or just contact me directly.

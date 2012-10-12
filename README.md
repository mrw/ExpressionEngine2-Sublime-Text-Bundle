ExpressionEngine 2.0 Sublime Text 2 Bundle
====================================

ExpressionEngine Sublime Text 2 that also supports the [jQuery bundle](https://github.com/mrmartineau/jQuery) syntax when inside of `<script>` tags.

Forked and only slightly modified from [Wes Baker's EE 2 TextMate Bundle](https://github.com/wesbaker/ExpressionEngine2.tmbundle), which had this note: 

A reworked version of [Tim Kelty's ExpressionEngine bundle](http://github.com/timkelty/expressionengine-tweaked-tmbundle), updated to work with ExpressionEngine 2.0. 

Automatic Instlalation (OSX Only)
------------
Run the following command in Terminal to install the ExpressionEngine bundle.

```
cd /tmp && curl -s https://nodeload.github.com/mrw/ExpressionEngine2-Sublime-Text-Bundle/tarball/master -o expressionengine.tar.gz && tar -xzf expressionengine.tar.gz > /dev/null && mv ./mrw-ExpressionEngine2-Sublime-Text-Bundle* ~/Library/Application\ Support/Sublime\ Text\ 2/Packages/expressionengine && rm -f expressionengine.tar.gz && echo "The ExpressionEngine bundle for Sublime Text 2 is now installed."
```

Manual Installation
------------

1. Click the Downloads button at the top right of this page.
2. Choose the zip file.
3. Once downloaded, unzip the the zip file.
4. If you're looking at a folder, rename it to ExpressionEngine. If you're looking at a set of files, create a new folder named ExpressionEngine and put the files in.
5. Copy the folder to ~/Library/Application Support/Sublime Text 2/Packages/ (make sure this is the Library inside your home folder, not the one in the root of your hard drive)
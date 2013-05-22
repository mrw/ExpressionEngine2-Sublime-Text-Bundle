ExpressionEngine 2.0 Sublime Text 2 Bundle2
===========================================

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



NOTE:

The HTML5 package for ST may override this package and prevent proper highlighting.

Forked and modified from [imjared's ExpressionEngine2-Sublime-Text-Bundle][https://github.com/imjared/ExpressionEngine2-Sublime-Text-Bundle], which had this note:

Forked and only slightly modified from [Wes Baker's EE 2 TextMate Bundle](https://github.com/wesbaker/ExpressionEngine2.tmbundle), which had this note:

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

Below is a list of shortcomings with this syntax definition and test cases for each.

Many of the problems below have to do with nesting multiple syntaxes, and could probably be fixed with grammar injection if Sublime Text supports it.

I'd be happy to incorporate solutions to these problems (and any other improvements); please initiate a pull request, or just contact me directly.

From higher to lower priority:


(1) Nested quotes (EE tag containing quote nested inside quoted string). Actually a nested syntax challenge -- EE tags within HTML tags:

	<a href="{path="channel/archives"}">{month}, {year}</a>
	<a href="{day_path="channel/index"}">{day_number}</a>
	<a href="{title_permalink="channel/index"}">{title}</a>
	<a href="{profile_path="member/profile"}">{author}</a>

(2) Nesting EE tags inside HTML tags _AND_ not losing full highlighting of all HTML (solving both requirements probably requires injection grammar):

	<a {!-- COMMENT --} href="{path="channel/archives"}">
		<img src="foo" alt="{site_name}" />
	</a>

(3) No coloring of php code (hidden cost of properly coloring EE code within PHP code)

	 <?php echo 'hello {username}'; ?>

(4) EE code inside CSS (CSS definitions get messed up by EE brackets). Possible solution: inject EE definition (at least comments) into CSS and JS and PHP syntaxes?? Or use Matching Nested Constructs feature of regex

	<style>
		{!-- comment --}
		.my_class { background:#fff; content:{site_name}; }
		{!-- .unwanted_class {background:green;} --}
		{if logged_in}
			html{ {if group_id == 1}background:yellow;{/if} }
		{/if}
		body{ background:{!-- white --} black;}
	</style>
	/* THIS TEXT IS INTERPRETED AS A "comment.block.css" EVEN THOUGH IT"S OUTSIDE THE STYLE BLOCK ABOVE. ALL HIGHLIGHTING IS BROKEN FROM HERE ON OUT DUE TO EE COMMENT ABOVE. SECOND STYLE TAG BELOW IS NEEDED TO CLOSE THE STYLE BLOCK AND RESTORE ORDER. */
	</style>

(5) EE tags inside HTML tags. Presents like nested quotes problem (EE tag containing quote nested inside quoted string):

	<a href="{path="channel/archives"}">{month}, {year}</a>
	<a href="{day_path="channel/index"}">{day_number}</a>
	<a href="{title_permalink="channel/index"}">{title}</a>
	<a href="{profile_path="member/profile"}">{author}</a>

(6) Don't match local variables preceded by colon:

	{nothing:here:should:be:colored:item:version}
	{this_too:item}
	{bands:title}

	NOTE: Make sure formatting of these is not disturbed:
	{if (timezone == 2 OR
timezone > 6 OR (can_edit)) OR
 channel_id)
}
{if (member_id == 2 OR
current_page > 6 OR (member_id)) OR
 member_id)
}

(7) Dont highlight variables preceded by end slashes that shouldnt be there:

	{header}	 	is valid
	{/header}	 	is valid
	{site_name} 	is valid
	{/site_name} 	is INVALID
	{author}		is valid
	{/author}		is INVALID
	{author x="x"}	is valid
	{x /author}		is INVALID
	(all INVALID tags should go uncolored)

	NOTE: Make sure formatting of these is not disturbed:
	{if (timezone == 2 OR
timezone > 6 OR (can_edit)) OR
 channel_id)
}
{if (member_id == 2 OR
current_page > 6 OR (member_id)) OR
 member_id)
}

(8) Allow logical operators to not be surrounded by spaces. Both these are legal:

	{if name == "bozo"}
	{if name=="bozo"}

(9) EE comments (and code) in quoted string are not colored. (maybe this is as it should be, it could get confusing if quotes not uniformly colored?)

	<a href="{path=blog}{!-- COMMENT --}" title="{site_name}">{!-- COMMENT--}{site_name}</a>

(10) Distinguish between local and global for variables that can be either (requires compiler, or possibly setting scope between open and close tags inclusive):

	{location}
	{exp:member:custom_profile_data}
		{location}
	{/exp:member:custom_profile_data}




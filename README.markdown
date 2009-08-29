Lauch App Scripts
=================

Automated creation of Application launching scripts for use with your favorite keyboard shortcut tool.  This was written as a replacement for my Quicksilver addiction after upgrading to Snow Leopard.

The Rakefile was derived from [Grant Hollingworth's][3] [command-number-tab][4].

Install
-------

1. Change the APPLICATIONS constant at the top of the Rakefile
2. Compile and install the AppleScripts with `rake install`. The scripts will be installed under `~/Library/Scripts/Launch`
3. Set up keyboard shortcuts with [FastScripts][1] (or [Butler][2] or whatever)

[1]: http://www.red-sweater.com/fastscripts/
[2]: http://www.petermaurer.de/butler/
[3]: http://granth.ca/
[4]: http://github.com/granth/command-number-tab/tree/master

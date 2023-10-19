# index basher
This is an incredibly basic static site generator written in bash. It crawls the working directory and recursively generates an index.html file for each directory. How the html file looks can be configured in a .config file. The html consists of a preamble, a list of links to all files and child directories in the directory, and a postamble.

This project makes use of:
- sed
- awk
- ls

# .config
a .config file consists of a series of named blocks containing the needed information. a block consists of `\[<name>\] <text> \[end\].
The options you have access to are:
- \[index_preamble\] houses everything that comes before the link list, including the <head></head> and opening <body> tag.
- \[index_postamble\] houses the closing </body> tag and anything you would like to put before it
- \[card_preamble\] allows you to wrap links in extra decoration
- \[card_postamble\] allows you to wrap links in extra decoration
- \[ignore\] houses a list of files to ignore
- \[protected\] the protected option will prevent the existing index.html from being overwritten.

# not yet implemented
- index protection
- would like to expose some variables to config

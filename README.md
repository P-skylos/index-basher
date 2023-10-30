# index basher
This is an incredibly basic static site generator written in bash. It crawls the working directory and recursively generates an index.html file for each directory. How the html file looks can be configured in a .config file. The html consists of a preamble, a list of links (called cards) to all files and child directories in the directory, and a postamble.

Despite its very limited functionality, you may want to use this tool if you desire a site generator with minimal overhead. The only additional files it creates are an index.html file in each directory it crawls, and it only makes use of a single optional .config file in each directory. This is great if, for example, you have a directory full of pictures you would like to simply upload to a site so you have something to link your friends to. I made a small site <grandmas-cabin.neocities.org> to demonstrate this sort of use case.

This project makes use of the following utils:
- sed
- awk
- ls
- grep

# use
```bash
index-basher [dir]
```

# .config
a .config file consists of a series of named blocks that index-basher will pull data from. If a .config file does not exist or a specific section inside a config isn't used, index-basher will inherit configuration from the parent directory or use the default configuration if the user never set the variable.

a block consists of `[<name>] <text> [end]`.
The options you have access to are:
- `[doc_preamble]` houses everything that comes before the link list, including the \<head>\</head> and opening \<body> tag.
- `[doc_postamble]` houses the closing \</body> tag and anything you would like to put before it
- `[card]` allows you to set the html generated for each file in the directory
- `[ignore]` houses a list of files to ignore
- `[protected]` the protected option will prevent the existing index.html from being overwritten.

If you wish to escape one of these reserved words, put a backslash inside the brackets `[\foo]`

you may also access the following variables inside your html blocks
- `{{now_date}}` gives the date at compile time in yyy-mm-dd
- `{{now_time}}` gives the compile time in hh:mm
- `{{path}}` gives the path to the current directory
- `{{file}}` **only works within cards** and gives the current file name **if used outside it a card it will not be substituted**

# wishlist
- would like to expose some variables to config
 - file date
- option to whitelist instead of ignore
- fail on bad substitution
- refactor for speed and readability

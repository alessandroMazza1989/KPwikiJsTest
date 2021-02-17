---
title: File Management
description: Redirection and Piping, Navigation and File Management
published: true
date: 2021-02-17T15:48:20.355Z
tags: 
editor: markdown
dateCreated: 2021-02-17T15:39:01.010Z
---

# File Management

## Redirection and Piping

- cmd > file		→ Redirect stdout to file. Overwrites the file each time! To avoid use >>.
- cmd >> file		→ Append stdout to file.
- cmd < file		→ Redirect stdin from file.
- cmd 2> file		→ Redirect stderr to file.
- cmd1 | cmd2		→ Pipe output of cmd1 as input of cmd2. You can pipe multiple commands.

## Navigation and File Management

- pwd			→ Print Working Directory.
- ls			→ List contents of directory.
  - -a			→ Show all files, including hidden files.
  - -l			→ Long format: prints details of files including author and permissions.
              Format: Permissions Owner Group Size Timestamp Filename
  - \*			→ List all files and files in subdirectories.
  - -R			→ List recursively, thus including all subdirectories and their files.
  - -F			→ List contents with their type indicator (directory, executable, etc...).
  - -s			→ List files with their sizes. (-S to sort by file size.)
  - -p			→ Append ‘/’ indicator to directories.
- ll is the equivalent of ls -alF
- file name		→ Returns the type of name. With ‘*’ it classifies all the directory’s objects.
- find dir -attr <-action> → Searches through the dir for files and directories with a given attr.
- cd [path]		→ Change directory to path. Without path it defaults to home directory.
	- **Ex:** cd ..		→ Go to the parent directory.
	- **Ex:** cd -		→ Go to the previous directory (back).
	- **Ex:** cd or cd ~	→ Go to the home directory.
- mkdir name		→ Create a directory named name.
- rmdir name		→ Remove directory named name. If no arguments remove empty directories.
- cp src dest	→ Copy file from src to dest. If dest is current directory use '.' as dest.
	- -r			→ Copy recursively, thus copying all subdirectories and their files.
	- -v			→ Display a per-copy one-line report when copying multiple files.
- mv src dest	→ Move src(s) to dest directory, OR Rename src to dest using ./dest.
- rm file		→ Deletes file (not undoable!).
- touch	file		→ Create void file or edit timestamps of file if it exists. (Default: current time).
- gzip	file		→ Compress file to a .gz format.
- gunzip file		→ Uncompress file from a .gz format.
- unzip file 		→ List, test and extract compressed files in a ZIP archive. (Not installed by default.)
- rename		→ Renaming tool (non-standard, must be installed usually).

## Displaying Files and Text

- echo string		→ Prints string to screen (only useful in scripts).
		- -n			→ No carriage return option. Ignores newlines.
		- echo $var	→ Prints the value of a variable. (See export for how to set ambient variables.)
- cat file(s)		→ Outputs to screen and concatenates file(s). Used to stream a file into a pipe.
	- -s			→ Suppress repeated empty lines.
	- -n or -b		→ Makes each output line numbered.
	- **Ex:** cat >file		→ Creates file named file.
	- **Ex:** cat src > dest	→ Copies contents of scr file to dest file.
	- **Ex:** cat src >> dest	→ Appends contents of scr file to the end of dest file.
	- **Ex:** cat file | cmd 	→ Streams a file into a pipe which allows the command to use it as input.
- zcat file		→ Reads compressed files in a .gz format without needing to unzip them.
- tac file		→ Like cat, but reads file in reverse order.
- more file		→ Pages through file one screenful at a time. SLOW and DEPRECATED → use less.
- less file		→ Opens file and displays it in chunks.
	- q		→ Quit.
	- /pattern	→ Search for a pattern in the file.
	- :g and :G	→ Go to the end or beginning of the file.
	- :xxxg		→ Go to line number xxx.
	- -S		→ Toggle word wrap (long line folding).
	- -s		→ Toggle coalescing of blank lines.
- head			→ Display the first few lines of a file.
- tail			→ Display the last few lines of a file.
	- -f		→ Follow up with new changes. Actively monitors the file (takes over shell). 
		- -numf	→ Follow up with num new changes
	- -n +num	→ Output num less lines from the top. (Top line is 1, so counting starts at 2.)
  
## Searching, Sorting, Counting, Parsing, and Batch Text Manipulation

- grep keywords file	→ Search a file for keywords (CASE SENSITIVE). Prints out the relative lines.
	- grep 'pattern' file	→ Search file for exact pattern, which can be a regEx.
	- -i 				→ Case insensitive search.
	- -v 				→ Display only lines that do not match.
	- -o 				→ Restrict output only to matching patterns.
	- -n 				→ Number each matching line.
	- -c 				→ Print only the total count of matching lines.
	- -E or -P			→ Adds support for more complex regEx.
- wc file		→ Returns lines, words, and chars count of file.
	- -l 		→ Line-count only
	- -w 		→ Word-count only
	- -c 		→ Char-count only
- sort			→ Sort elements. Execute then enter line-separated elements then press ^D to stop.
	- **Ex1:** display the “passwd” file in a-z order →  less etc/passwd | sort	
- diff	file1 file2→ Compares two files and displays the differences (file1 = '<', file2 = '>') .
- uniq			→ Omit and filter out repeated lines. (Or report repeated lines with options.)
	- -c 			→ Adds number of occurrences to the left.
- tr “ch1” “ch2”	→ Replace or Translate characters
- cut			→ Print selected columns of csv-like files.
- paste			→ Merge files row by row in a single csv-like file.
- sed -opt 'script' input_file → Stream EDitor: pattern search and substitution tool.
	- -e 		→ TODO
	- **Script syntax:** '\<line> \<command letter>/\<regex pattern>/\<flags>'
		- **Line (optional):** says which line to apply the script to. 
			- To define a range use x,y. 
			- To refer to the last line use $.
		- **Commands**
			- s/this/that/\<options>	→ Substitute this with that.
			- d/regEx/			→ Delete lines matching regEx.
		- **Flags:**
			- /n 	→ apply to the n-th occurrence.
			- /g 	→ apply to all occurrences (Global).
			- /ng 	→ apply from the n-th occurrence to the end.
			- /p 	→ duplicates the line after the script is applied on it.
	- **Ex1:** Replace unix with linux from the 3rd occurrence. → sed 's/one/two/3g' file.txt 	
	- **Ex2:** Delete first line. → sed '1d' file.txt 
- awk -opt 'selection {action}' input_file → Pattern scanning and processing language.
	- **Options**
		- -f src_file	→ Reads the source from the a src_file, instead of from the command line.
		- -F fs 	→ Uses fs for the input field separator. (Fields are the elements of a line.)
	- **Selections** (resulting lines are "records" whereas resulting elements on a line are "fields")
		- /keyword/	→ Select lines containing the keyword.
	- **Built-in variables** (strings and chars are referenced between “”)
		- $0	 	 → Represents a whole line.
  	- $n	 	 → Represents the n-th whitespace-separated element of a line, called field.
   	- NR	 	 → Number of current input record (i.e., the number the lines).
   	- NF	 	 → Number of fields in the current input record. $NF means the last field.
   	- FS	 	 → Field separator char dividing fields on the input line (default: whitespace).
   	- RS	 	 → Record separator char (default: newline).
   	- OFS	 	 → Output field separator (default: whitespace).
   	- ORS	 	 → Output record separator (default: newline).
	- **Actions** (performed once per every record that matches the pattern)
		- {print} 	 	→ Print every selected line (without selections it prints all the lines).
		- {print f,v}	→ Of the selected lines print only certain fields or variables.
		- {print "string"}	→ Of the selected lines print a certain fixed string.
		- BEGIN{...}		→ Action is executed only once, at the beginning.
		- END{...}		→ Action is executed only once, at the end. Useful when counting.
		- {var = ...}	→ Variable declaration.
		- {if(...) ...}	→ If statement structure.
		- {for(i=num;i<=num;i++)...} → For statement structure.
		- {length(var)}	→ Calculate length of variable
	- **Ex1:** awk '/manager/ {print NR, $0}' file.txt 
		- Prints all lines that contain "manager", numbering them. 
	- **Ex2:** awk 'NR==3, NR==6 {print NR, $0}' file.txt 
		- Prints lines from 3 to 6, numbering them. 
	- **Ex3:** awk '{if (length($0) > max) max = length($0)} END {print max}' file.txt
		- Find the length of the longest line present in the file.
    
## Text Editing Programs

- **Editing programs and tools**
	- vim
	- nano
	- gedit
	- emacs
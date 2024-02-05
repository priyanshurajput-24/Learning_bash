# Basic syntax `sed -e "" filename`


* `-e` tells that some script are passed in command line
* `-n` tells that suppress automatic printing of pattern space `sed -e -n "" filename`
* `sed -e "=" fileaname`  prints the line number of every line.
* `sed -n -e "6p" filename` print only the sisth line.
* `sed -n -e '6!p' filename` print every line except 6th.
* `sed -n -e '$p' filename` print last line.
* `sed -n -e '$!p' filename` print all line except lastone.
* `sed -n -e "$p" filename`  if we use double quote then here `p` is treated as shell variable.
* `sed -n -e '5,8p' filename` print line from 5th line to 8th line.
* `sed -n -e '=;5,8p' filename` print the line of all line, and print line also `5th` to `8th`.
* `sed -n -e '5,8 {=;p;}' filename` print the line number and line from `5th` to `8th`. -- for this address range you need to print line number and line from `5th` to `8th`.
* `sed -n -e '1~3p' filename` print the 1st, 3rd and 5th line and so on.
* `sed -n -e '1~3!p' filename` print the 2st, 3rd, 5th and 6th line and so on.
* `sed -n -e '/pages/{=;p;}' filename` print the line number,line that contain "pages".
* `sed -n -e '/word_bbox/,+2p' filename` prints two lines after that 'word_bbox'/matching word line.
* `sed -e '1d' filename` delete the first line and print rest all.
* `sed -e '$d' filename` delete the last line and print rest all.
* `sed -e '/pages/d' filename` delete the line that contain "pages" and print rest all.
* `sed -e 's/pages/PAGES/g' filename` substitute 'pages' to 'PAGES' in all lines and print full updated file contents.
* `sed -e '1s/pages/PAGES/g' filename` substitute 'pages' to 'PAGES' in 1st line and print full updated file contents.
* `sed -e '1,56s/pages/PAGES/g' filename` substitute 'pages' to 'PAGES' in 1st line to 56th line and print full updated file contents.


 
 
 ##  https://www.youtube.com/watch?v=uCJjZ3cbaAw&t=935s

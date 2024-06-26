OBJECTIVES:
Work with File Reader tools like cat,grep,head,tail,less and more

GREP-GNU Regular expression Parser. It's used for searching texts in a file
CAT-Short for concatenate-Used to combine(concatenate) and read files together,write to a file,create a file and print out a file text.
CAT -A Shows/read hidden texts in a file
CAT-n shows the line numbers of texts
TAIL-Used to read the end of a file:
tail - n 13 /etc/group-It is used to read the last 13 lines of the file group
tail -f Is used to show the latest entries of a file in real time..Suitable for reading logs
HEAD-Used to read the beginning of a fie:
head -n 12 /etc/passwd -Used to read the first 12 lines of the file passwd

LESS AND MORE are examples of pagers.They read one page of a file at a time...
LESS <file> Reads the file.
while using less to read a file, you can specify "/ <text or word>" to search for a text in a file.
n-See next line having <word>
-N-Display Line Numbers

Grep
--
grep -i sinzzu /etc/passwd- ignore case letter
grep -B 3 sinzzu /etc/passwd- print 3 lines preceeding the searched strings
grep- A 3 sinzzu- print  3 lines after the searched strings.
grep -iw "is" /etc/passwd- search for only matched words and not words having is like "this","miss","kiss". 
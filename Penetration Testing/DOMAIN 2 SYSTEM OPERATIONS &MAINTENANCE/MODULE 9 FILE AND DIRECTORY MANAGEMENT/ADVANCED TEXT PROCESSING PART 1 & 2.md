OBJECTIVES-----------------------------------------
Understand the need for advanced text processing.
Work with more advanced processing tools like grep,egrep and fgrep

grep -v "#" /etc/passwd-  exclude the "#" and any line having "#" and reads the file
grep ro* /etc/passwd- Searches for any word having having the letter 'r or o' or both in it.
grep ro. /etc/passwd-Searches any word having both "ro" together in it.

extended grep(egrep)- Can be used for searching multiple words in a file
egrep "ps4| ps5" name1
fgrep for fixed strings..........................................................

PART2-----
OBJECTIVES-
Work with more text processing tools like awk,sed,printf
AWK-The awk command is use to perfrom text processing one line at a time
awk '{print $1}' numbers  -prints the first line of the text in the file "numbers"
awk works with white spacing,it reads according to rows and columns.

awk -F: '{print $1}' /etc/passwd- It omits the colon or ":" by specifying it with "F" and  print $1 means print the first column.
"F" -field seperator,is used to indicate what we want to omit which is the ": or column"

awk '{print $2}' file- prints the second column.

we can use awk -F : '{print "User", NR-1, "is: ",$1}'- user 1 is root
user 2 is debian
e.t.c...............
SED-Short form of string editor. Most useful to change the occurence of a searched string to upper case or lower case or edit a string
sed s/root/ROOT/  /etc/passwd | grep -i root-It edits the first occurence of "root" in /etc/passwd to be in uppercase and uses grep to find all "root" occurence.
"s"-means search
sed s/root/ROOT/g  /etc/passwd | grep -i root
-g Stands for global. it will edit not only the first occurence but every.

PRINTF----------------
%d- displays decimal
%s- displays any argument as a string
\n- return to the next line

printf "The %s barks %d times" dog 5
output>>The dog barks 5 times

printf 

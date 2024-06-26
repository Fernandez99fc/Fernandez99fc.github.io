  OBJECTIVES
--
Purpose of Text Processing in linux.
work with Text Processing tools like tr,sort,cut,wc,paste

COMMANDS-
echo-Outputs something to the screen
echo james is tall > "file1"- echos "james is tall " to file1

tr or TRANSLATE can be used to translate lower case to upper case and uppercase to lower case.
tr 'a-z' 'A-Z' <(stdinp) filename- It changes the letters in lowercase to upper case 
tr 'A-Z' 'a-z' <(stdinp) filename-It changes the letters in uppercase to lower case
tr -d [:digit:] < filename- To remove digits from a file text

SORT commands-----
sort filename- will sort out the content of the file
sort -n filename- To sort file contents according to numbers
sort -k 2 filename- Sorts file contents alphabetically

CUT is a delimeter for (columns,period(.),comma(,) or any punctuation.---------------
It is used to eliminate column in a file
cut -d ":" -f1 /etc/passwd- note: f1 means first line,f2 second line and so on.

wc-give us the number of lines,words and total characters in a text file.

PASTE-----
paste  can be used for reading files together without being on the same line
paste file1 file2

note:bash or ./ to extract files


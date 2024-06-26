OBJECTIVES-------------------------
1)Redirect Standard (stdout)output
2)Redirect Standard error(stderr) output
3)Combine stdout and stderr redirections
4)Redirect Standard (stdinp)input

stdout(1)-It's used for redirecting an output
stuffs like
cat <filename>
cat>>
cat>
cat file1 >>file2- redirect file1 content to file2 and read it.
echo "text" > file or >> to append 
cat file1 file2- reads both files
cat file1> file2- redirects files1's contents to file2

Standard Input(0)-uses < and <<(heredoc)
Can be used to direct an instruction to a file...
sort < filename- will sort out the file texts in the file
sort <namefile >namefile2- Will sort out namefile contents and output it to name2file

HEREDOC<<Used to send commands while writing a text

stderr(2) uses 2> and 2>>- used for redirecting errors
2> It is used for redirecting errors into another file.
file1-exist
file2-does not

cat file2 2>file1
cat file2 2>>file1-Appends another line to it.

Combining stdout and sterr(&>)
file1-exist
file2-exist
file3-doesnt

cat file3 2> file 2 -outputs error to file 2 and can only accespt error redirection as an append
cat file1 file3 &> outputs both error and standard output to file 2
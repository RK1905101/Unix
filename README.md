**Basic top 15 commands in Unix**

- ls : _used for listing files/directories_ <br>
Syntax: >> ls <br> 
Options:  -l, -r, -t, -h, -a <br>

-	mkdir: used for creating new directory. <br>
Syntax: >> mkdir directoryName <br>

-	rmdir: remove directory <br>
Syntax: >> rmdir directoryName <br>

-	cp : copy one file content to other <br>
Syntax: >> cp [option] file1 file2 <br>
	cp directoryPath .     ( .  means current directory) <br>
	cp file1 directoryName <br>
Options: -i  interactive <br>


-	mv: move one or many files to other location/directory (Also we call it as CUT-PASTE command or RENAME command) <br>
Syntax: mv file1  file2  <br>
	mv file1 file2  directory <br>

-	rm : remove files <br>
Syntax: rm filename <br>
Options:  -i  interactive <br>

-	cat : create and read file <br>
Syntax: To create  cat > filename <br>
	To read  cat filename <br>

-	vi : create, read and edit file <br>
Syntax: To create and read  vi filename <br>
	(Once you type above command and hit enter, you will get into vi editor) <br>
	To insert data  Press “ i “ <br>
	To get out of insert command  press ESC <br>
	To save and exit editor  type “ :wq “ <br>

-	wc : display line, word and character counts in file <br>
Syntax: wc [options] filename <br>
Options: -l, -w, -c <br>

-	pwd : present working directory <br>
Syntax: pwd <br>

-	cd : change directory <br>
Syntax: cd ..   Go to parent directory <br>
	cd../..  2 level up grandparent directory <br>
	cd../home  Go to Home directory <br>

-	chmod: change the permission of files <br>
Syntax: chmod [user group other] filename <br>
Options: (Give permission using octal numbers or using parameters) <br>
	Octal numbers  3,4,5,6,7 <br>
	Parameters  u, g, o <br>
	r= read permission <br>
w=write permission <br>
x=execute permission <br>

-	head : display top N lines in a file <br>
Syntax: head -N filename <br>
	N  1,2,3,… <br>
	
	tail : display bottom N lines or from Nth line in file <br>
	Syntax : tail -N filename  print bottom N lines <br>
		  tail +N filename  print all lines from Nth line <br>

-	mailx : to mail other users <br>
Options : -s , -a <br>
Syntax: mailx -s “ SUBJECT” -a “ATTACHMENT FILE”  mail_id < filename    body of mail is in file  <br>
	Echo “ BODY of mail “ | mailx -s “ SUBJECT” -a “ATTACHMENT FILE”  mail_id  body of mail using echo command. <br>

-	History : to get history of previous commands <br>
Syntax: history N <br>
Options: N  1,2,3,4… <br>




Introduction to sed commands in unix <br>

Sed  STREAM EDITOR <br>

Used to edit anything in file without opening that file, print something from file and <br>
to find & replace something in file. <br>


Syntax: sed options “ address action ” filename <br>


NOTE: whenever we need to print anything using sed we will use -n option always and action as p <br>


Options: -n  while printing <br>
	  -e  while giving different range of lines to print <br>
	  -i  replace anything in original file <br>


>> To remove case sensitivity  will use -i along with context addressing in sed <br>
Example:  Sed ‘s/Director/HR/i’ emp.txt <br>


>> To find and replace in original file will use -i as option <br>
Example: Sed –i ‘s/director/HR/g’ emp.txt <br>


>> To take backup of file before making any changes to original file using sed command <br>
Example: Sed –i.back ‘s/director/HR/g’ emp.txt <br>











Introduction to grep commands in unix <br>

GREP  GLOBAL REGULAR EXPRESSION PRINT <br>

Grep is a useful command to search for matching patterns in a file. <br>

Usecase: If you are a system admin who needs to scrape through log files or a developer trying to find certain occurrences in the code file, then GREP is a powerful command to use. <br>

Syntax:  grep [OPTION...] PATTERNS [FILE...] <br>


Options: -w  to search for word <br>
	   -i  to remove case sensitivity <br>
	   -n  want to print line number wherever pattern/word matches <br>
	   -v  to print everything except given pattern <br>
	   -r  recursive option prints all directories/ Subdirectories wherever that pattern matches <br>


>> search with regular expression characters ^ and $ <br>
^  it search the beginning of the line <br>
$  it search the end of the line <br>
.*  it search for any character <br>

Example: grep -iv "^employee_number.*salary$" employee.txt>only_data.txt <br>
             			




Introduction to awk commands in unix <br>

Used when we want to manipulate the column specific data then we will use AWK command. <br>

Syntax:  awk option ‘selection_criteria {action}’  filename <br>

NOTE : while using awk command we will always use -F option for describing file delimiter ‘ | ‘. <br>
( <br>
Selection criteria : <br>
NR  Line number,  <br>
NF  No. of Fields, <br>
OFS  Output Field Separator <br>
) <br>

Use case1: print 2nd,3rd,6th column only in file <br>
Example: awk –F “|”  ‘{print $2,$3,$6}’ employee.txt  <br>

Use case2 : print column specific data from line 3 to line 10 only  <br>
>>   awk –F “|”  ‘NR==3, NR==10{print $2,$3,$6}’ employee.txt <br>

Use case3: want to print only those records who are having 8 columns <br>
>> awk –F “|” ‘NF ==8{print}’ employee.txt > goodfile <br>
(If you only give print it will give you all the columns) <br>

Use case4: pattern matching in column specific <br>
>>  awk –F “|” ‘$3~/HR/{print}’ employee.txt <br>

Use case5: want to change delimiter in output file <br>
>> awk –F “|” ‘{OFS =“,”} {print $1,$2,$3,$4,$5}’  emp.txt <br>








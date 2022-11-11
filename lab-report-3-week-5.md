# find 
The find command has many different options. I will start by exploring the `-type` option.

## `-type`
### Example 1:
```
Rajs-MacBook-Pro-2:docsearch rajnawal$ find technical  -type d
technical
technical/government
technical/government/About_LSC
technical/government/Env_Prot_Agen
technical/government/Alcohol_Problems
technical/government/Gen_Account_Office
technical/government/Post_Rate_Comm
technical/government/Media
technical/plos
technical/biomed
technical/911report
```
The d after `-type` tells `find` to return all the directories present in the techincal folder. It is useful because it lets you find a specific type of file.

### Example 2:
```
Rajs-MacBook-Pro-2:docsearch rajnawal$ find technical -type d -empty 
```
This command looks for all empty directories; it behaves this way because  `-type` was used in conjunction with `-empty`. This command is useful because you might want to find empty directories or files.

### Example 3:
```
Rajs-MacBook-Pro-2:docsearch rajnawal$ find technical/911report -type f
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-13.1.txt
technical/911report/chapter-13.2.txt
technical/911report/chapter-13.3.txt
technical/911report/chapter-3.txt
technical/911report/chapter-2.txt
technical/911report/chapter-1.txt
technical/911report/chapter-5.txt
technical/911report/chapter-6.txt
technical/911report/chapter-7.txt
technical/911report/chapter-9.txt
technical/911report/chapter-8.txt
technical/911report/preface.txt
technical/911report/chapter-12.txt
technical/911report/chapter-10.txt
technical/911report/chapter-11.txt
```
This command prints out all of the files in the specified directory(it does not print the directory paths out). This is useful because there might be times when you only want the paths of files and not any subdirectories.

## `-atime`
### Example 1:
```
Rajs-MacBook-Pro-2:docsearch rajnawal$ find technical -atime 0
technical/plos/journal.pbio.0020001.txt
```
This command finds all files in the specified directory that were accessed in the last day. This is useful if you are trying to find out which files you accessed recently. 

### Example 2:
```
Rajs-MacBook-Pro-2:docsearch rajnawal$ find technical/government/Alcohol_Problems ! -atime 0
technical/government/Alcohol_Problems
technical/government/Alcohol_Problems/DraftRecom-PDF.txt
technical/government/Alcohol_Problems/Session4-PDF.txt
```
This finds all the files in the specified directory that have not been accesed in the past day. This is useful when you want to create a reading list of sorts to determine which files you still have to go through.

### Example 3:
```
Rajs-MacBook-Pro-2:docsearch rajnawal$ find technical/government/Alcohol_Problems ! -atime 0 -type f
technical/government/Alcohol_Problems/DraftRecom-PDF.txt
technical/government/Alcohol_Problems/Session4-PDF.txt
```
This returns all of the paths to files(excludes subdirectories) that have not been accessed in the last day. This is useful when you do not want to see paths to subdirectories in your list of results.

## `-size`
### Example 1:
```
Rajs-MacBook-Pro-2:docsearch rajnawal$ find technical -size 1
technical
technical/government
technical/government/Env_Prot_Agen
technical/government/Alcohol_Problems
technical/government/Post_Rate_Comm
```
This returns the list of paths whose rounded up size is 512 byte; the number after size tells the command what size of a 512 byte block it should round upto, that is 2 would tell it to round up to 1024 bytes. This command is useful if you want to look for files or folders of a certain size.

### Example 2:
```
Rajs-MacBook-Pro-2:docsearch rajnawal$ find technical -size +200k -type f
technical/government/About_LSC/commission_report.txt
technical/government/Env_Prot_Agen/bill.txt
technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
technical/government/Gen_Account_Office/d01591sp.txt
technical/911report/chapter-13.4.txt
technical/911report/chapter-13.5.txt
technical/911report/chapter-3.txt
```
This command is looking for all files whose size is over 200kb. This is useful if you want to look for files that are over a certain size.

### Example 3:
```
Rajs-MacBook-Pro-2:docsearch rajnawal$ find technical -size +100k -mindepth 3
technical/government/About_LSC/commission_report.txt
technical/government/About_LSC/State_Planning_Report.txt
technical/government/Env_Prot_Agen/multi102902.txt
technical/government/Env_Prot_Agen/ctm4-10.txt
technical/government/Env_Prot_Agen/bill.txt
technical/government/Env_Prot_Agen/tech_adden.txt
technical/government/Gen_Account_Office/d0269g.txt
technical/government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
technical/government/Gen_Account_Office/Sept27-2002_d02966.txt
technical/government/Gen_Account_Office/d01376g.txt
technical/government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
technical/government/Gen_Account_Office/pe1019.txt
technical/government/Gen_Account_Office/gg96118.txt
technical/government/Gen_Account_Office/d01591sp.txt
technical/government/Gen_Account_Office/im814.txt
technical/government/Gen_Account_Office/ai9868.txt
technical/government/Gen_Account_Office/May1998_ai98068.txt
technical/government/Gen_Account_Office/d02701.txt
```
This command looked for all files that were over 100k and 2 folder deeper than the current one. This is useful when you want to ignore files at a certain depth while looking for files over a certain size.
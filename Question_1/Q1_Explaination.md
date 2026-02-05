Answer 1 Explanation

The shell script in the analyze.sh file has been written and executed in my Kali Linux VM to check if it was working. You can find a detailed explanation for every command executed to check whether each of the shell script blocks is working. 
![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/40dfcfec1b1b3d22803fffca6f57f5c0cbf2569b/Question_1/Screenshot%202026-02-05%20220758.png)

The first thing I did after creating the analyze.sh file with the complete script in it is go to the Kali command line and changed the directory to Desktop (cd Desktop), where the file was saved.

I then used the command chmod +x analyze.sh to permit my current user to execute the shell script.

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/9dc9e9581dcc0547544a16914dd8d0678dcc276e/Question_1/Screenshot%202026-02-05%20220429.png)


The first block of the shell script is to check for exactly one argument:


<code>if [ $# -ne 1 ]; then
echo "Error: Please provide exactly one argument."
exit 1
fi</code>


I used the command ./analyze.sh bandit ~/Downloads to analyze a file named "bandit" and a directory name "Downloads". The script is instructed to show an error message if there's more than one argument, and it does its job. Since there's two arguments given in the command, it shows the error message.

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/7f4abae26d8bacd7a23bfa3ce95aa3eec6b3b6c4/Question_1/Screenshot%202026-02-05%20221613.png)
On the above image, you can see that I also used the command ./analyze.sh Downloads to test the second part of the script to check if the path exists:


<code>if [ ! -e "$1" ]; then
echo "Error: Path does not exist."
exit 1
fi</code>


Since I'm in the Desktop directory and there's no direct pathway to Downloads from there unless I include the complete pathway ~/Downloads, it shows an error, just as the script instructs it to, because the path Downloads doesn't exist in the Desktop directory.

The third part of the script checks if it's a file.


<code>if [ -f "$1" ]; then
echo "File Analysis:"
echo "Lines: $(wc -l < "$1")"
echo "Words: $(wc -w < "$1")"
echo "Characters: $(wc -c < "$1")"</code>


I used the command ./analyze.sh bandit to analyze the file name bandit. The result I got is given in the screenshot below:
![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/ea3debd655b1340329c158b72637dd1c6120d6e4/Question_1/Screenshot%202026-02-05%20221857.png)

If it was not a file, it will move on to the final part that checks if it's a directory


<code>elif [ -d "$1" ]; then
echo "Directory Analysis:"
echo "Total files: $(ls -l "$1" | grep "^-" | wc -l)"
echo ".txt files: $(ls "$1"/*.txt 2>/dev/null | wc -l)"</code>


I used the command ./analyze.sh ~/Downloads to analyze the Downloads directory. The first image shows my Download directory results with no .txt files, and the second image shows the result after I added a txt file. 

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/f084c982653a81715b285843a6d9e1c6bd248a17/Question_1/Screenshot%202026-02-05%20222452.png)

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/a137ab946792967f15aee9f1e86efc4b1b37de01/Question_1/Screenshot%202026-02-05%20222718.png)


For additional checks, I have also analyzed an empty file and an empty directory: Screenshot (759)









The Question 2 folder contains both the shell script file "loganalysis.sh" and the example log file I created to use for demonstration, named "systemlog.log".
The first part of the shell script is to check if the number of arguments is more than one. The command should only accept one argument file, and hence the shell script block checks if the argument is not equal to one; if that's true, it will show an error message.

<code>if [ $# -ne 1 ]
then
echo "Error: Please provide exactly one log file."
exit 1
fi</code>

The next block of script is to check whether the file exists and is readable:

<code>if [ ! -r "$1" ]
then
echo "Error: File does not exist or is not readable."
exit 1
fi</code>

The third block counts the number of log entries that mention INFO, WARNING, and ERROR:

<code>total=$(wc -l < "$1")
info=$(grep " INFO " "$1" | wc -l)
warning=$(grep " WARNING " "$1" | wc -l)
error=$(grep " ERROR " "$1" | wc -l)</code>

The fourth block is used to find the last ERROR message shown:

<code>last_error=$(grep " ERROR " "$1" | tail -1)</code>

"tail -1" is used to find the most recent one, the most ERROR message in this context.

The fifth block is to create the report file:

<code>date=$(date +%Y-%m-%d)
report="logsummary_$date.txt"</code>

The sixth block is to write all of the required data into the report file:

<code>echo "Log Summary Report - $date" > "$report"
echo "Total entries: $total" >> "$report"
echo "INFO messages: $info" >> "$report"
echo "WARNING messages: $warning" >> "$report"
echo "ERROR messages: $error" >> "$report"
echo "Most recent ERROR:" >> "$report"
echo "$last_error" >> "$report"</code>

The command echo is used to print the info, ">" used to create the file with the first line printed, and ">>" adds to the file. Using ">" after creating the file will overwrite any data that's already in it.

And then the final line of script is to show the report that was created:

<code>cat "$report"</code>

Once this shell script was created in my Kali Linux, I saved it in my Kali Desktop, changed directory to Desktop, and used the command "chmod +x loganalysis.sh" to give my current user account permission to execute the file.

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/3e6382a271af7e928cec0e4fc6bf5605172ccc07/Question_2/images/Screenshot%202026-02-05%20223830.png)





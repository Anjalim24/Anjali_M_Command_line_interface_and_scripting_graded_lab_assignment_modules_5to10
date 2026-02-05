Answer 6 Explanation
Question 6 folder contains the shell script "metrics.sh" and the text file "input.txt" I created to demonstrate this assignment question.
The shell script command explanation
1 <code>words=$(tr -cs 'a-zA-Z' '\n' < input.txt)</code>
Converts text into one word per line and stores it in the variable words

2 <code>echo "Longest word:"
echo "$words" | awk '{ print length, $0 }' | sort -nr | head -1 | cut -d" " -f2</code>

Prints the lenght of each word, then sorts it in reverse order (largest to smallest), takes the longest, removes the lenght and only shows the word.

3 <code>echo "Shortest word:"
echo "$words" | awk '{ print length, $0 }' | sort -n | head -1 | cut -d" " -f2</code>

Pretty much the same as the longest word, except this time there's no -r, hence the smallest comes first, and displays the smallest word.

4 <code>echo "Average word length:"
echo "$words" | awk '{ sum += length; count++ } END { print sum/count }'</code>

<code>sum += length</code> adds all the characters and gives the total number of characters, <code>count++</code> counts the number of words, END after processing all lines and then calculate the average <code>sum/count</code>

5 <code>echo "Total unique words:"
echo "$words" | sort | uniq | wc -l</code>

sort groups the duplicates, uniq removes the duplicates, and wc -l counts the remaining lines.

In summary, the script converts text into one word per line using tr, analyzes word lengths using awk, and counts unique words using sort, uniq, and wc.

Execution steps and demostration
I first wrote the shell script:

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/2a034b3094942d61ce6ebd51923d364627df35f7/Question_6/images6/Screenshot%202026-02-05%20231316.png)

Then I created the input.txt file: 

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/32f4694ed1203f9dc9a22455d7940cf3dbacd411/Question_6/images6/Screenshot%202026-02-05%20231510.png)

And finally, used the command chmod to give permission to execute the shell script and executed it using ./metrics.sh input.txt 

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/e4928a4511c6c53e0ed306acc51f043ad197c750/Question_6/images6/Screenshot%202026-02-05%20231624.png)


The output gave the longest word, the shortest word, average word length, and total unique words. The shell script worked!




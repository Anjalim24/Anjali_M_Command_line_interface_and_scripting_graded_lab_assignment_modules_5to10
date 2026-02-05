Answer 6 Explanation
Question 6 folder contains the shell script "metrics.sh" and the text file "input.txt" I created to demonstrate this assignment question.
The shell script command explanation
1 words=$(tr -cs 'a-zA-Z' '\n' < input.txt)
Converts text into one word per line and stores it in the variable words

2 echo "Longest word:"
echo "$words" | awk '{ print length, $0 }' | sort -nr | head -1 | cut -d" " -f2

Prints the lenght of each word, then sorts it in reverse order (largest to smallest), takes the longest, removes the lenght and only shows the word.

3 echo "Shortest word:"
echo "$words" | awk '{ print length, $0 }' | sort -n | head -1 | cut -d" " -f2

Pretty much the same as the longest word, except this time there's no -r, hence the smallest comes first, and displays the smallest word.

4 echo "Average word length:"
echo "$words" | awk '{ sum += length; count++ } END { print sum/count }'

sum += lenght adds all the characters and gives the total number of characters, count++ counts the number of words, END after processing all lines and then calculate the average sum/count

5 echo "Total unique words:"
echo "$words" | sort | uniq | wc -l

sort groups the duplicates, uniq removes the duplicates, and wc -l counts the remaining lines.

In summary, the script converts text into one word per line using tr, analyzes word lengths using awk, and counts unique words using sort, uniq, and wc.

Execution steps and demostration
I first wrote the shell script:

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/2a034b3094942d61ce6ebd51923d364627df35f7/Question_6/images6/Screenshot%202026-02-05%20231316.png)

Then I created the input.txt file: Screenshot (775)

And finally, used the command chmod to give permission to execute the shell script and executed it using ./metrics.sh input.txt Screenshot (774)


The output gave the longest word, the shortest word, average word length, and total unique words. The shell script worked!

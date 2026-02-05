Answer 7 Explanation
Question 7 folder contains the shell script "patterns.sh" and the text file "lyrics.txt" I created to demonstrate this assignment question. I've also copied and pasted the mixed.txt file that was created after I executed the shell script, since it was too long to capture on screenshot.
The shell script command explanation
1 words=$(tr -cs 'a-zA-Z' '\n' < "$1" | tr 'A-Z' 'a-z')
It splits text into one word per line and translates all the capital letters into small letters.

2 echo "$words" | grep -E '^[aeiou]+$' > vowels.txt

Finds words containing only vowels and stores it into vowels.txt

3 echo "$words" | grep -E '^[^aeiou]+$' > consonants.txt

Finds words that do not contain vowels, and stores it into consonants.txt

[^aeiou] means anything except vowels, which means it includes only consonants.

4 echo "$words" | grep -E '^[^aeiou][a-z][aeiou][a-z]$' > mixed.txt

This line of script ensures the first letter is a consonant and there's at least one vowel.

Execution steps and demonstration
I first wrote the shell script and then I created the lyrics.txt file for demosntrating the shell script.

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/794eee92bb481602538873479dc099566fb971a7/Question_7/images7/Screenshot%202026-02-05%20232602.png)

I then used the command chmod and gave permission to run the script. After running the script, all three of the text files get created. Screenshot (782)

Answer 4 Explanation
The Question 4 folder contains both the shell script file "emailcleaner.sh" and the example text file I created to use for demonstration, named "emails.txt".
<code>#!/bin/bash</code> -> Tells the system to run the script using bash.

<code>grep -E '^[a-zA-Z0-9]+@[a-zA-Z]+.com$' emails.txt > valid.txt</code> -> Extract VALID emails

<code>^</code> -> start of line

<code>[a-zA-Z0-9]+</code> -> one or more letters or digits

<code>[a-zA-Z]+</code> -> one or more letters in domain name

<code>$</code> -> end of line

-E enables extended regex and lets us use <code>+</code> without escaping, and <code></code> valid.txt</code> stores matched lines into valid.txt file.

To extract the INVALID emails:

<code>grep -Ev '^[a-zA-Z0-9]+@[a-zA-Z]+.com$' emails.txt > invalid.txt</code>

<code>-v</code> is used to invert match, as in give me lines that do not match a specific pattern. Hence, the code finds all the emails that cannot be categorised as valid and stores them into the invalid.txt file.

In order to remove duplicates from valid.txt:

<code>sort valid.txt | uniq > temp.txt</code>

Here, we used "sort" first because "uniq" only removes adjacent duplicates. So we first get all the same emails adjacent to each other and then use uniq to remove them, and store them into temp.txt.

To replace the original file with the final correct valid file:

<code>mv temp.txt valid.txt</code>

This is because we can't directly overwrite <code>valid.txt</code> while reading it.

This is the text file created with all the valid, invalid, and duplicate emails in them.

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/cebf796c2a543cb4e85039be1cea2f0c0ffc8e35/Question_4/images4/Screenshot%202026-02-05%20230012.png)

Once I run the script after using the chmod command, and then using the ./emailcleaner.sh emails.txt command, I get valid.txt and invalid.txt automatically created in my system, with the proper email classification.


![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/4069a4e703dd50c20efe2281051679001f1f1c33/Question_4/images4/Screenshot%202026-02-05%20230235.png)



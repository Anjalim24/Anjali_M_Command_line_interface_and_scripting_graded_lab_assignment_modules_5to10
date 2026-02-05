Answer 4 Explanation
The Question 4 folder contains both the shell script file "emailcleaner.sh" and the example text file I created to use for demonstration, named "emails.txt".
#!/bin/bash -> Tells the system to run the script using bash.

grep -E '^[a-zA-Z0-9]+@[a-zA-Z]+.com$' emails.txt > valid.txt -> Extract VALID emails

^ -> start of line

[a-zA-Z0-9]+ -> one or more letters or digits

[a-zA-Z]+ -> one or more letters in domain name

$ -> end of line

-E enables extended regex and lets us use + without escaping, and > valid.txt stores matched lines into valid.txt file.

To extract the INVALID emails:

grep -Ev '^[a-zA-Z0-9]+@[a-zA-Z]+.com$' emails.txt > invalid.txt

-v is used to invert match, as in give me lines that do not match a specific pattern. Hence, the code finds all the emails that cannot be categorised as valid and stores them into the invalid.txt file.

In order to remove duplicates from valid.txt:

sort valid.txt | uniq > temp.txt

Here, we used "sort" first because "uniq" only removes adjacent duplicates. So we first get all the same emails adjacent to each other and then use uniq to remove them, and store them into temp.txt.

To replace the original file with the final correct valid file:

mv temp.txt valid.txt

This is because we can't directly overwrite valid.txt while reading it.

This is the text file created with all the valid, invalid, and duplicate emails in them.

Screenshot (766)
Once I run the script after using the chmod command, and then using the ./emailcleaner.sh emails.txt command, I get valid.txt and invalid.txt automatically created in my system, with the proper email classification.

Screenshot (765)
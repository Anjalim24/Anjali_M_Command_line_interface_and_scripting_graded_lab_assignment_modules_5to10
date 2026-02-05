Answer 3 Explanation
The Question 3 folder contains both the shell script file "validate_results.sh" and the example text file I created to use for demonstration, named "marks.txt".
The below code reads one line at a time from marks.txt:

while read roll name m1 m2 m3

fail=0-> It tracks how many subjects the student failed.

In the code below, -lt means less than, checking if the mark is less than 33, which would then mean failed, and hence the fail coutner increases.

if [ $m1 -lt 33 ]; then
fail=$((fail + 1))
fi
if [ $m2 -lt 33 ]; then
fail=$((fail + 1))
fi
if [ $m3 -lt 33 ]; then
fail=$((fail + 1))
fi

In the code below, if the fail counter equals one, then the roll number and name of the student will be printed, and the fail_one counter goes up by 1. In the case when the fail counter is zero, then the student has passed all subjects and their roll number and name will be printed, and 1 will be added to the pass_all counter.

 if [ $fail -eq 1 ]; then
echo "Failed in one subject: $roll $name"
fail_one=$((fail_one + 1))
fi
if [ $fail -eq 0 ]; then
echo "Passed all subjects: $roll $name"
pass_all=$((pass_all + 1))
fi

The below line of code feeds the marks.txt into the while loop line by line:

done < marks.txt

The final two lines gives the total number of students who failed one subject and the total number of students who passed all subjects:

echo "Count failed in exactly one subject: $fail_one"
echo "Count passed in all subjects: $pass_all"

The output I acquired when I ran the following commands:

chmod +x validate_results.sh

./validate_results.sh marks.txt


![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/f5df28f59162ae72d54ebd4cb7aa0971c2a44381/Question_3/images_3/Screenshot%202026-02-05%20225049.png)

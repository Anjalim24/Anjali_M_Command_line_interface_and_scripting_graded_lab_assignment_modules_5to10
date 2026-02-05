Answer 8 Explanation
Question 8 folder contains the shell script "bg_move.sh". I reused the dirB directory I created for Question 5 to demonstrate this question's shell script.
The shell script command explanation
1 dir=$1 means that the first argument is stored as the function dir.
2 backup="$dir/backup"
mkdir -p "$backup"

Creates the backup directory as a subdirectory of the directory given as the argument. -p ensures there's no error if backup already exists.

3 for file in "$dir"/*
do
mv "$file" "$backup" &
echo "Moved $file | PID: $!"
done

All the files inside the directory are moved to the backup directory, and the "&" symbol makes the commands run in the background.

"$!" gives the PID of the most recent background process.

4 wait
echo "All background processes completed."

Pauses the script execution and waits until all background processes finish. If we do not use wait, script may exit before moves complete. Finally, it displays the completion message after all processes are done.

In summary, the script moves files concurrently using background processes, tracks their PIDs using $!, and synchronizes completion using wait.

Execution steps and demonstration
Used "chmod +x" to give execution permission, and executed the shell script.

![image alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/3b33f0cdfedd08cc92d6581e16cb15ecfd49389f/Question_8/images8/Screenshot%202026-02-05%20233640.png)

I used the dirB directory I created for Question 5 for demonstration here. After I executed the shell script and checked the directory, the backup sub-directory was created and the files had been moved into it.

![images alt](https://github.com/Anjalim24/Anjali_M_Command_line_interface_and_scripting_graded_lab_assignment_modules_5to10/blob/ffd9ef0d4640e19ffc5013a0c6aa9fac6771939f/Question_8/images8/Screenshot%202026-02-05%20233655.png)

The shell script worked!


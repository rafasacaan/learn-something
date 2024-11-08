# Bash
Based on https://www.freecodecamp.org/news/bash-scripting-tutorial-linux-shell-script-and-command-line-for-beginners/

## The basics
Generally, commands follow this syntax:

```bash
command [OPTIONS] arguments
```
The shebang (#!) is an absolute path to the bash interpreter. It telss the shell to execute via bash shell.

```bash
#!/bin/bash
```
You can find your bash shell by typing

```bash
which bash
```

## Scripting
Let´s see this example.

```bash
#!/bin/bash
echo "Today is " `date`

echo -e "\nenter the path to directory"
read the_path

echo -e "\n you path has the following files and folders: "
ls $the_path
```

What the script does is the following:
1. Print the date
2. Ask the user to enter (-e) a path
3. Read the path and store it in the `the_path` variable
4. Executes the ls command for the path in the variable

Now, we need to **make the script executable**.

```bash
chmod u+x example.sh
```

We are ready to run the command by:

```bash
sh example.sh
```

### Comments

You can create comments like this:
```bash
# This is an example comment
# Both of these lines will be ignored by the interpreter
```

### Variables
You can directly assign a value to variable or based on the output obtained:

```bash
country=Chile
new_country=$country
```

### Reading user input
```bash
#!/bin/bash 
echo "What's your name?" 
read entered_name 
echo -e "\nWelcome to bash tutorial" $entered_name
```

### Reading from a file
Read each line of `input.txt`

```bash
while read line
do
  echo $line
done < input.txt
```

### Access arguments given
You can acces the first and second arguments with `$1` and `$2`.
```bash
echo "Hello, $1!"
```

And call it as 
> sh example.sh Rafa

### Writing to a file

```bash
echo "More text." > output.txt
```

### Appending to a file
Append line to the end fo the file.
```bash
echo "More text." >> output.txt
```

### Some bash commands
`cd`, `ls`, `mkdir`, `touch`, `rm`, `cp`, `mv`, `echo`, `cat`, `grep`, `chmod`, `sudo`, `df`, `history`, `ps`.

### Conditional statements (if/else)
 ```bash

if [[ condition ]];
then
    statement
elif [[ condition ]]; then
    statement 
else
    do this by default
fi
```

### Logical statements
We can use `-a` for AND operator, and `-o` for OR. 
Also, we can use `-gt` for greater than, `lt` for less than, and `-eq` for equals.

```bash
if [ $a -gt 60 -a $b -lt 100 ]
```

### While loop
A while loop looks like this. Print numbers from 1 to 10.
```bash
#!/bin/bash
i=1
while [[ $i -le 10 ]] ; do
   echo "$i"
  (( i += 1 ))
done
```

### For loop
Print numbers from 1 to 5.
```bash
#!/bin/bash

for i in {1..5}
do
    echo $i
done
```

### Case statements

```bash
case expression in
    pattern1)
        # code to execute if expression matches pattern1
        ;;
    pattern2)
        # code to execute if expression matches pattern2
        ;;
    pattern3)
        # code to execute if expression matches pattern3
        ;;
    *)
        # code to execute if none of the above patterns match expression
        ;;
esac
```

For example, 
```bash
fruit="apple"

case $fruit in
    "apple")
        echo "This is a red fruit."
        ;;
    "banana")
        echo "This is a yellow fruit."
        ;;
    "orange")
        echo "This is an orange fruit."
        ;;
    *)
        echo "Unknown fruit."
        ;;
esac
```

### Schedule scripts

Using `cron`.
```bash
# Cron job example
* * * * * sh /path/to/script.sh
```

Here, the asterisc (*) represents **minute/hour/day/month/weekday**. Some examples are:

Run a script at midnight every day.
> 0 0 /path/to/script.sh 

Run a script every 5 minutes.
> /5 /path/to/script.sh

Run a script at 6am from monday to friday.
> 0 6 1-5 /path/to/script.sh

Run a script on the first 7 days of every month
> 0 0 1-7 /path/to/script.sh

Run a script on the first day of every month at noon
> 0 12 1 /path/to/script.sh

### Using crontab
Useful to add and edit cron jobs.

You can list the jobs scheduled:
> crontab -l

You can eddit and add the cron through:
> crontab -e

### Debugging
For later.


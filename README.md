# 🐚 Bash for Developers: A Comprehensive Course

## ℹ️ Course Overview

🎙️ **Audience:** Developers new to the shell

🎯 **Goal:** Understand core shell concepts, confidently use Bash to automate and manipulate files and processes

📝 **Format:** 15 sections, each with interactive exercises

⏰ **Estimated Duration:** 4–6 hours total

🌎 **Environment:** Use the terminal on Linux and macOS, or WSL on Windows

## 🔹 Section 1: Introduction to the Shell

**What You'll Learn:**

- What a shell is
- Bash vs. other shells
- Why developers use the terminal

**Key Concepts:**

- CLI vs GUI
- Shells as command interpreters
- Shell versions: sh, bash, zsh, etc.

A shell is a command-line interface (CLI) that lets you interact with your computer by typing commands instead of using a graphical user interface (GUI). It's a text-based interface between you and the operating system. Bash (short for Bourne Again SHell) is one of the most commonly used shells in Unix-like systems. Others include Zsh, Fish, and Tcsh.

The terminal gives developers a powerful way to automate tasks, manipulate files, manage system processes, and much more. It's often faster and more flexible than graphical tools, especially for repetitive tasks or remote work.

**Exercise:**

```sh
echo $SHELL
which bash
```

## 🔹 Section 2: Running Commands

**What You'll Learn:**

- How to run and structure commands
- Understanding command syntax

**Key Concepts:**

- Command, options, and arguments
- man pages for help

Shell commands usually follow this structure:

```sh
command [options] [arguments]
```

For example:

```sh
ls -l /tmp
```

Here, `ls` is the command, `-l` is an option to show a detailed list, and `/tmp` is the argument (the target directory).

Use the `man` command to read the manual for any command:

```sh
man ls
```

Type `q` to quit the manual.

**Exercise:**

```sh
ls -l /tmp
man ls
```

## 🔹 Section 3: File Navigation

**What You'll Learn:**

- How to move through the filesystem using the terminal

**Key Commands:**

- pwd, cd, ls, tree

You can navigate your file system using:

- `pwd` – prints the current directory
- `cd` – changes directory
- `ls` – lists files and directories

**Examples:**

```sh
pwd
cd /etc
ls -l
```

**Exercise:**

```sh
pwd
cd /
ls -lh
```

## 🔹 Section 4: Working with Files and Directories

**What You'll Learn:**

- Creating, moving, copying, and deleting files

**Key Commands:**

- touch, mkdir, cp, mv, rm, rmdir

You can perform file operations using:

- `touch file.txt` – creates an empty file
- `mkdir new_dir` – makes a directory
- `cp file.txt file2.txt` – copies a file
- `mv file2.txt archive.txt` – renames or moves a file
- `rm file.txt` – deletes a file
- `rmdir dir_name` – deletes an empty directory

Be careful with `rm` – it deletes permanently.

**Exercise:**

```sh
mkdir workshop
cd workshop
touch file1.txt
cp file1.txt file2.txt
mv file2.txt archive.txt
rm archive.txt
```

## 🔹 Section 5: stdin, stdout, stderr

**What You'll Learn:**

- How commands handle input and output

**Concepts:**

- stdin, stdout, stderr
- File descriptor numbers: 0, 1, 2

Bash uses three standard streams:

- `stdin` (0) – standard input, usually from keyboard
- `stdout` (1) – standard output, usually to terminal
- `stderr` (2) – standard error output

You can redirect these streams:

```sh
echo "Hello" > out.txt      # stdout to file
ls nonexist 2> err.txt      # stderr to file
cat < out.txt               # stdin from file
```

**Exercise:**

```sh
echo "Hello" > hello.txt
cat < hello.txt
ls nofile 2> error.log
```

## 🔹 Section 6: Redirects and Pipes

**What You'll Learn:**

- Redirection and chaining output between commands

**Concepts:**

- `>`, >>, <, 2>, |

Use redirection operators to control where input and output go:

- `>` – redirect stdout to file (overwrite)
- `>>` – redirect stdout to file (append)
- `<` – read stdin from file
- `2>` – redirect stderr

Use pipes (`|`) to pass stdout from one command to another:

```sh
cat file.txt | grep "error" | wc -l
```

**Exercise:**

```sh
echo "line1" > file.txt
echo "line2" >> file.txt
cat file.txt | wc -l
```

## 🔹 Section 7: Exit Codes and Control Operators

**What You'll Learn:**

- How Bash signals success or failure

**Concepts:**

- $?, &&, ||

Every command returns an exit code:

- `0` means success
- Any other value means failure

Check the last exit code:

```sh
echo $?
```

Control operators:

- `&&` – run next command only if previous succeeded
- `||` – run next only if previous failed

```sh
mkdir test && cd test
false || echo "Command failed"
```

**Exercise:**

```sh
false
echo $?
true && echo "Success"
false || echo "Failed, but continuing"
```

## 🔹 Section 8: Variables and Quoting

**What You'll Learn:**

- Creating and using variables
- Quoting rules

**Concepts:**

- name=value, $name
- "double quotes" vs 'single quotes'

Create variables with no spaces:

```sh
name="world"
echo "Hello, $name!"
```

Quoting:

- Double quotes (`"`) allow variable expansion
- Single quotes (`'`) treat everything literally

```sh
echo "$name"    # expands
echo '$name'    # literal
```

**Exercise:**

```sh
name="world"
echo "Hello, $name!"
echo 'Hello, $name!'
```

## 🔹 Section 9: Command Substitution

**What You'll Learn:**

- Using output of one command in another

**Concepts:**

- $(command), legacy \`command\`

Command substitution lets you assign output of a command to a variable:

```sh
now=$(date)
echo "Current time is: $now"
```

The older syntax is:

```sh
now=`date`
```

But `$(...)` is preferred.

**Exercise:**

```sh
now=$(date)
echo "Current time is: $now"
```

## 🔹 Section 10: Common Core Utilities

**What You'll Learn:**

- The most-used command-line tools

**Commands:**

- cat, head, tail, grep, cut, sort, uniq, xargs, wc, find

Useful core utilities:

- `cat`,`head`, `tail` – view file content
- `grep` – search for text
- `cut`, `awk`, `sed` – extract/transform text
- `sort`, `uniq` – organize lines
- `xargs` – build and execute commands
- `find` – search for files

**Examples:**

```sh
grep "ERROR" logfile.txt
find . -name "*.log" | xargs rm
```

**Exercise:**

```sh
echo -e "one\ntwo\nthree\none" > list.txt
cat list.txt | sort | uniq -c
find . -name "*.txt"
```

## 🔹 Section 11: Globs and Wildcards

**What You'll Learn:**

- Pattern matching in filenames

**Concepts:**

- *, ?, [abc], {a,b}

Use wildcards to match files:

- `*` – matches any characters
- `?` – matches a single character
- `[abc]` – matches a, b, or c
- `{a,b}` – matches a or b

**Note:** Wildcards are _not_ regular expressions, although they do have some similarities in syntax.

**Examples:**

```sh
ls *.txt
ls file?.txt
ls {a,b}.log
```

**Exercise:**

```sh
touch a.txt b.txt c.md
ls *.txt
ls ?.txt
```

## 🔹 Section 12: Conditionals

**What You'll Learn:**

- Using if, else, elif statements

**Concepts:**

- test or [ ... ] syntax
- -f, -d, -n, -z, etc.

Test conditions with `[` or `[[`:

```sh
if [ -f file.txt ]; then
  echo "File exists"
else
  echo "No file"
fi
```

Common test options:

- `-f` – file exists
- `-d` – directory exists
- `-z` – string is empty
- `-n` – string is not empty

**Exercise:**

```sh
if [ -f list.txt ]; then echo "File exists"; else echo "No file"; fi
```

## 🔹 Section 13: Loops

**What You'll Learn:**

- Looping through files or command results

**Concepts:**

- for, while, until

`for` loop example:

```sh
for file in *.txt; do
  echo "Found: $file"
done
```

while loop example:

```sh
count=0
while [ $count -lt 5 ]; do
  echo $count
  count=$((count + 1))
done
```

**Exercise:**

```sh
for file in *.txt; do echo "Found: $file"; done
```

## 🔹 Section 14: Writing Bash Scripts

**What You'll Learn:**

- Putting it all together in `.sh` files

**Concepts:**

- Shebang (#!/bin/bash)
- Making scripts executable

Scripts start with a shebang:

```sh
#!/bin/bash
```

Save commands in a file:

```sh
echo -e '#!/bin/bash\necho "This is a script."' > myscript.sh
chmod +x myscript.sh
./myscript.sh
```

Use `$1`, `$2`, etc. for script arguments.

**Exercise:**

```sh
echo -e '#!/bin/bash\necho "This is a script."' > script.sh
chmod +x script.sh
./script.sh
```

## 🔹 Section 15: Putting It All Together

Workshop Mini-Project:

Write a script to:

1.	Search a directory for .log files
2.	Count the lines in each
3.	Output the filename and line count, sorted by count

🛠️ Hint:

Use find, wc -l, sort

<details>
  <summary>Sample solution</summary>
  <pre>
  find . -name "*.log" | while read file; do
    count=$(wc -l < "$file")
    echo "$count $file"
  done | sort -n
  </pre>
</details>


## 🧠 In Context for Cerbo

**Congratulations!** 🎉

Paired with the docker and kubernetes training, you now know enough to be _dangerous_ in the AWS production environment. 😈

> With great power comes great responsibility. 🕸️

```sh
export AWS_PROFILE="us-workloads-prod"
aws sso login
kubectl config use-context <context-arn>
kubectl get namespaces | grep <namespace>
kubectl get pods --namespace="<namespace>"
kubectl exec -it "<pod-name>" --namespace="<namespace>" -- /bin/bash
# Unleash your new-found powers ✨
```

## 📘 Bonus Topics

- Using readline for cursor navigation
- Using environment variables
- Functions in Bash
- trap and signal handling
- Using getopts for argument parsing
- Shellcheck for linting scripts
- Managing processes and background jobs
- Using `~` and `-` directory shorthands
- Using `$@` and `case`

## 🐉 For the Adventurous

- Using vim for editing text files


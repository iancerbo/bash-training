# 🐚 Bash for Developers: A Comprehensive Course

## 🎯 Course Overview

**Audience:** Developers new to the shell

**Goal:** Understand core shell concepts, confidently use Bash to automate and manipulate files and processes

**Format:** 15 sections, each with interactive exercises

**Estimated Duration:** 4–6 hours total

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

What You'll Learn:
- How commands handle input and output

Concepts:
- stdin, stdout, stderr
- File descriptor numbers: 0, 1, 2

Exercise:

```sh
echo "Hello" > hello.txt
cat < hello.txt
ls nofile 2> error.log
```

## 🔹 Section 6: Redirects and Pipes

What You'll Learn:
- Redirection and chaining output between commands

Concepts:
- >, >>, <, 2>, |

Exercise:

```sh
echo "line1" > file.txt
echo "line2" >> file.txt
cat file.txt | wc -l
```

## 🔹 Section 7: Exit Codes and Control Operators

What You'll Learn:
- How Bash signals success or failure

Concepts:
- $?, &&, ||

Exercise:

```sh
false
echo $?
true && echo "Success"
false || echo "Failed, but continuing"
```

## 🔹 Section 8: Variables and Quoting

What You'll Learn:
- Creating and using variables
- Quoting rules

Concepts:
- name=value, $name
- "double quotes" vs 'single quotes'

Exercise:

```sh
name="world"
echo "Hello, $name!"
echo 'Hello, $name!'
```

## 🔹 Section 9: Command Substitution

What You'll Learn:
- Using output of one command in another

Concepts:
- $(command), legacy `command`

Exercise:

```sh
now=$(date)
echo "Current time is: $now"
```

## 🔹 Section 10: Common Core Utilities

What You'll Learn:
- The most-used command-line tools

Commands:
- cat, head, tail, grep, cut, sort, uniq, xargs, wc, find

Exercise:

```sh
echo -e "one\ntwo\nthree\none" > list.txt
cat list.txt | sort | uniq -c
find . -name "*.txt"
```

## 🔹 Section 11: Globs and Wildcards

What You'll Learn:
- Pattern matching in filenames

Concepts:
- *, ?, [abc], {a,b}

Exercise:

```sh
touch a.txt b.txt c.md
ls *.txt
ls ?.txt
```

## 🔹 Section 12: Conditionals

What You'll Learn:
- Using if, else, elif statements

Concepts:
- test or [ ... ] syntax
- -f, -d, -n, -z, etc.

Exercise:

```sh
if [ -f list.txt ]; then echo "File exists"; else echo "No file"; fi
```

## 🔹 Section 13: Loops

What You'll Learn:
- Looping through files or command results

Concepts:
- for, while, until

Exercise:

```sh
for file in *.txt; do echo "Found: $file"; done
```

## 🔹 Section 14: Writing Bash Scripts

What You'll Learn:
- Putting it all together in .sh files

Concepts:
- Shebang (#!/bin/bash)
- Making scripts executable

Exercise:

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

## 🧠 In Context for Cerbo

**Congratulations!** Paired with the docker and kubernetes training, you now know enough to be _dangerous_ in the AWS production environment. 😈

```sh
export AWS_PROFILE="us-workloads-prod"
aws sso login
kubectl config use-context arn:aws:eks:us-east-1:081513380233:cluster/eks-ue1-prod-mdhq
kubectl get namespaces | grep parsleymedicalsf
kubectl get pods --namespace="parsleymedicalsf"
kubectl exec -it "parsleymedicalsf-mdhq-stack-84fc97ffdc-4hfx5" --namespace="parsleymedicalsf" -- /bin/bash
cd /tmp
mkdir workshop-sandbox
cd workshop-sandbox
```

## 📘 Bonus Topics

- Readline
- Functions in Bash
- trap and signal handling
- Using getopts for argument parsing
- Shellcheck for linting scripts

## 🐉 For the Adventurous

- Vim


# Cheatsheet - git

In this case you will be working with files on your local respository

## Navigating between commits using `git checkout`.

This cheat shows you how to create three version of a file and then replenish each version of that file on your file system according to a commit. In this case you're going to move from the 3rd version to the 1st version and then back to the 3rd version.

Before you start, if your environment is not configured with your access credentials, create a set of fictitious user credentials

```
  git config --global user.email "you@example.com"
  git config --global user.name "Your Name"
```

**Step 1:**  Get the source code

`git clone https://github.com/reselbob/sli-000.git`

**Step 2:** Navigate to the source code folder

`cd ./sli-000`

**Step 3:** Add a line of code to the working folder


```
echo "I am line 1." >> cool_text.txt
```
**Step 4:** Add it to `git` Staging (index)

`git add .`


**Step 5:** Commit the file

`git commit -m "added line 1"`


**Step 6:** Add a line of data to the a file

```
echo "I am line 2." >> cool_text.txt
```

**Step 7:** Add it to `git` Staging (index)

`git add .`

**Step 8:** Commit the file

`git commit -m "added line 2"`

**Step 9:** Add another line of data to the a file

```
echo "I am line 3." >> cool_text.txt
```

**Step 10:** Add it to `git` Staging (index)

`git add .`

**Step 11:** Commit the file

`git commit -m "added line 3"`

**Step 12:** Red the contents of the file

`cat cool_text.txt`

You will get the following output:

```
I am line 1.
I am line 2.
I am line 3.
```

**Step 13:** Take a look at the history of your git activiy on the local repository by outputing the log history to a file named, `cool_get.log`.

`git log --pretty=format:'%h : %s' --graph > cool_git.log`

Take a look at the log file:

`cat cool_git.log`

You will get the following output:

```
* 8cb66b4 : added line 3
* 359583e : added line 2
* a7d9eac : added line 1
* 5446140 : clearing file
* 5ea3e19 : Adding a message
* d12958e : Update texts.txt
* 5cd8ec7 : Update texts.txt
* 842d96b : First Commit
* ae8fa18 : Initial commit$
```
Pay attention to the commit ids. They are important. **Remember!** We added three lines to the file, `cool_test.text` incurring a `git commit` each time a line was added.

For more information about viewing commit history using `git log` go [here](https://git-scm.com/book/en/v2/Git-Basics-Viewing-the-Commit-History).

**Step 14:** Set the the state of the file, `cool_text.txt` back to the version in which there are only one line of code.

(**BE ADVISED** The relevant commit number will be different on your computer.)

Execute the command:

`git checkout 4a7d9eac`

You will get output similar to the following:

```
Note: checking out 'a7d9eac'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at a7d9eac... added line 1
```

**Step 15:** Take a look at the contents of the file, `cool_text.txt`.

`cat cool_text.txt`

You will see the following output

`I am line 1.`

**Step 16:** Go back to the version of the file that had 3 line of text.

`git checkout 8cb66b4`

Take a look at the contents of the `cool_text.txt` now.

`cat cool_text.txt`

You will get the following output:

```
I am line 1.
I am line 2.
I am line 3.
```





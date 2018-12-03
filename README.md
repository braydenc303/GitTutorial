# dBGitExperiments
Merge conflicts on purpose

-Create a new repository called merge-conflict and clone it to your computer.

-Create an index file that looks like this:

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
</head>
<body>
    <div>
        <p>I want to make a mess of this.</p>
        <p>I don't even care if we fix it. I just want to see what happens when it breaks.</p>
    </div>
</body>
</html>

-You decide to create another branch to use for experimental features.

-At the command line, create a branch called my-branch.
We will just leave this alone for now.

-On the master branch. In the code editor, edit the first paragraph to say, “I want to screw this up.”

-Save the file.

-Do a git add, git commit, and a git push origin master.

-Imagine some time has passed, and you'd like to develop on the other branch.

-Switch into to the other branch by typing:
	git checkout my-branch

-From that branch, open the file in your code editor. Above your paragraphs, add:

<h2>This is an experiment</h2>,

and change the first paragraph to say,
“I want to mess this up.” 

-Save the file.

-Once again, do a git add, then commit the changes to the repository with a commit message.

Let's say you decide you'd like to merge the changes from your branch into the master branch. This is where you can run into problems. You have made commits on separate branches that change the same line of code in different way. Now when you try to merge your other branch into master, Git will not know which changes to keep. Watch what happens.

-Switch to the master branch.

-Do a git pull origin master to make sure that you have the most up to date code.

-Do a git merge my-branch

-Notice the alert about the merge conflict.
****
$ git merge my-branch
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.

-Look at the file in vsCode Fix the merge conflict by choosing which change to accept, and save your file.

-Do a git status. You should receive a message similar to:
	
On branch master
Your branch is ahead of 'origin/master' by 1 commit.
  (use "git push" to publish your local commits)

You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")

-Do a git add.

-Do a git commit -m”Resolved merge conflict.”

-You can now push to origin/master and delete the other branch.

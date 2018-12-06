# dBGitExperiments
Merge conflicts on purpose:
A Tutorial, and Best Practices For Git Workflow.

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

-At the command line, create a branch called my-branch by typing: 
    git branch my-branch

Press enter. We will just leave this alone for now.

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

Let's say you decide you are now ready add these changes to the working version of your site. This is where you can run into problems. You have made commits on separate branches that change the same line of code in different way. Now when you try to merge your other branch into master, Git will not know which changes to keep. Watch what happens.

To be safe, lets try to merge the master branch into my-branch. That way, if there is a merge conflict, we can handle that here.

-First, switch to the master branch.

-Do a git pull origin master to make sure that you have the most up to date code. It should already be up to date, but do this as a best practice, especially if you are working in a group.

-Switch back to my-branch.

Do a git merge master

-Notice the alert about the merge conflict.
****
$ git merge master
Auto-merging index.html
CONFLICT (content): Merge conflict in index.html
Automatic merge failed; fix conflicts and then commit the result.

-Look at the file in vsCode Fix the merge conflict by choosing which change to accept, and save your file.

-Do a git status. You should receive a message similar to:
	
On branch my-branch
You have unmerged paths.
  (fix conflicts and run "git commit")
  (use "git merge --abort" to abort the merge)

Unmerged paths:
  (use "git add <file>..." to mark resolution)

        both modified:   index.html

no changes added to commit (use "git add" and/or "git commit -a")
----------------------------------------------------------
-Do a git add.

-Do a git commit -m”Resolved merge conflict.”

Once the conflict is resolved, do a git push origin my-branch. 

Now go to github website. Navigate to your repository. You my be promted to create a pull request. If so click to create the merge and pull request. If not, navigate to your branch and create a new pull request anyway.

Because of the workflow the we have used to this point, there should be no merge conflicts. This because you are working on this by yourself. This may not be the case if you are working in a group. However, conflicts should be minimized using this approach.

----------------------------------------------------------
The first portion of this exercise used a practice that is unsafe if working in a group. Typically you do not want to push to origin master if you are ever working in a group. Try to follow the best practices below.

Safe workflow practices.
---------------------------------------------------------

On your computer, create a folder where you want to store the repository.

On the github website navigate to the repository you'd like to clone and click on the clone repository button. Copy the link provided.

On your computer in your terminal, make sure you are in the folder where you'd like to store the repository. Type:
    git clone repository-link
Pasting the repository link from github where the above line says, "repository-link."

Create a new branch and give it a name appropriate to your current task.

Switch to the new branch by typing:
    git checkout new-branch
Where new-branch is the name you have given to your branch.

Do your work in here. As you make progress be sure to do git adds and commits regularly.

Once you feel that it is time to add your code to the project, switch to the master branch and do a git pull to make sure you have the most up to date code.

Switch back to your branch.

Type git merge master.

Resolve conflicts as necessary.

Once resolved, git add, git commit, and git push origin your-branch. Where your-branch is replaced with the name of the branch you are working in.

Once that is done, you can navigate on the github website to create a pull request and submit it for review.

Once your code is approved and added to the project's working master, you can delete your branch, pull origin master into your local master, create a new branch for your current task, and repeat this process safely.


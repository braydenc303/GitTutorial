# GitTutorial

## Merge conflicts on purpose: A Tutorial, and Best Practices For Git Workflow

1. On the Github website, create a new repository called merge-conflict and clone it to your computer.

2. Create an index.html file that looks like this:

    - Feel free to copy and paste the below HTML, but know that the more you simply type this out, the more it will become second nature.

    ```html
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
    ```

    - You decide to create another branch to use for experimental features.

3. At the command line, create a branch called my-branch by typing: git branch my-branch

4. Press enter. We will just leave this alone for now.

5. On the master branch. In the code editor, edit the first paragraph to say, “I want to screw this up.”

6. Save the file.

7. Do a git add, git commit, and a git push origin master.

    - Imagine some time has passed, and you'd like to develop on the other branch.

8. Switch into to the other branch by typing: git checkout my-branch

9. From that branch, open the file in your code editor. Above your paragraphs, add:

    ```html
    <h2>This is an experiment</h2>
    ```

    - and change the first paragraph to say,
“I want to mess this up.”

10. Save the file.

11. Once again, do a git add, then commit the changes to the repository with a commit message.

Let's say you decide you are now ready add these changes to the working version of your site. This is where you can run into problems. You have made commits on separate branches that change the same line of code in different way. Now when you try to merge your other branch into master, Git will not know which changes to keep. Watch what happens.

To be safe, it is always a good idea to pull the most current master before pushing. That way, if there is a merge conflict, we can handle that here.

1. On the command line type:

    ```bash
    git pull origin master
    ```

    to make sure that you have the most up to date code. It should already be up to date, but do this as a best practice, especially if you are working in a group.

2. Notice the alert about the merge conflict.

    ```bash
    $ git merge master
    Auto-merging index.html
    CONFLICT (content): Merge conflict in index.html
    Automatic merge failed; fix conflicts and then commit the result.
    ```

3. Look at the file in vsCode Fix the merge conflict by choosing which change to accept, and save your file. Feel free to choose whichever version you like.

4. In the command line, type

    ```bash
    git status
    ```

    You should receive a message similar to:

    ```bash
    On branch my-branch
    You have unmerged paths.
      (fix conflicts and run "git commit")
      (use "git merge --abort" to abort the merge)

    Unmerged paths:
      (use "git add <file>..." to mark resolution)

            both modified:   index.html

    no changes added to commit (use "git add" and/or "git commit -a")
    ```

5. git add .

6. git commit -m”Resolved merge conflict.”

7. Once the conflict is resolved, on the command line type:

    ```bash
    git push origin my-branch
    ```

8. Now go to github website. Navigate to your repository. You my be promted to create a pull request. If so click to create the merge and pull request. If not, navigate to your branch and create a new pull request anyway. 

9. Once you create the pull request, you will be taken to another screen where you should see that the branches have no conflicts and are able to merge. If you would like to include a more detailed message at this point, you can. Once you have added any additional message if any, then click the green Create pull request button.

10. Following this, you'll be tacken to a page that will allow you to approve the merge. You should see a message: This branch has no conflicts with the base branch. Merging can be performed automatically. Press the green Merge pull request button.

11. Press the green Confirm merge button. You will receive a message stating that the Pull request successfully merged and closed. You can then safely delete the branch both on the website and on your local machine.

My preference is to wait a moment before deleting my local branch. Switch back into my local master, pull the current master, and create a new branch to work in. Then I will switch to the new branch and confirm that the code works as expected before deleting the old branch that I was working on and just merged in to master.

Because of the workflow the we have used to this point, there should be no merge conflicts. This because you are working on this by yourself. This may not be the case if you are working in a group. However, conflicts should be minimized using this approach.

---

The first portion of this exercise used a practice that is unsafe if working in a group. Typically you do not want to push to origin master if you are ever working in a group. Try to follow the best practices below.

---

## GitHub Centralized Workflow

  >When following these instructions, the lines that do not begin with an uppercase letter are to be typed into the command line. Of course, you will want to substitute the name of your branch wherever you see branch-name.
  >
  >On your computer, create a folder where you want to store the repository.
  >
  >On the github website navigate to the repository you'd like to clone and click on the clone repository button. Copy the link provided.
  >
  >On your computer in your terminal, make sure you are in the folder where you'd like to store the repository.

1. git clone repository-link

    a. where repository-link is the link you copied from the Github website.

    b. (If using npm or yarn packages) npm/yarn install (if you don't know what this means yet, just skip this step)

2. git checkout -b branch-name (only if creating a new branch, otherwise it will be git checkout branch-name)

    - By convention git hub repositories and branches do not use camel case, so use dashes.

    - As much as possible try to be working on different files from your team mates.

3. Work on your task within your branch. Be sure to periodically save your work and:

    a. git status  (to see if there are changes that need to be added)

    b. git add . (to add changes)

    c. git commit -m "description of work you did"

4. Once you have changes to push.

5. git pull origin master

    - This is where you will see conflicts if there are any

    - You should be able to reconcile these in VS Code at this point.

6. (If using npm or yarn packages) npm/yarn install (see note above if you don't know what this is referring to).

7. Re-run your code to ensure everything still works.

    - If not, create a new branch in which to repair any broken code. Once it is working properly, begin again at step 3a.

8. git status

9. if needed: git add .

10. also if needed: git commit -m"explanation of changes made/conflicts resolved"

11. git push origin branch-name (of course replacing branch-name with the actual name of the branch you are currently working in)

12. Create a pull request on GitHub

    a. Let the team know about Pull Request on Slack

13. Once your code has been merged: git checkout master

14. git pull origin master

15. git checkout -b new-branch-name (replacing new-branch-name with the name of the new branch)

    a. npm/yarn install (If using npm or yarn packages, see above notes)

    b. If new packages were added:

      - git add .

      - git commit -m"new packages added"

16. Run the code in your new branch to ensure one last time that everything is working as it should. If not, speak with your team.

17. Do some more work and start again at step 3a.

    - If you have finished your project and everything is working as it should, you can now delete any unneeded local branches by moving on to step 18 in your local master branch.

18. git branch

    - To get a list of branches on your local machine.

19. git branch -d branch-name

    - For each of your local branches you wish to discard.

20. You may get a warning about your branch not being fully merged at this point. If so: git branch -D branch-name

Though you do not need to use this workflow when working by yourself, know that you absolutely may, and that it will prepare you for working in a group better than just about anything. There is nothing that we do as programmers, that we don't get better at with practice. Practice, practice, practice, and you will be a Git ace in no time. Even just running through this exercise once in a while can be extremely helpful.

Cheers!
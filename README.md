# GitTutorial

## Merge conflicts on purpose: A Tutorial, and Best Practices For Git Workflow

1. Create a new repository called merge-conflict and clone it to your computer.

2. Create an index file that looks like this:

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

To be safe, lets try to merge the master branch into my-branch. That way, if there is a merge conflict, we can handle that here.

1. First, switch to the master branch.

2. Do a git pull origin master to make sure that you have the most up to date code. It should already be up to date, but do this as a best practice, especially if you are working in a group.

3. Switch back to my-branch.

4. Do a git merge master

5. Notice the alert about the merge conflict.

    ```bash
    $ git merge master
    Auto-merging index.html
    CONFLICT (content): Merge conflict in index.html
    Automatic merge failed; fix conflicts and then commit the result.
    ```

6. Look at the file in vsCode Fix the merge conflict by choosing which change to accept, and save your file.

7. Do a git status. You should receive a message similar to:

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

8. Do a: git add .

9. Do a: git commit -m”Resolved merge conflict.”

10. Once the conflict is resolved, do a: git push origin my-branch.

Now go to github website. Navigate to your repository. You my be promted to create a pull request. If so click to create the merge and pull request. If not, navigate to your branch and create a new pull request anyway.

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

    b. (If using npm or yarn packages) yarn/npm install

2. git checkout -b branch-name (only if creating a new branch, otherwise it will be git checkout branch-name)

    - By convention git hub repositories and branches do not use camel case, so use dashes.

    - As much as possible try to be working on different files from your team mates.

3. Work on your task within your branch. Be sure to periodically save your work and:

    a. git status  (to see if there are changes that need to be added)

    b. git add . (to add changes)

    c. git commit -m "description of work you did"

4. Once you have a change to push.

    - git checkout master

5. git pull origin master

6. git checkout branch-name

7. git merge master

    - This is where you will see conflicts if there are any

    - You should be able to reconcile these in VS Code at this point.

8. (If using npm or yarn packages) yarn/npm install

9. Re-run your code to ensure everything still works.

    - If not, create a new branch in which to repair any broken code. Once it is working properly, begin again at step 3a.

10. git checkout branch-name

11. git push origin branch-name

12. Create a pull request on GitHub

    a. Let the team know about Pull Request on Slack

13. Once your code has been merged: git checkout master

14. git pull origin master

    a. yarn/npm install (If using npm or yarn packages)

    b. If new packages were added:

      - git add . and git commit -m"new packages added."

15. Run the code in your master branch to ensure one last time that everything is working as it should. If not, speak with your team.

16. git checkout -b new-branch-name

17. Do some more work and start again at step 3a.

    - If you have finished your project and everything is working as it should, you can now delete your local branches by moving on to step 16.

18. git branch

    - To get a list of branches on your local machine.

19. git branch -d branch-name

    - For each of your local branches.

20. You may get a warning about your branch not being fully merged at this point. If so: git branch -D branch-name

![image](https://github.com/Rapha-Borges/mdBook-action/assets/53947674/6dc3c8d0-9442-4a7b-b30a-1e7f1cdc3355)


# mdBook-action
A custom action to deploy mdBook

This Github action is triggered when a push occurs on the "main" branch of the repository. It executes a series of steps within a job named "build", which runs on the latest version of the Ubuntu operating system.

The steps include using the "actions/checkout@v3" action to perform a checkout of the current repository. Then, it utilizes a Docker container with the image "raphaelborges/mdbook:1.0.2" to build a book located at the path "/github/workspace/book".

After that, the action grants execution permission to a shell script named "copy.sh" located in the ".github/workflows" directory. Finally, it runs this shell script using the "sh" command, also located in the ".github/workflows" directory.

 The "copy.sh" script does:

1. It creates a worktree named "gh-pages" using the Git command "git worktree add".

2. The script sets the Git configuration with a user name and email for the deployment from CI.

3. It navigates to the "gh-pages" directory.

4. The script deletes the reference to the "gh-pages" branch, ensuring a clean slate, and removes all existing files in the directory.

5. It copies files from the "home" directory (located at the repository's root) and the "/book/book/i18n" directory to the "gh-pages" directory.

6. The script adds all the copied files, commits the changes with a commit message indicating the deployment of a specific GitHub SHA, and forces a push to the "gh-pages" branch on the "origin" remote repository.

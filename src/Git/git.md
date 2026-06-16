# Git
Git is a distributed version control system that allows developers to track changes in their codebase, collaborate with others, and manage different versions of their projects. It was created by Linus Torvalds in 2005 and has since become one of the most widely used version control systems in the software development industry.

## Key Concepts
- **Repository**: A repository, or repo, is a storage location for your project. It contains all the files and history of changes made to those files.
- **Commit**: A commit is a snapshot of your repository at a specific point in time. It includes a message describing the changes made and a unique identifier (hash).
- **Branch**: A branch is a separate line of development in a repository. It allows you to work on different features or bug fixes without affecting the main codebase.
- **Merge**: Merging is the process of combining changes from one branch into another. This is often done when a feature branch is ready to be integrated into the main branch.
- **Remote**: A remote is a version of your repository that is hosted on a server, such as GitHub or GitLab. It allows you to collaborate with others and share your code.
- **Clone**: Cloning is the process of creating a local copy of a remote repository on your machine. This allows you to work on the code locally and then push your changes back to the remote repository.
- **Pull**: Pulling is the process of fetching changes from a remote repository and merging them into your local repository. This is often done to keep your local code up to date with the latest changes from other collaborators.
- **Push**: Pushing is the process of sending your local commits to a remote repository. This allows others to see your changes and collaborate on the project.
- **Fork**: Forking is the process of creating a copy of a repository under your own account. This allows you to make changes to the code without affecting the original repository. You can then submit a pull request to propose your changes to the original repository.
- **Pull Request**: A pull request is a way to propose changes to a repository. It allows you to submit your changes for review and discussion before they are merged into the main codebase.

## How to Use Git
1. **Initialize a Repository**: To start using Git, you can initialize a new repository in your project directory using the command `git init`.
2. **Add Files**: You can add files to your repository using the command `git add <file>`. This stages the files for the next commit.
3. **Commit Changes**: To save your changes, you can create a commit using the command `git commit -m "Your commit message"`. This will create a snapshot of your repository with the changes you have made.
4. **Create a Branch**: To create a new branch, you can use the command `git branch <branch-name>`. This will create a new branch that you can switch to and work on independently from the main branch.
5. ** Switch Branches**: To switch to a different branch, you can use the command `git checkout <branch-name>`. This will change your working directory to the specified branch.
6. **Merge Branches**: To merge changes from one branch into another, you can use the command `git merge <branch-name>`. This will combine the changes from the specified branch into your current branch.
7. **Push Changes**: To push your commits to a remote repository, you can use the command `git push origin <branch-name>`. This will send your changes to the remote repository for others to see and collaborate on.
8. **Pull Changes**: To pull changes from a remote repository, you can use the command `git pull origin <branch-name>`. This will fetch the latest changes from the remote repository and merge them into your local branch.
9. **Fork a Repository**: To fork a repository, you can use the "Fork" button on platforms like GitHub. This will create a copy of the repository under your own account, allowing you to make changes without affecting the original repository.
10. **Submit a Pull Request**: After making changes to a forked repository, you can submit a pull request to propose your changes to the original repository. This allows the maintainers of the original repository to review your changes and decide whether to merge them into the main codebase.
11. **Remove a Repository**: To remove a local repository, you can simply delete the directory containing the repository. To remove a remote repository, you can use the command `git remote remove <remote-name>`.
12. **Set origin** `git remote set-url origin ssh_route`


## Generate a key ssh
1. Open a terminal and run the following command to generate a new SSH key:

```bash
ssh-keygen -t ed25519 -C "email_address" -f "path_to_save_key"
```
  For example, to generate a key fo use to push in git  from powershell. This command will create a new SSH key using the Ed25519 algorithm and associate it with your email address.
```bash
ssh-keygen -t ed25519 -C "test@gmail.com" -f "$env:USERPROFILE\.ssh\id_ed25519_test"
````
2. When prompted, specify the file where you want to save the key (or press Enter to accept the default location).
3. You will be asked to enter a passphrase for added security. You can choose to enter a passphrase or leave it empty for no passphrase.
4. After completing the steps, your SSH key will be generated and saved to the specified location. You can then add the public key to your Git hosting service (e.g., GitHub, GitLab) to enable SSH authentication for your Git operations.

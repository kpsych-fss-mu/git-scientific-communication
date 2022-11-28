# **Introduction to version control with Git for a more efficient collaboration**

## **Table of Contents**
- [**What is a version?**](#what-is-a-version)
- [**What is version control?**](#what-is-version-control)
- [**Using Git**](#using-git)
- [**Useful shell commands**](#useful-shell-commands)
- [**Clone a repository (git clone)**](#clone-a-repository-git-clone)
- [**Creating a branch**](#creating-a-branch)
- [**Pushing changes (git push)**](#pushing-changes-git-push)
- [**Pull request**](#pull-request)
- [**Update (git pull**](#update-git-pull)
- [**Bug reporting (issues)**](#bug-reporting-issues)
- [**README: Information for others**](#readme-information-for-others)
- [**License**](#license)
- [**Next: Hands-on!**](#next-hands-on)
- [**Resources**](#resources)

## **What is a version?**
- <u>Contents of a file at a given point in time</u>
- **Metadata** (information associated with the file):
  - *The author of the file*
  - *Location*
  - *Type*
  - *Timestamp of the last save*
  
## **What is version control?**
- **Version control** is a <u>group of systems and processes</u>
  - To manage changes made to documents, programs, and directories
- Version control is **useful** for anything that:
  - **changes over time**, or
  - **needs to be shared** 

<img src="git-logo.png" width="400" class="center">

- [Git](https://git-scm.com/) is a popular **version control system** for computer programming and other projects 
- [**Open source**](https://en.wikipedia.org/wiki/Open-source_software)
- **Scalable** (= in terms of projects, collaborators or resources)

- **Benefits** of Git:
  - Git **stores contents and metadata**, so nothing is lost
  - Git **notifies** use when there is **conflicting content** in files
  - Git **synchronizes** across different people and computers

> **Action**

- Install Git or check whether you have it already for your respective operation system:
[Linux](https://github.com/git-guides/install-git?fbclid=IwAR1kihhEjz295LQ6s65BlIzxdTamThQBcVzBnBs1ZDQ0pKT4HOJLZF9aWT8#install-git-on-linux), [MacOs](https://github.com/git-guides/install-git?fbclid=IwAR1kihhEjz295LQ6s65BlIzxdTamThQBcVzBnBs1ZDQ0pKT4HOJLZF9aWT8#install-git-on-windows) and [Windows](https://github.com/git-guides/install-git?fbclid=IwAR1kihhEjz295LQ6s65BlIzxdTamThQBcVzBnBs1ZDQ0pKT4HOJLZF9aWT8#install-git-on-windows).

In case you are **Windows** users, **consider installing shell** along the way. 

## **Using Git**
- Git commants are run on the **shell**, also known as the **terminal**
- The **shell** (*Zsh*, *PowerShell*,...)
  - is a **program for executing commants** (e.g., create a folder)
  - can be used to easily <u>preview, modify, or inspect files and directories</u> (= folders)
  
> **Action**

- Open your terminal - either inside another tool like [RStudio](https://support.posit.co/hc/en-us/articles/115010737148-Using-the-RStudio-Terminal) or as a [standalone app](https://towardsdatascience.com/a-quick-guide-to-using-command-line-terminal-96815b97b955).
  
## **Useful shell commands**

- *Locate your current working directory* - `pwd`
- *List all of the items in the current working directory* - `ls`
- *Change a directory* - `cd <directory_name>`
- *Checking Git version* - `git --version`
- *Create or edit a file* - `echo`

For more commands, see (e.g.) the following [article](https://towardsdatascience.com/how-to-become-a-command-line-wizard-5d78d75fbf0c).

Please note that the [**default command prompt**](https://www.makeuseof.com/tag/a-beginners-guide-to-the-windows-command-line) on **Windows uses different syntax**. 

<img src="github.png" alias= "#github" width="400" class="center">

- Cloud-based hosting **service**
- Allows users to store and track their work (= version control)
- **On-demand resources** over the internet, such as **storage**

There are plenty of sites on the Internet where you can upload git repositories with code - e.g. [GitLab](https://about.gitlab.com/) or [BitBucket](https://bitbucket.org/product).

- <u>Use-cases</u>
  - *Storing projects*
  - *Keeping track of projects and files*
  - *Collaborating with others*
  - *Social network*
  - *Open-source projects*

**GitHub enhances Git, but cannot be used without it.**

> **Action**

- If you don't already have a user account on github.com, go there and create one.

## **Clone a repository** (`git clone`)
- To get started, let's try working with a repository created for the purposes of this workshop. 

> **Action**

- Type the following command in your command line:
```
git clone https://github.com/kpsych-fss-mu/git-scientific-communication.git
```

- A new repository will be created - a directory with the name `git-scientific-communication` that contains folders and files.

> **Action**

- You can look at the **URL** you used in this example in your **browser**. There, you'll see a **list of files** and lots of **links** to information about the repository (for example, under **"commits"** is the history).

> **Action**

- Switch to the new directory (`cd git-scientific-communication`) and try looking at the history (`gitk` or `git log`). It may be short, but it's important that there is some. You have a copy of a project on your computer that someone else created!

- **Your contribution to this project** will be a **write to the repository**: specifically, <u>adding a file with your name on it</u>. 
  - The **name** (or distinct identificator) is there **to avoid clashes**: we need the contributions from all the people going through this course to be different.

- However, your post will be **publicly displayed on the internet**. If you don't want to expose your real name, feel free to use a **nickname**, a favorite food, or a few random letters instead (be original to avoid conflicts). 
  - Whatever you decide to use, it will be referred to as `<your_name>` further down the line.

## **Creating a branch**

<img src="octopus.jpeg" width="600" class="center">

> **Action** 

- Use `git branch` to find out what branch you are currently on. It should be the `master` / `main` [branch](https://www.theserverside.com/feature/Why-GitHub-renamed-its-master-branch-to-main).

- This `master` / `main` branch is only good to use for commits that the whole team has already **agreed** on. So when you want to contribute to a project, the <u>first step is to make a new branch for your contribution and switch to that branch</u>. For example:
```
git branch <your_branch>
git checkout <your_branch>
```

## **Pushing changes** (`git push`)
> **Action**

- In R, create a data file to be shared with others.

```
# Excplicitedly call the source package
library("datasets")

# Import the USArrests dataset from the package
data("USArrests", package = "datasets")

# Save the object as a data frame
USArrests <- as.data.frame(USArrests)

# Export the data frame as a .csv file with <your_name>
write.csv(USArrests, file = "data/USArrests_<your_name>.csv", row.names = FALSE)
```

> **Action**

- Add a file named after your name (or nickname):
```
git add USArrests_<your_name>.csv
```

- Use the `git status` to observe the indicated changes:
```
git status
```

- Commit the added file to git (`git commit`):
```
git commit -m "Add the USArrests data for the respective contributor"
```

- Again, use the `git status` and compare the outcome with the previous status:
```
git status
```

- Now all that's left to do is "just" **merge the change into the original** shared repository. But that's not easy: the repository you cloned [cannot be changed](https://docs.github.com/en/repositories/configuring-branches-and-merges-in-your-repository/defining-the-mergeability-of-pull-requests/managing-a-branch-protection-rule) by just anyone.
- A lot of places on the Internet (**blogs, news sites, e-shops**) work in such a way that a **select group of peopl**e, "editors", have the **right to change the content** as they like. 
  - Such editors must be **trusted by the project administrator** before they are allowed access.
- With **Git**, a slightly **different mechanism** is used: you **upload changes to your own shared repository**, which only you have the right to change.   - You then **write a pull request** to the **owner of the original project**. This could be an email saying *"Hey, I have some changes at so-and-so address that you might find useful! Add them to your project!"*
- The advantage is that **anyone can** join the project - if it's [**public**](https://docs.github.com/en/repositories/creating-and-managing-repositories/about-repositories). **You don't have to ask beforehand**, you don't have to prove you're a trustworthy person, just change something and send it. 
  - <u>Whether the authors of the project like the change or not is another matter</u> - but they can judge the change itself, not the credibility of the author.
- **Services** like github.com allow you to make your own **shared repository** (which will be **available on the web**) and make it easy to **incorporate changes** (instead of sending an email, just press a button). Let's see how to do it.

> **Action**

- **Log in to GitHub** and then go to the **address** you used for `git clone`. Find the **"Fork"** button on the top left and click it. This will create your own copy of the repository on GitHub. The address should be something like: `https://github.com/<your_github_name>/git-scientific-communication.git`.

> **Action**

- Now, how do you <u>upload changes from your computer to GitHub</u>? For each repository on your computer, Git remembers the addresses where you can download and push changes. The `git remote -v command` will show you a list of those addresses. For example:
```
git remote -v
origin https://github.com/kpsych-fss-mu/git-scientific-communication.git (fetch)
origin https://github.com/kpsych-fss-mu/git-scientific-communication.git (push)
```
- This output means that "origin" is the address from which you cloned the repository.

> **Action**

- Add a similar shortcut for your own repository on GitHub. Don't forget to replace your name with the name of the account you have on GitHub. (Note that your name appears twice in the command!)

- `git remote add <your_name> https://github.com/<your_github_name>/git-scientific-communication.git` and check that it worked:
```
git remote -v
origin git@github.com:kpsych-fss-mu/git-scientific-communication.git.git (fetch)
origin git@github.com:kpsych-fss-mu/git-scientific-communication.git.git (push)
<your_name> https://github.com/<your_name>/git-scientific-communication (fetch)
<your_name> https://github.com/<your_name>/git-scientific-communication (push)
```

> **Action**

- So much for the setup - just do git remote add once for each repository. Then you can upload changes using:
```
git push --set-upstream origin <your_branch>
```

- Which means: push the</u> `<your_branch>` <u>branch to the address stored under</u> `<your_name>`.

> **Action**

- Does it work? Look at `https://github.com/<your_github_name>/git-scientific-communication` in your browser and make sure your changes are there.

## **Pull request**

- Now all you have to do is <u>ask the authors of the original project to add the changes from your shared repository to their copy</u>. GitHub has a mechanism for doing this called a [**pull request**](https://docs.github.com/en/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).

> **Action**

- Go to the original project's page (the address you used for `git clone` in the beginning). There you should see a notification of your newly uploaded branch with a big green **Compare & pull request button**. **Click** on it. If you want, **add/change the description** of what this change entails. Then hit the next button.

- If you don't see the Compare & pull request button, go to the **address of your copy of the repository** and hit the **New pull request** button. **Select** what you want to include, **add/change** the label, then press **Create pull request**.
- **You're done**! Now it's up to the **project authors** to look at the changes and **accept** them - or start a **discussion** about how to make them even better. (You can discuss on the pull request page or via email.)
- This probably won't happen for adding a name to the attendance list, but if you needed to work on the change a bit more before incorporating it (even after a few days of discussion), it wouldn't be a problem. **Switch to the** `<your_branch>` **branch on your machine**, make **further commits**, and use **git push to update** your `<your_branch>` **pull request**.

## **Update** (`git pull`)
- Once your **changes** - and those of others - have been **merged**, you can **update your local repository**.
  - This is the **one on your computer**.

> **Action** 

- First, **switch back** to the `master` branch. Now you won't be working on `<your_branch>`; that branch is already committed.
- This is done with `git pull origin master` (pull changes from the "master" branch from the address under "origin"). You can use `gitk --all` or `git log` to see how the project has evolved in the meantime.

- It's always a good idea to do this `git pull` **before you start working on a new change/branch**. This will ensure that the project you are changing is **"fresh"**.
  - Congratulations! You just went through the "round" that most programmers do every day: making a change, pushing it to colleagues for review and incorporation, and pulling changes from others.
  
<img src="git-workflow.png" width="600" class="center">

## **Bug reporting** (issues)

- Occasionally, you **find a bug** in a GitHub project, but you **don't have the time or knowledge to fix it**. 
  - In this case, you'll often find a list of reported [**issues**](https://docs.github.com/en/issues/tracking-your-work-with-issues/about-issues) on the GitHub project page under the **Issues tab**. 
  - If you don't find "your" bug among them, you can report it - just click on **New Issue** and you can <u>post when the bug occurs, what the program is doing wrong, and what it should be doing instead</u>.
- Some projects don't use Issues on GitHub. If you can't find the Issues tab, check the project documentation to see if there's a link to the bug list.

## **README**: Information for others
- <u>If you're creating a project and want others to contribute to it, you need them to know what your project does, what it's good for, how it's used</u>, etc.

- The [**README**](https://docs.github.com/en/repositories/managing-your-repositorys-settings-and-features/customizing-your-repository/about-readmes) file is used for **basic information about the project/repository**. This file can include:
  - *project name*,
  - *a brief description of the project (one or two sentences)*,
  - *a short instruction on how to install the project*,
  - *short instructions on how to run the project*,
  - *short instructions on how to use the project, or a link to more extensive documentation*,
  - *if the project has tests, information on how to run them*,
  - *information on how to get involved in the development of the project*,
  - *information about the authors of the project*,
  - *licensing information (more on licensing later)*.

- The README should be **structured** and shouldn't take the user an hour to read, **usually short punchy information with a possible link somewhere else is enough**. 
  - For example, you don't need to explain in each project how to install Python. Just say that Python is needed (and in which version) and refer the user to the appropriate instructions. 
    - You also need to take into account the **inteded audience(s)** or **who will be reading** the README.
- GitHub (and lots of other similar services) allows you to **use a markup language** such as **Markdown** for the README. It's then possible to use headings, images, etc.
- And last but not least: **open-source projects tend to be in English** so that anyone from around the world can participate. **Variable names, comments, documentation** - everything is **primarily in English**.

## **License**
- To make **sharing work for legal purposes**, it is **not enough to upload a piece of code to the Internet**. You also have to **officially announce** that others can play with it. 
  - This is because **you have a copyright** on your code that says **others cannot use your program**, let alone improve it, **unless you give them permission.** 
    - <u>To formally grant this permission, they use licenses written by lawyers</u>.
- The issue of licenses can, unfortunately, be quite complex. But if you simplify it to the minimum, you just want to ensure that everyone can use your creation, learn from it, pass it on, and improve it. In that case, choose, for example, the [*MIT license*](https://en.wikipedia.org/wiki/MIT_License).
- In addition, if you want to prevent someone from taking your code and "improving" it and profiting from it without sharing the improvements with others, try the [*AGPL*](https://en.wikipedia.org/wiki/Affero_General_Public_License).
- Code is most often licensed by putting the license text into a file called `LICENSE` and adding it to Git. It is a good idea to mention the license in the `README` file as well.
- If you want to read more about licenses, I refer you to choosealicense.com, or creativecommons.org and opensource.org.

## **Next: Hands-on!**

> **Action**

- **Consider a project** where you want tu use Git (and GitHub; *~15 min*)
  - What is the **nature of the collaboration** in this project? 
  - Who are the **collaborators**?
  
- **Create** the respective **repository**
 - Secure the main branch from pushing directly to it
 - Set **tokens** and other **security** elements
 - **Create** the **README** and **licence** files
 - **Push** all of the related **materials to the repository** and **create a pull request**
 - Let the **collaborator review** the pushed code.
 - **After** the changes are **merged**, <u>checkout to the local main branch and pull the updated remote main branch</u>.


## **Resources**

- You may find multiple resources for learning git and/or services like GitHub available for free (although sometimes you need to register).

### **Courses**

- [Introduction to Version Control with Git](https://app.datacamp.com/learn/courses/introduction-to-version-control-with-git)
- [Introduction to Git](https://app.datacamp.com/learn/courses/introduction-to-git)
- [GitHub Concepts](https://app.datacamp.com/learn/courses/github-concepts)
- [Git: Become an Expert in Git & GitHub in 4 Hours](https://www.udemy.com/course/git-expert-4-hours)
- [Introduction to Git and GitHub](https://www.coursera.org/learn/introduction-git-github)
- [Spolupráce a Open-Source](https://naucse.python.cz/course/pyladies/sessions/foss/) (Czech)


### **Documentation**

- [Git - Documentation](https://git-scm.com/doc)
- [GitHub Docs](https://docs.github.com/en)

### **Cheat-sheets**

- [git](https://pyvec.github.io/cheatsheets/basic-git/basic-git-cs.pdf) (Czech)
- [Markdown](https://www.markdownguide.org/cheat-sheet/)

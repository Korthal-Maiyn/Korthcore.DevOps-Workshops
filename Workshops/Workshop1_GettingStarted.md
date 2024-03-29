﻿# Workshop 1 : Getting Started

The aim of this workshop is to run through the basics of how to get started, including some incredibly relevant links for additional resources, and a small excercise to get you going. A lot of the content within will be a very high overview of processes, tools etc to help get you started, but please be aware there are many *many* different ways to tackle this, as such it is entirely plausible some items in this you will very much have a working knowledge of already, but don't worry this is merely a very simplistic getting started guide to help you on your journey. So with this in mind, let's jump straight into it!

## Contents

1. [Setting Up Your local Environment](#Setting-Up-Your-Local-Environment)
    - [Getting Started With WSL2](#Getting-Started-With-WSL2)
    - [Configuring an IDE](#Configuring-an-IDE)
        - [Starter Visual Studio Code Extensions](#Starter-Visual-Studio-Code-Extensions)
    - [Configuring SSH (Optional)](#Configuring-SSH-(Optional))
2. [Source Control Management and Git](#Source-Control-Management-and-Git)
    - [Git Branch Workflow](#Git-Branch-Workflow)
    - [Basic Git](#Basic-Git)
    - [Git in Visual Studio Code](#Git-in-Visual-Studio-Code)
3. [Pull Requests](#Pull-Requests)
    - [Code Reviews Comments and Collaboration](#Code-Reviews-Comments-and-Collaboration)
    - [Merging](#Merging)
4. [Helpful Resources](#Helpful-Resources)

# Setting Up Your Local Environment

There are so many different ways you can configure your working environment, one primary thing when working alongside like minded individuals is to attempt to have a standard configuration no matter where you are. This helps ensure that no matter who is doing the work, that the development environment they are working in is standardised helping to reduce issues or oddities between different environments. Whilst this is very much an important step, it's important to recognise that these kinds of configurations are simply a guideline and that it is very much possible to have different environments working together cohesively without hassle.

That said for this particular configuration we will be choosing to setup and configure Windows Subsystem for Linux on your machine to help ensure the standardisation aspect as above. It is very much possible to set this up in Windows by itself, or even OS X for Mac Users, however in doing so generally there are some extra configuration items required so we'll keep it simple and containerised / separate from your primary working device for the purpose of this workshop.

## Getting Started With WSL2

If you've not heard of ***WSL2***, this stands for Windows Subsytem for Linux and is essentially the Linux Kernel (with multiple different Linux distributions available) running directly on your Windows machine as opposed to spinning up a VM or similar. There are a huge number of benefits in doing so, all of which you can look to read more about [here](https://docs.microsoft.com/en-us/windows/wsl/about). We won't dig into the specifics / benefits of ***WSL2*** as a development environment, but we will ensure to standardise by using Ubuntu on ***WSL2*** on our machines.

We'll be going over a super high level version of the following [documentation](https://docs.microsoft.com/en-us/windows/wsl/setup/environment), but please do feel free to read more on this if you'd like to play with your configuration to understand how ***WSL2*** works on your Windows machine.

Start by opening up Windows PowerShell as Administrator (or cmd.exe if that's your thing) and typing `wsl --install` which will immediately do the following :

- Enable the required optional components
- Download the latest Linux kernel
- Set ***WSL2*** as your Default
- Install a Linux distribution (Ubuntu by default)

Once this installation has processed you'll want to open ***Ubuntu*** from your Start Menu which will in turn open up the ***Ubuntu*** Distribution prompting you to finalise the installation by providing a User Name and Password for the primary Linux Administrator account, thus allowing you to use `sudo` commands where necessary. You can, quite obviously, set these to be whatever you want it to be, it's your environment after all!

Congratulations! You now have the ***Ubuntu*** Linux Distribution installed on your Windows machine, and have the facility to treat it exactly like you would any other Linux environment. You can spend the time setting up how you'd like to access this however you would like, I, personally, use Windows Terminal as my all in one Terminal and you can read more on how to use this [here](https://docs.microsoft.com/en-us/windows/wsl/setup/environment#set-up-windows-terminal).

For some additional information, you can easily access your Windows file directory from your WSL Distribution by accessing `/mnt/<drive letter>/` or alternatively the other way around, accessing WSL from Windows via `\\wsl$\<Distro>\home\<username>`.

### First Steps Within Ubuntu

Now that you have your sudo user credentials configured, the first thing you should always look to do is update and upgrade the packages pre-installed on ***Ubuntu*** to ensure they have been updated to the latest version, this includes Git which comes pre-installed on most Linux Distributions. Once you've got your Ubuntu Terminal in front of you, simply type `sudo apt update && sudo apt upgrade` and you'll have everything updated appropriately. You should look to do this regularly, I like to this every time I fire up the Distribution to ensure things are kept up to date.

## Configuring an IDE

Now, as above with Distros, there are countless IDE's available that you can choose to use and you may in fact already have a favourite you use daily. However, in order to keep things standardised we are going to talk about ***Visual Studio Code*** specifically as this has fantastic integration with WSL but also a myriad of Extensions available to help with your workflow. There are really two main parts to this, installing ***Visual Studio Code*** and utilising an environment configuration to standardise configs across the board.

Doesn't need much explanation but either head to [https://code.visualstudio.com/Download](https://code.visualstudio.com/Download) and download the latest version applicable for your system *or* if you've still got PowerShell as Admin open, simply type `winget install -e --id Microsoft.VisualStudioCode` to use the Windows Package Manager to install ***Visual Studio Code*** from the command line.

Either way, get ***Visual Studio Code*** installed and we can get some basic Extensions installed! Check the below image for a super handy guide to [Keyboard Shortcuts](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf) within ***Visual Studio Code***.

<div style="text-align: center;">

![Visual Studio Code Keyboard Shortcuts](/Workshops/images/1.1_VSCodeShortcuts.png)

</div>

There is also a typical Configuration you can set to use on every single installation for a Project, no matter who's computer this is. You can find these standard configuration files in the ***.vscode/settings.json*** file included in this repository. By sharing this configuration template, you can ensure that every person working on a code base / repository has a somewhat identical configuration for their ***Visual Studio Code*** installation, standardising items such as Tab Sizes, Spaces vs Tabs etc. Have a look through the provided config and see if you can make sense of what items do what, they should be nicely commented to help you out!

### Starter Visual Studio Code Extensions

If you open up ***Visual Studio Code*** and hit `View -> Extensions (Ctrl+Shift+X)` you'll bring up the Extensions sidebar. This will show you a list of currently installed Extension and the facility to search for Extensions in the Marketplace. There are, quite literally, hundreds upon hundreds of different Extensions to use for different use cases. To keep things nice and simple we will only install a handful relevant to this Workshop, but do feel free to have a browse and see what's available! Maybe try to find a theme that you like outside of the default options! The items below will outline the Extension name and it's author so you can verify the Extension as there are quite a few with similar names around the place. These Extensions will be split into their relevance with a title for each.

#### Remote Development

- Remote - WSL | Microsoft
- Remote - SSH | Microsoft
- Remote Development | Microsoft

#### Git Tools

- Conventional Commits | vivaxy
- GitLens | GitKraken
- Gitignore | CodeZombie

You may also want to find some language specific Extensions relevant to your use case. Maybe some PowerShell or Pester Tests Extensions. Perhaps a markdown linter. Bicep language support. You get the idea, there are countless extensions available to help you configure your ***Visual Studio Code*** to suit your particular development needs.

Notice in the Extensions above you do not have to install Git or Version/Source Control at all, the Git Extensions are simply additional helpers. ***Visual Studio Code*** has integrated source control management and comes with Git support out-of-the-box which makes it super handy! You can straight up open this on the Sidebar menu or by using the `Ctrl+Shift+G G`

## Configuring SSH (Optional)

This particular step isn't necessarily a requirement (thus why it is Optional) but realistically you should be using SSH Authentication wherever possible due to it's security, and even more so when using a Linux Distro where you only have the command line interface accessible (not to say the other isn't possible). Both methods, for reference, work absolutely fine within a Development Environment and I actually use a mix of both depending on if my environment is Windows or Linux based. But everyone should know how to configure SSH Authentication for source control repositories at it's most basic level and understand how these work and are configured within ***Azure DevOps*** so as that access can be provided (where relevant) in a secure manner. This also includes *Personal Access Tokens* however they are outside the scope of this Workshop.

As noted above, you can absolutely configure SSH on a Windows environment (of which I have and use), but for the sake of standardisation we will only focus on generating this within the Linux Distro for this documentation. If you're feeling spicy, feel free to set this up within your Windows Environment instead!

I will be using **Azure DevOps** within this workshop specifically as that is what I am using currently, as such there are some caveats. Namely that, at the time of this writing, there is only really **good** support for using a typical *RSA* SSH key type. Whilst this is, realistically more than adequate, the *RSA* SSH keys are technically less secure than using the newer *ED25519* SSH key type, so make sure to at least use a key size of 2048 bits when generating *RSA* SSH keys. Maybe one day specific support may come for ***Azure DevOps***, however as it stands we will focus on the *RSA* SSH key type.

As above, if you're feeling adventurous, why not try configuring an *ED25519* SSH key with a provider such as GitHub for a personal Repository to play with. Or maybe try and find some of the workarounds that exist to utilise *ED25519* encryption within ***Azure DevOps*** instead (yes, it is somewhat possible!). All of this will help understand the security and provisioning of access to Repositories outside of a standard GUI logon.

Open up your Linux Distro command line interfact and simply type `ssh-keygen -C "username@domain.com"` to generate a new *RSA* SSH key-pair. Leaving no options on `ssh-keygen` will, by default, create a 2048 bit *RSA* key-pair. You will then be prompted to choose a location to save this, just leave the default as this is pretty standard (this is almost always `/home/<username>/.ssh/id_rsa`). You can, if you so choose, add a passphrase to make your key more secure, however for this particular Workshop that is not necessary. If all goes to plan you should have an output similar to below!

<div style="text-align: center;">

![Configuring SSH](/Workshops/images/1.2_ConfiguringSSH.png)

</div>

You need to then take this newly generated *RSA* SSH Key and configure it against your ***Azure DevOps*** account so as that the platform knows which user is authenticating and as such what permissions within the Project they are entitled to. We will want to start by copying your *RSA* SSH key to your clipboard in order to paste into your SSH public keys section within ***Azure DevOps***.

*Note: This goes without saying, but for those who have not used SSH authentication before, never **EVER** share your Private Key with anyone. This is your key and your key alone. As noted before we generate a key-pair (public and private) and we simply use the Public key to authenticate against our Private key for verification.*

Start by typing `cat ~/.ssh/id_rsa.pub` into the Ubuntu CLI to show an output of your Public Key. There are other ways to automatically copy this to the clipboard, however this will suffice. Simply highlight the output of the Public Key and Right+Click to copy to your clipboard. It will look something like this :

<div style="text-align: center;">

![RSA SSH Public Key Output](/Workshops/images/1.3_PubKey.png)

</div>

Notice the start `ssh-rsa` and the end `username@domain.com` this tells us the key type and the -C comment we made to generate the key. You add comments to help easily distinguish the use case of these keys, and for the most part tend to follow a *username@hostname* or *email.address@domain.com* format.

Now we need to paste this Public Key into your ***Azure DevOps*** Organisation. Obviously start by logging in to your [Azure DevOps Organisation](https://dev.azure.com/) and once you are logged in, select your **User Profile** icon up the Top Right (Step 1). From the subsequent dropdown menu select **Security** (Step 2). And finally select the **SSH public keys** menu item from the left hand menu (Step 3). Unless you've set this up previously, you should be presented with an empty list.

<div style="text-align: center;">

![RSA SSH Public Key Output](/Workshops/images/1.4_SSHPublicKeys.png)

</div>

Hit **+ New Key** up the top right, give it a name that makes sense to you (so as that you know where the Private Key for this Public Key is stored, usually the Computer Name is a good start) and paste the previously copied Public Key into the *Public Key Data* field below. Congratulations! You've just configured SSH Authentication for ***Azure DevOps***. You can verify this by selecting the newly added key and verifying the data matches what you have input. It should look much like the below.

<div style="text-align: center;">

![RSA SSH Public Key Output](/Workshops/images/1.5_SSHKeyData.png)

</div>

*Note: The details above have already been deleted after screenshots were taken. Images for informational purposes only.*

# Source Control Management and Git

I'm sure most everyone knows about or has heard of Git at least in some capacity. As a simple refresher a git repository is simply a place where the history of the work you have done is stored. Git is only one of a few different types of Version Control / Source Control Management, each with their own pros and cons. However, Git is the most relevant use case for us here and as such is all we will be focussing on. Do feel free to look up some of the others to see the differences!

When it comes to creating a new Repository to store your code base you generally determine what kind of workflow you want to employ for your repository. There are, actually, quite a few different options available to choose from and the type you use kind of helps determine your continuous delivery process. But, it's important to choose a workflow that is suitable for the Team itself, rather than determining which is the *best*. Each option has it's own list of pro's and cons and may or may not integrate in a way that is best for your team's effectiveness.

## Git Branch Workflow

As above, when choosing a workflow a couple of importing things to consider are :

- Does this workflow scale with team sie?
- Is it easy to undo mistakes and errors with this workflow?
- Does this workflow impose any new unnecessary cognitive overhead on the team?

And taking a look at some of the more common workflows :

- ***Git Flow*** | You generally have a `main` branch which contains production ready code. A `dev` branch in which newly developed features are integrated and tested. And can have additional supporting branches such as `feature`, `hotfix` and `release`.
- ***GitHub Flow*** | Works around the rule that the `main` branch is **always** deployable. As such, you'll make a new branch from the `main` branch relevant to work you are doing. Review, discuss and merge back into `main` when ready to do so.
- ***GitLab Flow*** | Trunk-based using `feature` branches. Test all commits to ensure code integrity, not just on `main`. Code Reviews on merge requests.

I'll be honest and note I've never really followed one of these explicitly, as such I've found I tend to follow a mix of Git Flow and GitLab Flow aspects together. For the sake of simplicity as this is *Getting Started* we'll keep with a typical ***Git Flow*** workflow. Feel free to read up on the many other types of workflows out there and maybe you'll have some feedback on a better choice for your team! An example diagram of ***Git Flow*** is as below (from [GitKraken]() originally):

<div style="text-align: center;">

![Git Flow Example Diagram](/Workshops/images/2.1_GitFlow.png)

</div>

 Since we're keeping it simple, we are going to focus purely on having a primary `main` branch that we treat as containing only production ready code. A `dev` branch in which all changes are made, whether directly or via `feature` branches to add new *features*. And finally mocking a code review for a pull request to merge the `dev` updates into `main`.

## Basic Git

But Chris, what does it all *mean*? I hear you ask. So to try and break it down simply to the way I learnt. We utilise a repository to store not only our code, but also a list of all changes made to that code in the form of `commits` in which the changes between each commit are visible, highlighted and commented (with commit messages) indicating the changes purpose. This helps keep an incredibly handy history for all changes made to the codebase, by who, when and why. And in doing so allows us to quickly and easily roll back to prior last known working versions. There is, of course, so so much more to it than that, but at it's core this is how I have always treated it. Utilising the workflow, on top of this, is what helps keep things nice and tidy.

Given we're assuming this hasn't been done before, one of the first things you need to do is configure git in your environment. There are a myriad of options available for this, however we will purely focus on the most basic ones we need to get started. You're more than welcome to configure a custom `~/.gitconfig` with your own setup if you know how! From the command line we want to start by giving a global username and email associated, do note however, you can very much configure this on a single repository only instead of globally, this helps if you have different details for different repos. We achieve this by typing the following :

```git
git config --global user.name "Korthal Maiyn"
git config --global user.email "email@example.com"
```

Now if we didn't have a repository in ***Azure DevOps*** already, we would use `git init` to create our own new local git repository that we could then push to our remote later on. However, since we are going to use this Repository as an example, you'd instead use `git clone` to clone the contents (pre-existing branches and all) of the repository down to your local machine. This essentially means each team member keeps a copy of the entire repository local in their environment to work on where required.

You continually keep your local repo up to date by using both a `git fetch` and `git pull` prior to making any changes. You will start with a `fetch` against the primary repository (in our case the ***Azure DevOps*** repo.) which will check if there are any remote commits that you should incorporate into yyour local changes, that is, changes made by your team mates that you want to ensure you have a copy of to verify. If things look good, `pull` those changes down to your local so you can ensure you have the most up to date version of the repository. This also helps to prevent merge conflicts, which we won't go over today.

Once you're happy with your changes and `commits` you've made locally, you need to `push` those changes from your local up to the remote repository so as that your team members can see these changes and act accordingly. There is also `sync` which effectively does a pull and push simultaneously.

So, we know that a repository will contain multiple branches that dictate where we work and for what reason. But what else? What do these things mean?

- `git config` | Used to set configuration details for git either globally or on individual repositories.
- `git init` | Initialises a new repository locally. One way to start a new project by initialising the git repository locally by yourself. Then you can push this up to a remote repository.
- `git clone` | Also initialises a new repository locally, howevever by cloning a pre-existing repository that already exists down locally.
- `git checkout` | Used to switch between / checkout the different branches within the repository, including creating new branches to work with such as new `feature` branches or `hotfixes`.
- `git commit` | When you have finished making changes and have saved your file you will want to `commit` those changes to Git. This means it is treated as a snapshot of the changes made to the file(s) at the point in time the `commit` was made. This is our history of changes that we have the facility to look back on.
- `git fetch` | Fetches changes to the remote repository different to your local changes. If these exist, you should `pull` to help prevent upstream merge conflicts.
- `git pull` | Pulls the latest version of the remote repository down locally to ensure you have the most up to date changes.
- `git push` | Takes the changes and `commits` you have made and pushes them up to the remote repository so as that people can view the changes made.
- `git sync` | simultaneously runs a `pull` and `push`
- `pull request` | This will be covered in more detail below, but effectively a request to merge one branch into another branch. i.e. `dev` into `main` once development changes have been completed.

Whilst I tend to use the git tools within ***Visual Studio Code*** for my `commits` and syncing to and from the repository, kowing that you can use these git commands in the command line may be your preference! In any case, it's wise to know exactly *what* each of the different types of commands do and how to use them. There are so many available options, flags and different commands you can use with Git. Have a look through the documentation and see if you can cobble together a slightly improved `.gitconfig` file where you've set some of your own aliases.

## Git in Visual Studio Code

So, as noted above, I tend to use the in-built git functions, with the help of some of those Extensions we installed, to manage my git workflow. Obviously it comes down to what you're most comfortable with, and I do tend to use a mixture of both CLI commands and ***Visual Studio Code*** as well, depending on what I'm looking to do. To keep things nice and simple without feeling overwhelmed, I find it nice to start with the ***Visual Studio Code*** implementation to get a good base idea that you can begin experimenting with the CLI as you find yourself becoming more comfortable using git.

Let's assume you've already used `git clone` or `git init` on your project already so it's ready for version control. If you want to use ***Visual Studio Code*** to edit your code, there's many ways to open the repository. One I like to do is within our ***WSL2 Ubuntu*** environment you can `cd` (change directory) to where your repository is located. Once you're at the top level (which you can easily determine by the location of the .git folder generally) you can type `code .` to open the directory as a whole within ***Visual Studio Code***. But feel free to play around with the different ways to get your project into ***Visual Studio Code*** and use what you feel most comfortable with!

We'll use this particular Project as an example, you can start by selecting the `Source Control` item from the left hand menu. This will throw out a sidebar full of a bunch of different panels relating to your git repository. It should, realistically, look similar to the below.

<div style="text-align: center;">

![Visual Studio Code Source Control](/Workshops/images/2.2_VSCodeSourceControl.png)

</div>

The main panel I tend to pay attention to is the `Changes` panel to keep track of which files I have made changes to and how they compare to previous `commits`. But as you can see, there is a lot of information available across all the different panels. Which `Branches` are on the repository? Which `Repositories` are here? What is the history of `Commits`? Just... Loads of information. To keep it simple, we'll primarily focus on the changes tab.

Okay cool, we've made a couple of changes to our local repository and we'd like to now `commit` those changes. Now, you can realistically do whatever you want for your `commit`, whether you decide to include a message or not is up to you. However, I tend to follow the ***Conventional Commits*** specification, purely because it is both widely adopted and helps to ensure human readable meaning to your `commit messages`. I highly suggest giving the [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/) documentation a read over to get a base understanding, if you remember we installed the ***Conventional Commits*** Extension earlier on so that will make following this specification much easier. For reference, you should try to always put a relevant message on your `commits` and by keeping your `commits` to a specific change, you can ensure each message is relevant to those changes and available for everyone in the team to see at a quick glance *what* the change was for (e.g. fix: feat: etc.) and a good message indicating it in further detail. Not only that, but it makes documentation of the Project so so much easier.

The first thing we want to do is `stage` our changes, this is effectively preparing our file for a commit, essentially adding the file to git's version control, but it not yet being commited, which comes next. This is achieved with the `git add` command within the CLI. Within ***Visual Studio Code*** and the *Source Control* tab simply hover over your Changes and you should see a little **+** icon, hit this to Stage your changes. The inverse is true also, once they are staged you can hit the **-** icon to remove them from being staged.

<div style="text-align: center;">

![Git Stage](/Workshops/images/2.3_StageChanges.png)

</div>

Once we've `staged` only the relevant changes we want to `commit` (remember, above, we want to group together and `stage` and `commit` like minded changes) we can then look to add a message and `commit` then `sync` these changes up to our remote repository! Now you could absolutely use that little `Message` box above the Staged Changes to enter a typical `commit` message. You can also achieve this in the CLI altogether with `git commit -m "Message Goes Here"` or even not add one at all (don't do that...). However, we're going to use the ***Conventional Commits*** Extension to help us structure and format our `commits` in a nice easy to read and understand manner. We want to start by hovering over the **Source Control** panel and you should see a small circle icon in the middle, and hovering over this will tell you that it is ***Conventional Commits***. Hit this and a little popup window should appear in the centre of your ***Visual Studio Code*** with a heading of **1/5**.

<div style="text-align: center;">

![Conventional Commits](/Workshops/images/2.4_ConventionalCommits.png)

</div>

The first page you're presented with asks you to select the type of change, these are all pretty well explained on-screen. We'll select `docs` for this as we are updating our Documentation. The next stage will ask you to select the `scope` of the change. This will, currently, be empty aside from the three (3) base options of None, New Scope and New Scope (only use once). Or if you have grabbed the `.vscode/config` files, you may see a few extras for different scopes I have put together during my creation. The `scope` helps us determine at which level the changes are being made, however in this instance we can simply select `None` for now.

You are then asked to provide a short, imperative tense description of the change you're committing. As an example, we'd say `Updated Workshop 1` as that's what we've done. The next part asks us to provide a longer, more detailed description of the change. Here we would add something like `Added sections on Git in Visual Studio Code to Workshop 1 Document.`. If you're using an agile methodology or have a system in place that is tracking changes or incidents, the final section allows you to reference these here. This will very much differ from company to company and system to system as to the types of indicators you would include here, for now we can simply leave it blank.

Finally, once that's done the message and ***Conventional Commmits*** structure will be added to the `commit` and we can well... `commit` it. Within Visual Studio Code just hit the little &#10004; icon to `commit`. You'll generally be presented with a confirmation box, but for the most part this should hopefully then present an option to `sync` your `commits` up to the remote repository so the rest of your team can view your changes and `pull` them locally as required!

<div style="text-align: center;">

![Time to Commit!](/Workshops/images/2.5_Commit.png)

</div>

Congratulations, you've just started working collaboratively on a code base by using git and the ***Git Flow*** workflow! Next we're going to talk about ***Code Reviews*** including pull requests! You can verify your changes by checking the Repo within ***Azure DevOps*** where it should show your recent `commits` listed. Have a play around and see if you can figure out how to check the history or do comparisons between the original and the staged changes you have.

<div style="text-align: center;">

![Azure DevOps Repo](/Workshops/images/2.6_DevOpsRepo.png)

</div>

# Pull Requests

Cool, so now you've made your changes to the `dev` branch with those fun little `commits` you've been working on. But what now? Well given we are following the ***Git Flow*** workflow, we would look to merge the changes we've made to `dev` into our `main` production ready branch. You generally accomplish this by creating a `pull request`. As the name implies, you are requesting to `pull` the changes made to your `dev` branch into `main`, and it is explicitly a request as this is where you'll have some processes and checks in place to ensure that the changes you are submitting to `main` won't break the production environment.

There are options within ***Visual Studio Code*** however, as we are using ***Azure DevOps*** I feel it would be helpful to get a feel for the process when done via the web portal as well. Let's imagine that we have set up the relevant policies that require us to have at least one ***Code Review*** by a member of our team prior to approving and processing the `pull request`. Start by logging in to ***Azure DevOps*** and navigating to your `Project -> Repos -> Files` where you should see a layout much like the below.

<div style="text-align: center;">

![Azure DevOps Repo](/Workshops/images/3.1_PullRequest.png)

</div>

You'll notice that we're currently on the `main` branch (as highlighted) but that there is an indication that the `dev` branch has been recently updated and a button to **Create a pull request** to merge these two together. You can realistically process these at any point, or you can make a whole bunch of `commits` and then merge these with a `pull request` when you have a couple of relevant `commits` compiled together. This helps with the `pull request` as you have a fairly solid history of the changes made from the current `main` working branch to the proposed changes to merge.

When you create a **New pull request** there will be a few sections and tabs to go over. Directly under the header tells you from which branch into which branch. You can change these to match whatever your use case is, but for here we'll focus on `dev into main`. Then there is the *Overview* section of the `pull request` where you give it a relevant title name and description going over exactly what changes are being pulled into the `main` branch. You'll have a list of *Reviewers* here, as noted above, assuming we have at least one (1) required as a policy, but as it shows we can have multiple people choose to review it as well as certain people who may be explicitly required to review the changes before approving the merge into production.

<div style="text-align: center;">

![Azure DevOps Pull Request](/Workshops/images/3.2_PullRequest.png)

</div>

Then you can link work items from your boards (you should if you're using these) to help track which requests match which work items as well as any relevant Tags for easy reference later on. If you navigate between the different Tabs you can also see **Files** which will show you the list of Files that were changed for this `pull request` including the changes made to each of them. As well as the **Commits** tab which will show you a sequential list of the `commits` made, by who and the ***Conventional Commits*** message associated.

Hitting Create will then create a new `pull request` for the team to ***Code Review***!

## Code Reviews Comments and Collaboration

Now we've got a `pull request` is where the collaboration aspect comes in. As noted previously, you can have both optional and required reviewers to go over your code. Your team should generally have visibility of the `pull request` and as such have the facility to add comments / suggestions on improvements or enforcing standarisations prior to approving the merge into the `main` branch.

In a basic example below you can see a couple of comments added in different locations. You can also see highlighted up the top that you have the facility to resolve these comments prior to Approving and Completing the `pull request`. These comments on the **Overview** tab can be filtered from the Filter on the right to what you want to see.

<div style="text-align: center;">

![Pull Request Comments](/Workshops/images/3.3_PullRequestComments.png)

</div>

From these comments above, one was created on the `pull request` **Overview** tab itself as a comment against the entire request. The second is a comment on a specific line of code, usually a change, to provide feedback or questions as to the purpose of changes to the codebase. To add you simply navigate to the Files tab, read through the different file changes, if you have a comment to add simply locate the line in the file that was changed you want to comment on and you will see a little *speech bubble* to indicate adding a comment. Click on this, add your comment and await your reply! These can then be resolved / updated as appropriate, including discussion chains relevant to this change.

Keeping all your comments regarding these changes in the same Source Control system helps keep everything documented from start to finish. If discussions regarding changes are had outside of the system (say in Teams or on calls) they should be updated here as well to reflect those discussions and as such the documentation surrounding those changes where appropriate. Correctly versioned with a long term history that is always visible for anyone new to the codebase.

<div style="text-align: center;">

![File Comments](/Workshops/images/3.4_FileComments.png)

</div>

As you continue to work together as a team and collaborate over the `pull request` changes, you can continue to `commit` updates to reflect that collaboration as you normally would. The **Updates** tab will keep a list of these `commits`, including those made after the `pull request` was created. This helps to determine which changes were made after the request and if they have been commented appropriately, should reference the discussions within the `pull request` itself. This is a really good way to help keep track of what additional changes have been made and what comments / discussions they reference within the `pull request` as well as the facility to jump directly to those latest changes.

<div style="text-align: center;">

![File Comments](/Workshops/images/3.5_Updates.png)

</div>

Once your team and the Project Manager / Project Owner are happy with the changes made, including those made during the `pull request` ***Code Reviews*** collaboratively, those listed reviewers (both optional and Required) should ensure they have approved the `pull request` and thus approve to merge those changes from `dev into main`.

# Merging

Once you've got that approval it's time to **Complete** the `pull request` by merging from `dev into main`, there are of course a whole bunch of additional details regarding things like **Branch Policies** and whether or not they are passing or failing for the `pull request` but for the most part we will ignore that as it is outside of the scope of this basic getting started workshop. When you hit **Complete** you're presented with a *Complete Pull Request* flyout on the right hand side of your browser which will ask you to provide the Merge type, and additional post-completion options. Play around with the different Merge Types on the flyout as the little diagram underneath can help you to understand the purpose.

- **Merge (no fast forward):** Merge with a non-linear history that preserves all commits.
- **Squash commit:** Merge with a linear history that combines all source commits into a single commit on the target, or squash merges the PR.
- **Rebase and fast-forward:** Rebase the source commits onto the target and fast-forward.
- **Semi-linear merge:** Rebase source commits onto the target and create a two-parent merge.

The Policies mentioned above can be applied to these, such as a branch maybe containing a `squash merge only` policy. However we will ignore these for now and instead purely use a ***Merge (no fast forward)***. The options underneath for post-completion are fairly self explanatory. Depending on the type of workflow you are using may determine whether or not you delete the branch for example. However items such as **Complete associated work items after merging** make sense, unless you have a separate policy in place for this.

- **Complete associated work items after merging:** Complete any linked work items.
- **Delete <branch name> after merging:** Delete the PR's source branch after merging.
- **Customize merge commit message:** Add a custom merge commit message. If you select this option, update the merge commit message.
- **Override branch policies and enable merge:** Force the merge even if the PR doesn't satisfy all branch policies. This option is only available if you have Exempt from policy enforcement permission.

<div style="text-align: center;">

![Complete Pull Request](/Workshops/images/3.6_Merging.png)

</div>

And just like that, you've successfully worked collaboratively on a `pull request` and then merged those changes into the `main` production branch! Remember, the way in which you proceed through these kinds of actions is very much determined by the type of git workflow you are using. There is a *lot* of flexibility here on how things are done and a lot of it comes down to what works within the team and which processes can be easily employed vs those that may not be able to.

# Helpful Resources

The bulk of the above was collated from a mixture of experience and research from multiple sources. For a collation of helpful official resources I have used and reference often for these items, see below. There are also countless 3rd party blogs and videos out there for you to consume :

#### WSL2

- [Windows Subsystem for Linux Documentation](https://docs.microsoft.com/en-us/windows/wsl/)
- [Install WSL](https://docs.microsoft.com/en-us/windows/wsl/install)
- [Set up a WSL development environment](https://docs.microsoft.com/en-us/windows/wsl/setup/environment)
- [Ubuntu on Windows](https://www.microsoft.com/en-au/p/ubuntu-on-windows/9nblggh4msv6?activetab=pivot:overviewtab)
- [Get started with the Windows Subsystem for Linux](https://docs.microsoft.com/en-us/learn/modules/get-started-with-windows-subsystem-for-linux/)
- [Get started with the LInux command line and the Shell](https://docs.microsoft.com/en-us/learn/paths/shell/)

#### Visual Studio Code

- [Visual Studio Code](https://code.visualstudio.com/download)
- [Get started using Visual Studio Code with Windows Subsystem for Linux](https://docs.microsoft.com/en-us/windows/wsl/tutorials/wsl-vscode)
- [Visual Studio Code Keyboard Shortcuts for Windows](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)
- [Visual Studio Code Extensions Marketplace](https://marketplace.visualstudio.com/VSCode)

#### SSH Keys

- [Azure DevOps - Use SH key authentication](https://docs.microsoft.com/en-us/azure/devops/repos/git/use-ssh-keys-to-authenticate?view=azure-devops)
- [Generate SSH Keys on Windows 10](https://ubuntu.com/tutorials/ssh-keygen-on-windows)
- [Key generation with Ubuntu on WSL](https://ubuntu.com/tutorials/ssh-keygen-on-windows#3-key-generation-with-ubuntu-on-wsl)
- [Sharing SSH keys between Windows and WSL 2](https://devblogs.microsoft.com/commandline/sharing-ssh-keys-between-windows-and-wsl-2/)
- [Azure DevOps - SSH Keys are of a deprecated type](https://github.com/MicrosoftDocs/azure-devops-docs/issues/11904)

#### Git

- [AZ-400 Work with Git for enterprise DevOps](https://docs.microsoft.com/en-us/learn/paths/az-400-work-git-for-enterprise-devops/)
- [Git Flow](https://www.gitkraken.com/learn/git/git-flow)
- [A successful Git branching model](https://nvie.com/posts/a-successful-git-branching-model/)
- [GitHub Flow](https://www.w3schools.com/git/git_github_flow.asp?remote=github)
- [GitLab Flow](https://about.gitlab.com/solutions/gitlab-flow/)
- [First-Time Git Setup](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup)
- [Use git fetch, pull, push and sync for version control in Visual Studio](https://docs.microsoft.com/en-us/visualstudio/version-control/git-fetch-pull-sync?view=vs-2022)
- [Use Git version-control tools in Visual Studio Code](https://docs.microsoft.com/en-us/learn/modules/use-git-from-vs-code/)
- [Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)
- [Azure DevOps Create Pull Requests](https://docs.microsoft.com/en-us/azure/devops/repos/git/pull-requests?view=azure-devops&tabs=browser)
- [Azure DevOps Complete Pull Requests](https://docs.microsoft.com/en-us/azure/devops/repos/git/complete-pull-requests?view=azure-devops&tabs=browser)

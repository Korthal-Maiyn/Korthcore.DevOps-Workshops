# Workshop 1 : Getting Started

The aim of this workshop is to run through the basics of how to get started, including some incredibly relevant links for additional resources, and a small excercise to get you going. A lot of the content within will be a very high overview of processes, tools etc to help get you started, but please be aware there are many *many* different ways to tackle this, as such it is entirely plausible some items in this you will very much have a working knowledge of already, but don't worry this is merely a very simplistic getting started guide to help you on your journey. So with this in mind, let's jump straight into it!

## Contents

1. [Setting Up Your local Environment](#Setting-Up-Your-Local-Environment)
    - [Getting Started With WSL2](#Getting-Started-With-WSL2)
    - [Configuring an IDE](#Configuring-an-IDE)
        - [Starter Visual Studio Code Extensions](#Starter-Visual-Studio-Code-Extensions)
    - [Configuring SSH (Optional)](#Configuring-SSH-(Optional))
2. [Source Control Management and Git](#Source-Control-Management-and-Git)
    - GitFlow
    - Basic Commands
    - Visual Studio Code Usage
3. Code Reviews
    - Comments
    - Pull Requests

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

### First Steps Withing Ubuntu

Now that you have your sudo user credentials configured, the first thing you should always look to do is update and upgrade the packages pre-installed on ***Ubuntu*** to ensure they have been updated to the latest version, this includes Git which comes pre-installed on most Linux Distributions. Once you've got your Ubuntu Terminal in front of you, simply type `sudo apt update && sudo apt upgrade` and you'll have everything updated appropriately. You should look to do this regularly, I like to this every time I fire up the Distribution to ensure things are kept up to date.

## Configuring an IDE

Now, as above with Distros, there are countless IDE's available that you can choose to use and you may in fact already have a favourite you use daily. However, in order to keep things standardised we are going to talk about ***Visual Studio Code*** specifically as this has fantastic integration with WSL but also a myriad of Extensions available to help with your workflow. There are really two main parts to this, installing ***Visual Studio Code*** and utilising an environment configuration to standardise configs across the board.

Doesn't need much explanation but either head to [https://code.visualstudio.com/Download](https://code.visualstudio.com/Download) and download the latest version applicable for your system *or* if you've still got PowerShell as Admin open, simply type `winget install **Visual Studio Code**` to use the Windows Package Manager to install ***Visual Studio Code*** from the command line.

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

I will be using **Azure DevOps** within this training excercise, there are some caveats. Namely that, at the time of this writing, there is only really **good** support for using a typical *RSA* SSH key type. Whilst this is, realistically more than adequate, the *RSA* SSH keys are technically less secure than using the newer *ED25519* SSH key type, so make sure to at least use a key size of 2048 bits when generating *RSA* SSH keys. Maybe one day specific support may come for ***Azure DevOps***, however as it stands we will focus on the *RSA* SSH key type. As above, if you're feeling adventurous, why not try configuring an *ED25519* SSH key with a provider such as GitHub for a personal Repository to play with. Or maybe try and find some of the workarounds that exist to utilise *ED25519* encryption within ***Azure DevOps*** instead (yes, it is somewhat possible!). All of this will help understand the security and provisioning of access to Repositories outside of a standard GUI logon.

Open up your Linux Distro command line interfact and simply type `ssh-keygen -C "username@domain.com"` to generate a new *RSA* SSH key-pair. Leaving no options on `ssh-keygen` will, by default, create a 2048 bit *RSA* key-pair. You will then be prompted to choose a location to save this, just leave the default as this is pretty standard (this is almost always /home/<username>/.ssh/id_rsa). You can, if you so choose, add a passphrase to make your key more secure, however for this particular Workshop that is not necessary. If all goes to plan you should have an output similar to below! *Note: I have explicitly used a different location as I have an id_rsa key-pair already and do not want to overrite this.*

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

Now we need to paste this Public Key into your ***Azure DevOps*** Organisation. Obviously start by logging in to your [Azure DevOps Organisation](https://dev.azure.com/) and once you are logged in, select your **User Profile** icon up the Top Right (Step 1). From the subsequent dropdown menu select **Security** (Step 2). And finally select the **SSH public keys** menu item from the left hand menu. Unless you've set this up previously, you should be presented with an empty list.

<div style="text-align: center;">

![RSA SSH Public Key Output](/Workshops/images/1.4_SSHPublicKeys.png)

</div>

Hit **+ New Key** up the top right, give it a name that makes sense to you (so as that you know where the Private Key for this Public Key is stored, usually the Computer Name is a good start) and paste the previously copied Public Key into the *Public Key Data* field below. Congratulations! You've just configured SSH Authentication for ***Azure DevOps***. You can verify this by selecting the newly added key and verifying the data matches what you have input. It should look much like the below.

<div style="text-align: center;">

![RSA SSH Public Key Output](/Workshops/images/1.5_SSHKeyData.png)

</div>

*Note: The details above have already been deleted after screenshots were taken. Images for informational purposes only.*

# Source Control Management and Git


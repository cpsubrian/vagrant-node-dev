# Vagrant Box ready for node development

This is a vagrant box based off of the lucid64 box.

It includes:

  - nvm: 
    - node.js v0.4.12 and v0.6.0 (default) installed
  - npm
  - redis 2.4.2
  - mongodb 2.0.1
  - git 1.7.0.4
  
# How to use

1. Install Vagrant 
  - http://vagrantup.com/docs/getting-started/index.html
2. Create the directory where you want the vm to live and `cd` to it.
3. Git clone, or download, this Vagrantfile and put it in the directory.
5. `$ vagrant up`
  - This will take a while, as it needs to download the box (>700 MB).
    When this command finishes the machine is ready to use.
6. `$ vagrant ssh` will give you shell access to the machine.
  - In windows you'll need to follow the instruction to set up
    a PuTTY key.
7. Once you are shelled into the machine, you need to setup an ssh keypair.
  - `$ ssh-keygen -t rsa -C "your_email@youremail.com"`
8. Identify yourself to git
  - `$ git config --global user.name "Your Name"
  - `$ git config --global user.email "your@email.com"
9. Now reload the bash profile so keychain will pick up your keypair.
  - `$ source ~/.bashrc`
10. Now you probably want to add your pub key to your github account.
  - You can find the key in `~/.ssh/`
  - Test your key: `$ ssh -T git@github.com`
11. Enjoy!

# Shared folder

By default Vagrant sets up a 'root' shared folder for you.  On the host
machine it will be wherever you ran `vagrant init` in step 4 above.

I have set up an symlink (for convenience) at `~/shared` that points 
to the location of the shared folder on the guest VM.

# Forwarded ports

The Vagrantfile I packed with this box sets up some common forwarded
ports used by node apps.  Ports `3000-3009` and `8080` are forwarded from the
guest machine to the host.  You can forward more ports.  Read the 
Vagrant documentation to find out how.

# Vagrant commands

From the Vagrant docs:

    $ vagrant
    Usage: vagrant SUBCOMMAND
            --help                       Show help for the current subcommand.
            --version                    Output running Vagrant version.

    Supported subcommands:
            box                 Box commands
            destroy             Destroys the vagrant environment
            halt                Halts the currently running vagrant environment
            init                Initializes current folder for Vagrant usage
            package             Packages a vagrant environment for distribution
            provision           Run the provisioner
            reload              Reload the vagrant environment
            resume              Resumes a suspend vagrant environment
            ssh                 SSH into the currently running environment
            ssh-config          outputs .ssh/config valid syntax for connecting to this environment via ssh
            status              Shows the status of the Vagrant environment.
            suspend             Suspends the currently running vagrant environment
            up                  Creates the vagrant environment

    For help on a specific subcommand, run `vagrant SUBCOMMAND --help`


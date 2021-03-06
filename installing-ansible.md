---
layout: top-level
title: Installing Ansible
prev: '<a href="key-concepts.html">Prev: Key Concepts</a>'
next: '<a href="preparing-a-computer.html">Next: Preparing A Computer For Ansible</a>'
---

# Installing Ansible

## Where Do You Install Ansible?

Ansible gets installed onto your computer: your desktop and/or laptop.  You'll run it from there to provision your own computer, or other computers over your network via SSH.

## Do You Need A Server For Ansible?

You don't need to set aside a server to install Ansible onto.  Unlike alternatives, Ansible doesn't need a central server or central database at all.  Instead, Ansible reads all of its configuration from files stored in the [playbook repo](key-concepts.html#playbook_repo).

If there are several of you who share responsibility for managing a set of servers, each of you can run Ansible from your own computers, and share your Ansible playbook repo via source control.

<div class="callout info" markdown="1">
#### Perfect For Developers

One of the reasons Ansible is becoming popular amongst developers is that there's no central infrastructure to setup and maintain.  Just clone the software repo where you store your Ansible playbook, and run Ansible from the comfort of your own computer.
</div>

## How Do You Install Ansible?

I recommend that you always install Ansible from [source](https://github.com/ansible/ansible).  Ansible is currently fast-moving, and grabbing the latest version will give you the latest bug fixes and features.  (As a rule of thumb, the official documentation always describes the very latest version).

First, install Python's YAML extension:

<pre>
# Ubuntu, Debian
sudo apt-get install python-yaml
</pre>

Then, install Python's Jinja2 templating library:

<pre>
# Ubuntu, Debian
sudo apt-get install python-jinja2
</pre>

Then, if you don't have it already, install Git:

<pre>
# Ubuntu, Debian
sudo apt-get install git
</pre>

Finally, install Ansible from Github:

<pre>
# Ubuntu, Debian
git clone https://github.com/ansible/ansible.git
cd ansible
sudo python setup.py
</pre>

Ansible is now ready to run from your computer.

Before you can use Ansible, you need to prepare each computer that Ansible is going to provision.  I'll show you how to do that in the next chapter.

## Upgrading Ansible

[You'll want to upgrade Ansible reguarly](key-concepts-html#ansible_versioning) to get access to the latest modules and to catch any backwards-compatibility breaks in your playbooks.

Upgrading is very simple:

1. Check [the official AnsibleWorks install docs](http://docs.ansible.com/intro_installation.html) to see if there are any new dependencies you need to install, then
2. Re-clone the Ansible git repo and run `sudo make install` inside it again
3. Re-run your playbooks to make sure that they still work

If any of your playbooks have stopped working, check [the Ansible changelog](https://github.com/ansible/ansible/blob/devel/CHANGELOG.md) first to see if there are any useful pointers to your problem.  I look at [debugging failing roles](debugging-failing-roles.html) later in this book.

<div class="callout warning" markdown="1">
#### Remember To Tell Everyone To Upgrade Ansible

If there are several of you using Ansible, you'll all need to upgrade at the same time.  Different people using different versions of Ansible can be a cause of unexpected playbook errors.
</div>
# Plan of a presentation

<input type="checkbox" unchecked>Brand new format of a presentation</br>
<input type="checkbox" unchecked>Why?</br>
<input type="checkbox" unchecked>Ansible</br>
<input type="checkbox" unchecked>Vagrant</br>
<input type="checkbox" unchecked>Live demo (Vagrant + Ansible)</br>

# Ansible
- What is Ansible?
  - Ansible is powerful IT automation that you can learn quickly. It's simple enough for everyone in your IT team to use, yet powerful enough to automate even the most complex deployments. Ansible handles repetitive tasks, giving your team more time to focus on innovation.
- Ansible use cases
  - https://www.ansible.com/use-cases
  - Provisioning
    - Your apps have to live somewhere. If you’re PXE booting and kickstarting bare-metal servers or VMs, or creating virtual or cloud instances from templates
  - Configuration management
    - Centralizing configuration file management and deployment is a common use case for Ansible, and it’s how many power users are first introduced to the Ansible automation platform.
  - Application deployment
    - When you define your application with Ansible, and manage the deployment with Ansible Tower, teams are able to effectively manage the entire application lifecycle from development to production.
  - Continuous delivery
    - Creating a CI/CD pipeline requires buy-in from numerous teams. You can’t do it without a simple automation platform that everyone in your organization can use. Ansible Playbooks keep your applications properly deployed (and managed) throughout their entire lifecycle.
  - Security automation
    - When you define your security policy in Ansible, scanning and remediation of site-wide security policy can be integrated into other automated processes and instead of being an afterthought, it’ll be integral in everything that is deployed.
  - Orchestration
    - Configurations alone don’t define your environment. You need to define how multiple configurations interact and ensure the disparate pieces can be managed as a whole. Out of complexity and chaos, Ansible brings order.

- My own understanding
  - Need to do something remotely by SSH?
  - Need to automate sophisticated lifecycles on remote boxes?
  - Need to test the designed *play* on a virtual machine?
  - Need to have idempotent / debuggable / reproducible scripts?
  - Need to test something on a fleed of heterogeneous boxes?
  - Need a simple and versionable way of doing some stuff on boxes?
  - Abstracts significant amount of complexity from DevOps / developers
  - It's NOT **Docker** 😊

## Pros
- AWESOME official documentation (one of the best I've ever seen)
  - http://docs.ansible.com
- The best quick start video I've ever seen
  - https://www.ansible.com/resources/videos/quick-start-video
- Pretty simple (remember *the devil is always in details*)
- YAML
  - Human readable syntax
  - Simple in design and in a nutshell (modules, plays, playbooks)
- Agentless
  - With Ansible you can start to do real work in just minutes due to its simple, human-readable language. Altogether its powerful capabilities allow orchestration of your entire application lifecycle regardless of where it’s deployed. And Ansible’s agentless architecture means it is one less thing to keep secure. 
- HUGE community
- Loads of books / video courses / articles
  - ⚠ **Ansible for DevOps** by Jeff Gerling
  - ⚠️ **(100% FREE)** Jeff's YouTube video course
    - https://youtu.be/goclfp6a2IQ
  - Jeff's blog
    - https://www.jeffgeerling.com/blog/2020/ansible-101-jeff-geerling-youtube-streaming-series
  - Medium
  - HackerNews
  - **Mastering Ansible** by Jesse Keating

## Cons
- Not that simple
- The package repositories are NOT 1000% reliable (cannot download a package for CentOS twice in 20 min)
- yum --> package

## Ansible architecture
- https://docs.ansible.com/ansible/latest/dev_guide/overview_architecture.html#ansible-architecture
- Modules
  - Ansible works by connecting to your nodes and pushing out scripts called “Ansible modules” to them. Most modules accept parameters that describe the desired state of the system. Ansible then executes these modules (over SSH by default), and removes them when finished. Your library of modules can reside on any machine, and there are no servers, daemons, or databases required.
- Plugins
  - Plugins augment Ansible’s core functionality. While modules execute on the target system in separate processes (usually that means on a remote system), plugins execute on the control node within the /usr/bin/ansible process. Plugins offer options and extensions for the core features of Ansible - transforming data, logging output, connecting to inventory, and more. Ansible ships with a number of handy plugins, and you can easily write your own. For example, you can write an inventory plugin to connect to any datasource that returns JSON. Plugins must be written in Python.
- Inventory
  - By default, Ansible represents the machines it manages in a file (INI, YAML, and so on) that puts all of your managed machines in groups of your own choosing.
- Playbooks
  - Playbooks can finely orchestrate multiple slices of your infrastructure topology, with very detailed control over how many machines to tackle at a time. This is where Ansible starts to get most interesting.

## Features
- Vault
```
# Run to encrypt the file with a secret (e.g. DB password)
$ ansible-vault encrypt secrets/db_password.yml
$ ansible-vault decrypt secrets/db_password.yml
$ ansible-vault edit secrets/db_password.yml
$ ansible-vault rekey secrets/db_password.yml

# Run the playbook and enter `test` as a key to Ansible Vault
# Enjoy the DB password value printed out
```

# Vagrant
TBD
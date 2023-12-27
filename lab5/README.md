# Lab: Learn IaC (Infrastructure as Code)

## Installation


1. Install VirtualBox - https://www.virtualbox.org/wiki/Downloads.
2. Install Vagrant on your computer - https://www.vagrantup.com/downloads.html.
3. (Optional) **On Windows**, ensure that Hyper-V is disabled:
  - Open a new PowerShell.
  - Run the following command:   
    ```bash
    Disable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V-All
    ```
4. Download the `centos/7` Vagrant box for the **Virtualbox provider**, run:
  ```bash
  vagrant box add centos/7
  ```
  
  It will output:
  
  ```bash
  ==> box: Loading metadata for box 'centos/7'
     box: URL: https://vagrantcloud.com/centos/7
  This box can work with multiple providers! The providers that it can work with are listed below. Please review the list and   choose
  the provider you will be working with.

  1) hyperv
  2) libvirt
  3) virtualbox
  4) vmware_desktop

  Enter your choice: 3
  ```



### Part 1. Imperative - Using Vagrant with Shell Provisioner.

Go to the [`lab5/part-1`](lab5/part-1) 
Run the command:

```bash
cd lab/part-1
```

Then : 

```bash
vagrant up
```

Try also other Vagrant commands that manage the VMs:

```bash
# will check VMs status
vagrant status 

# stop the VMs
vagrant halt

# will destroy VMs
vagrant destroy
```

### 3. Check that everything is ok by connecting to the VM via SSH

1. To enter inside the VM via SSH:

```bash
vagrant ssh
```

It will open a session in the VM and you can run any bash commands being inside the Linux VM (like `ls`, `pwd`, etc.) 

## Part 2. Declarative - GitLab installation using Vagrant and Ansible Provisioner 

We will install Gitlab on CentOS as described in [the official documentation](https://about.gitlab.com/install/#centos-7). You can try to repeat those steps manually one after another on the VM configured in part 1 of the lab. Usually, when we are installing first time a new software in a testing environment, we do it manually to test each step, and then, after clarifying all the installation processes we automatize it using tools like Vagrant and Ansible. 

We will use [`ansible_local` provisioner](https://www.vagrantup.com/docs/provisioning/ansible_local.html) what will install Ansible on [CentOS 7](https://www.centos.org/) Linux distribution virtual machine by [Vagrant](https://www.vagrantup.com/). So, you don't need Ansible on your host OS!

### 1. Prepare a virtual environment

Go to the [`lab/part-2`](lab/part-2) directory and take a look at the [`Vagrantfile`](lab/part-2/Vagrantfile) and at the YAML files [`playbooks/run.yml`](lab/part-2/playbooks/run.yml). To have more information how the `Vagrantfile` is configured follow this [Vagrant Guide](https://docs.ansible.com/ansible/latest/scenario_guides/guide_vagrant.html)

In the [`lab/part-2`](lab/part-2) directory, you will find:
- A `Vagrantfile` that defines the VMs to be managed by Vagrant (1 CentOS 7 VM named `gitlab_server` in our case)
- A `playbooks/` directory that contains Ansible playbooks to install GitLab and run health checks

### 2. Create and provision a virtual machine (VM)

Run the command:

```bash
vagrant up
```

It will take 5-10 min to install all the necessary software including required packages, GitLab instance, and databases.

### 3. Test the installation 

To test the installation of GitLab you can just open a URL in a browser and make sure it answers with any GitLab page (this is step 3 of the [GitLab installation doc](https://about.gitlab.com/install/#centos-7)).

So, open in your browser the URL - http://localhost:8080. If you see a GitLab sign in page, that means the VM is successfully provisioned.

You can log in by using the `root` username and a password that is randomly generated and stored in `/etc/gitlab/initial_root_password` inside the VM.

## Part 3. Declarative - Configure a health check for GitLab

1. Read the [GitLab Health Check doc](https://docs.gitlab.com/ee/user/admin_area/monitoring/health_check.html).

2. Run a health check using `curl`:
  - Connect to the VM using `vagrant ssh`.
  - Run the command:
    ```bash
    curl http://127.0.0.1/-/health
    GitLab OK
    ```

## Authors

Hugo Lafargue, Rodolphe Tellier
### Ghost Blog Development Environment
Use this Vagrant demo to show the value of small, lightweight, on-machine development.

#### Instructions
I wanted to keep requirements light. You will need the following prerequisites to run this demo:

* Vagrant 1.8 or higher
* Ansible 2.0 of higher (these playbooks use "become")

Once you have the required prerequisites installed on your machine, simply do the following:

```
your-machine@~ $ git clone
your-machine@~ $ vagrant up
```

Then connect to your machine at [http://192.168.236.10:2368](http://192.168.236.10:2368).

##### BOY backups
If you want to BYOB, make sure to copy the variables file located in `ghost-install/group_vars/all-sample.yml` to `all.yml`.

```
your-machine@~ $ cp ghost-install/group_vars/all-sample.yml ghost-install/group_vars/all.yml
```

Refer to [Vagrant Documentation](https://www.vagrantup.com/docs/) for more information.

#### Notes
This environment is intended to be similarly built/run to the [Official Ghost Dockerfile](https://github.com/docker-library/ghost). The point is to compare the benefits of Vagrant to Docker for developer workflow, pointing out the benefits of each solution.

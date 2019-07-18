Ansible Keylime
===============

[![Build Status](https://travis-ci.org/keylime/ansible-keylime.svg?branch=master)](https://travis-ci.org/keylime/ansible-keylime) [![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/keylime-project/community)

Ansible role to deploy [Keylime](https://github.com/keylime/keylime) against a Hardware TPM.

The role is currently configured to work with Fedora 29. Contributions are welcome,
should anyone wish to have this role provision other Linux distributions.

For details on using Keylime, please consult the
[project documentation](https://keylime-docs.readthedocs.io/en/latest/)

Usage
-----

Run the example playbook against your target remote host(s).

```
ansible-playbook -i your_hosts playbook.yml
```

Vagrant
-------

If you prefer, a Vagrantfile is available for provisioning.

Clone the repository and then simply run `vagrant up --provider <provider> --provision`

For example, using libvirt:

```
vagrant up --provider libvirt --provision
```

For example, using VirtualBox:

```
vagrant up --provider virtualbox --provision
```

Once the VM is started, vagrant ssh into the VM and run `sudo su - to
become root.

You can then start the various components using commands:

```
keylime_verifier
keylime_registrar
keylime_agent
```

WebApp
------

The web application can be started with the command `keylime_webapp`. If using
Vagrant, port 443 will be forwarded from the guest to port 8443 on the host.

This will result in the web application being available on url:

https://localhost:8443/webapp/

License
-------

Apache 2.0

Contribute
----------

Please do! Pull requests are welcome.

Please ensure CI tests pass!

Contributors
------------

* Luke Hinds (lhinds@redhat.com)
* Leo Jia (ljia@redhat.com )

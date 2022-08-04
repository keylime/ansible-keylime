# Ansible Keylime

[![Build Status](https://travis-ci.org/keylime/ansible-keylime.svg?branch=master)](https://travis-ci.org/keylime/ansible-keylime) [![Gitter chat](https://badges.gitter.im/gitterHQ/gitter.png)](https://gitter.im/keylime-project/community)

Ansible role to deploy [Keylime](https://github.com/keylime/keylime) with the [rust implementation of the keylime agent](https://github.com/keylime/rust-keylime) against
a Hardware TPM.

The role is currently configured to work with Fedora 35.

Contributions are welcome, should anyone wish to have this role provision other
Linux distributions.

For details on using Keylime, please consult the
[project documentation](https://keylime-docs.readthedocs.io/en/latest/)

## Usage

Run the example playbook against your target remote host(s).

```bash
ansible-playbook -i your_hosts playbook.yml
```

## Get started with Keylime

The best way to get started is to read the [Keylime
Documentation](https://keylime-docs.readthedocs.io/en/latest/), however if
you're keen to get started right away, follow these steps.

You first need to decide on if you will use the revocation framework, if
so you will need to install golang and set the following value in
`/etc/keylime.conf`

`ca_implementation = cfssl`

Alternately you can set `openssl` which has no other dependencies.

You now need to start the following services.

`# keylime_verifier`

`# keylime_registrar`

To run the agent, navigate to the rust-keylime directory and start the agent. 

`# RUST_LOG=keylime_agent=trace cargo run `

| Note: Keylime Agent requires a TPM active that the agent can take ownership on|
| --- |

You can now set up a use case, a good first scenario to try out would be [IMA
Integrity Monitoring](https://keylime-docs.readthedocs.io/en/latest/user_guide/runtime_ima.html)

For more detailed set up scenarios, see the [Keylime
documentation](https://keylime-docs.readthedocs.io/en/latest/user_guide/runtime_ima.html)

## WebApp

The web application can be started with the command `keylime_webapp`. If using
Vagrant, port 443 will be forwarded from the guest to port 8443 on the host.

This will result in the web application being available on url:

[https://localhost:8443/webapp/](https://localhost:8443/webapp/)

## License

Apache 2.0

## Contribute

Please do! Pull requests are welcome.

Please ensure CI tests pass!

## Contributors

* Luke Hinds (lhinds@redhat.com)
* Leo Jia (ljia@redhat.com )

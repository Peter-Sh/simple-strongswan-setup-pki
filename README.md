# Setup simple PKI for strongswan vpn

This ansible role helps to setup simple PKI for strongswan vpn based on easyrsa3.

I've made it for private usage, but decided to publish it to help my friends to setup vpn servers.

Use it on your own risk.

The work is based on this [post](https://habr.com/post/250859/) (russian).

## Installation

Create `requiments.yml` file or add this lines to existing file.

```
# req.yml
- src: git+https://github.com/Peter-Sh/simple-strongswan-setup-pki.git
  version: master
```

Install the role:
```
ansible-galaxy install -r req.yml
```

## Usage

Simple playbook example.

The example playbook will setup PKI infrastructure in /home/user/easy-rsa/easyrsa3/pki

One server certificate for `your.vps.domain.name` will be created.

Two user certificates for client1 and client2 will be created and exported to p12 format.

You can later add more certificates to clients list and rerun playbook.

```
- hosts: localhost
  roles:
          - role: simple-strongswan-setup-pki
            base_dir: /home/user/easy-rsa
            fqdn: your.vps.domain.name
            clients:
                    - client1
                    - client2
```

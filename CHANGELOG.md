# CHANGELOG

## v1.0.0

Creation of the Ansible iptables role.

**Functionalities:**

- Ensure to disarm **firewalld**.
- Ensure required packages are installed.
- Ensure the services **iptables** and **firewalld** are managed.
- Ensure the correct firewall rules are set persistently.

**Todo's (possibly):**

- Ensure `ip6tables` is also managed.

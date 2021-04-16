Ansible Role: systemd-journald
==============================

An Ansible role that configures **systemd-journald**.


Table of Contents
-----------------

<!-- toc -->

- [Requirements](#requirements)
- [Role Variables](#role-variables)
- [Dependencies](#dependencies)
- [Example Playbook](#example-playbook)
  * [Top-Level Playbook](#top-level-playbook)
  * [Role Dependency](#role-dependency)
- [License](#license)
- [Author Information](#author-information)


<!-- tocstop -->

Requirements
------------

- Ansible 2+


Role Variables
--------------

Role variables include all supported journald parameters as documented in detail at the [freedesktop.org website](https://www.freedesktop.org/software/systemd/man/journald.conf.html#).

Each variable has the `systemd_journald_` prefix, and is named for the parameter.  For example, the `MaxRetentionSec=` parameter maps to the `systemd_journald_maxretensionsec` role variable.

Because every parameter has a default, journald.conf starts completely commented out, until you choose to override a parameter default.

```yml
systemd_journald_maxretentionsec: '1month'
```


Dependencies
------------

None.


Example Playbook
----------------

Add to `requirements.yml`:

```yml
---

- src: idiv-biodiversity.systemd_journald

...
```

Download:

```console
$ ansible-galaxy install -r requirements.yml
```

### Top-Level Playbook

Write a top-level playbook:

```yml
---

- name: head server
  hosts: head

  roles:
    - role: idiv-biodiversity.systemd_journald
      tags:
        - systemd
        - systemd-journald

...
```

### Role Dependency

Define the role dependency in `meta/main.yml`:

```yml
---

dependencies:

  - role: idiv-biodiversity.systemd_journald
    tags:
      - systemd
      - systemd-journald

...
```


License
-------

MIT


Author Information
------------------

This role was created in 2020 by [Christian Krause][author] aka [wookietreiber
at GitHub][wookietreiber], HPC cluster systems administrator at the [German
Centre for Integrative Biodiversity Research (iDiv)][idiv].


[author]: https://www.idiv.de/groups_and_people/employees/details/eshow/krause-christian.html
[idiv]: https://www.idiv.de/
[wookietreiber]: https://github.com/wookietreiber

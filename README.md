ovv.calibre
=========

[![Build Status](https://travis-ci.org/ovv/ansible-role-calibre.svg?branch=master)](https://travis-ci.org/ovv/ansible-role-calibre)

Ansible role to install and configure [calibre-web](https://github.com/janeczku/calibre-web).

Dependencies
------------

The [pyslackers.python](https://github.com/pyslackers/ansible-role-python) role is required.

Requirements
------------

A Nginx installation is required. We recommend using [pyslackers.nginx](https://github.com/pyslackers/ansible-role-nginx).

Installation
------------

To install this roles clone it into your roles directory.

```bash
$ git clone https://github.com/ovv/ansible-role-calibre.git ovv.calibre
```

If your playbook already reside inside a git repository you can clone it by using git submodules.

```bash
$ git submodule add -b master https://github.com/ovv/ansible-role-calibre.git ovv.calibre
```

Role Variables
--------------

* `calibre_user`: Calibre-web running user (default to `calibre`).
* `calibre_group`: Calibre-web running group (default to `calibre`).
* `calibre_home`: Calibre-web home directory (default to `/home/calibre`).
* `calibre_upload_group`: Calibre-web upload directory group (default to `calibre_group`).

* `calibre_web_git_url`: Calibre-web git repository url (default to `https://github.com/janeczku/calibre-web.git`).
* `calibre_web_version`: Calibre-web git version (default to `master`).
* `kindlegen_version`: Kindlegen version (default to `2_9`).

Example Playbook
----------------

```yml
- hosts: calibre
  vars:
    nginx_sites:
      calibre:
        locations:
          - location: /
            proxy_pass: http://127.0.0.1:8083
  roles:
    - ansible-role-calibre
    - pyslackers.nginx
```

License
-------

MIT

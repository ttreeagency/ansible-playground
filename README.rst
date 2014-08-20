******************
Ansible Playground
******************


In my company, ttree.ch, we are currently planning to move to Ansible
for our configuration management. This repository contain so of our
current playbook. Those playbook are not in stable state, so you can
use it ... but we dont provide any garantee that they stay working in
the future.

======================
TYPO3 Neos Vagrant Box
======================

The current playbooks and roles can be used to build a TYPO3 Neos vagrant
box, with PHP 5.5, Nginx and MySQL. As we are active contributors to TYPO3
Neos, this box will receive a lots of love to help us in testing Neos in
different version, ...

------------
Installation
------------

.. code-block:: bash

    $ pip install ansible
    $ git clone git@github.com:ttreeagency/ansible-playground.git
    $ cd ansible-playground
    $ git submodule init
    $ git submodule update
    $ vagrant up

Update your hosts file:

.. code-block::

    192.168.77.21 www.neos-workshop.box neos-workshop.box

And open your browser to http://www.neos-workshop.box/setup

Enjoy ...

================
Availables Roles
================

* common
* mysql-client
* webserver-nginx
* webserver-php
* webserver-vhosts

========================
Contribution are welcome
========================

Any contribution is highly welcome, just push a PR, open an Issue, ...

Bests,

Dominique Feyer, ttree.ch
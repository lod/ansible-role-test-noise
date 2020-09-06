Ansible Test Noise
==================

A noise generator for testing Ansible execution

Role Variables
--------------

`atn_delay = 3` controls the delay between execution steps in seconds. It defaults to three.

`atn_inner_count = 5` specifies how many steps to execute in the inner task. Each step is followed by a pause of `atn_delay` seconds. This value defaults to five.

`atn_outer_count = 3` specifies how many inner tasks will be run. Each inner task is followed by a pause of `atn_delay` seconds. This value defaults to three.

The total execution time is roughly `atn_outer_count * atn_inner_count * atn_delay`.

Dependencies
------------

This role has no dependancies.

It also can be safely run against any operating system or localhost.

It never actually does anything or initiates a connection.

Example Playbook
----------------

	- hosts: localhost
	  become: false
	  gather_facts: false
	  roles:
	    - ansible_test_noise

	- hosts: anything
	  roles:
	    - role: ansible_test_noise
		  vars:
		    atn_delay: 10
			atn_outer_count: 5
			atn_inner_count: 3

License
-------

BSD

Author Information
------------------

This role was created in 2020 by [David Tulloh](https://github.com/lod/)

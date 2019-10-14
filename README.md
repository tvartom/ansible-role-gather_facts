tvartom.gather_facts
====================

A role to gather facts from var/files and the host.

Install role
------------

Create `requirements.yml` in your ansible playbook-folder:

    ---
    # Documentation:
    # https://docs.ansible.com/ansible/latest/reference_appendices/galaxy.html#installing-multiple-roles-from-a-file
    
    - name: tvartom.gather_facts
      src: https://github.com/tvartom/ansible-role-gather_facts
      scm: git
      # version: "v1.0" # Omit for latest version.

Run:

    $ ansible-galaxy install -r requirements.yml -p roles/



Requirements
------------

As an alternative to ansible-vault, a file with variables
can be red from the host `/root/host_vars.yml`
Make sure only root can access it.

    ---
    mariadb:
      root_password: "MY SECRET PASSWORD"

    my_private_key: >-
      SECRET SECRET SECRET
      SECRET SECRET SECRET

Role Variables
--------------

Return variables:

* Any given in the variable files.
* diskspace_message

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      tasks:
        - include_role:
            name: tvartom.gather_facts
          vars:
            facts_options:
              var_files:
                - users
                - system
              host_vars_from_host: true
              diskapace_message: true
          tags:
            - always

License
-------

CC-BY-4.0

Author Information
------------------

tvartom

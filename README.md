Role Name
=========

A brief description of the role goes here.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: username.rolename, x: 42 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).


1. set the keyboard to _Windows mode_ using the side switch

1. hold `Fn + X + L` for 4 seconds to set the function key row to _fn mode_

1. ensure the `hid_apple` module is loaded

   ```shell
   sudo modprobe hid_apple

   # load at boot
   echo 'hid_apple' | sudo tee /etc/modules-load.d/keychron.conf
   ```

1. configure the keyboard's _fn mode_:

   ```shell
   echo 0 | sudo tee /sys/module/hid_apple/parameters/fnmode

   # load at boot
   echo 'options hid_apple fnmode=0' | sudo tee /etc/modprobe.d/keychron.conf
   ```

## Further readings

- [K8 keyboard user manual]
- [Keychron fn keys in Linux]
- [Apple Keyboard] on the [Archlinux wiki]

[apple keyboard]: https://wiki.archlinux.org/index.php/Apple_Keyboard
[k8 keyboard user manual]: https://www.keychron.com/pages/k8-keyboard-user-manual
[keychron fn keys in linux]: https://mikeshade.com/posts/keychron-linux-function-keys

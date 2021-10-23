# Keychron Capable

Enables a **Linux** system to accept input from a Keychron keyboard's function keys row.

Example of manual process:

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

## Requirements

The changes this role makes:

- **only** work on (and are only applied to) a Linux system
- will work better if you are using a Keychron keyboard

## Role Variables

Variable                | Type    | Default value              | Description
------------------------|---------|----------------------------|------------
fast_connectable        | boolean | `true`                     | Enable fast reconnect via Bluetooth
fn_mode                 | integer | 0                          | Default fn keys behavior: `0` = multimedia, `1` = use last setting, `2` = function
module_name             | string  | hid_apple                  | Module to load
module_file_name        | string  | keychron.conf              | File name for module loading on boot; will be put into `/etc/modules-load.d`
module_params_file_name | string  | same as `module_file_name` | File name for module configuration; will be put into `/etc/modprobe.d`
tune_bluetooth          | boolean | `no`                       | Tune Bluetooth settings

## Dependencies

None.

## Example Playbook

```yaml
- hosts: workstation
  roles:
    - role: keychron_capable
      tags:
        - keyboard
        - keychron
      vars:
        tune_bluetooth: true
        fast_connectable: no
        fn_mode: 2
        module_file_name: hid_apple.conf
```

## License

MIT

## Sources

- [K8 keyboard user manual]
- [Keychron fn keys in Linux]
- [Apple Keyboard] on the [Archlinux wiki]

[apple keyboard]: https://wiki.archlinux.org/index.php/Apple_Keyboard
[k8 keyboard user manual]: https://www.keychron.com/pages/k8-keyboard-user-manual
[keychron fn keys in linux]: https://mikeshade.com/posts/keychron-linux-function-keys

[archlinux wiki]: https://wiki.archlinux.org

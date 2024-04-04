# Ansible Role: Flare VM ([Ludus](https://ludus.cloud))

An Ansible Role that installs [Flare VM](https://github.com/mandiant/flare-vm) on Windows >= 10 hosts.

## Requirements

Windows defender should be disabled in Safe Mode see [this guide](https://lazyadmin.nl/win-11/turn-off-windows-defender-windows-11-permanently/) or [this video](https://www.youtube.com/watch?v=81l__vvGnjA).
While this role attempts to disable Defender, it can only do so much without booting into safe mode.

## Role Variables

    # Disable the red/green dynamic Ludus wallpaper in favor of the static flarevm wallpaper
    ludus_flarevm_use_flarevm_wallpaper: true

## Dependencies

None.

## Known issues

Check the [Daily Failures](https://github.com/mandiant/VM-Packages/wiki/Daily-Failures) page for known issues with flarevm packages on different operating systems.

Other issues:
- `DotNet3.5` fails to install on Windows 11 22H2.

## Example Playbook

```yaml
- hosts: flarevm_hosts
  roles:
    - badsectorlabs.ludus_flarevm
```

## Example Ludus Range Config

```yaml
ludus:
  - vm_name: "{{ range_id }}-flare"
    hostname: "{{ range_id }}-FLARE"
    template: win11-22h2-x64-enterprise-template
    vlan: 99
    ip_last_octet: 2
    ram_gb: 8
    cpus: 4
    windows:
      install_additional_tools: true
    roles:
      - badsectorlabs.ludus_flarevm
```

## License

GPLv3

## Author Information

This role was created by [Bad Sector Labs](https://github.com/badsectorlabs), for [Ludus](https://ludus.cloud/).

# Ansible Role: NTP

Installs NTP on CentOS & Ubuntu Linux servers.

## Requirements

None.

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

* ntp_enabled: `true`

Whether to start the ntpd service and enable it at system boot. On many virtual machines that run inside a container (like OpenVZ or VirtualBox), it's recommended you don't run the NTP daemon, since the host itself should be set to synchronize time for all it's child VMs.

* ntp_timezone: `Etc/UTC`

Set the timezone for your server.

    ntp_manage_config: false

Override the following default variable with your custom || other ntp servers like so:

```python

    ntp_servers:
     - 0.pool.ntp.org
     - 1.pool.ntp.org
     - 2.pool.ntp.org
     - 3.pool.ntp.org

```

Specify the NTP servers you'd like to use. Only takes effect if you allow this role to manage NTP's configuration, by setting `ntp_manage_config` to `true`.

## Dependencies

None.

## Example Playbook

* With defaults:

```python

    - hosts: all
      roles:
        - shelleg.ntp

```

* With ntp_timezone & ntp_servers overrides:

```python

    - hosts: all
      roles:
        - shelleg.ntp
          ntp_servers:
            - my_cool_ntp.mydomain.com
            - my_cool_ntp2.mydomain.com
          ntp_timezone: Asia/Jerusalem

```

## License

MIT / BSD

## Author Information

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
# Ansible Role: Icecast

[![Build Status](https://travis-ci.org/danielwhite/ansible-role-icecast.svg?branch=master)](https://travis-ci.org/danielwhite/ansible-role-icecast)

An Ansible role that installs [Icecast](http://icecast.org/) on Debian/Ubuntu.

Currently this is limited to providing only a master server.

## Role Variables

The following describes the variables for configuring the role (see: `defaults/main.yml`).

```
icecast_listener_port: 8000
icecast_listener_bind_address: 127.0.0.1
```

The port and address that Icecast will listen for connections from clients, sources, and relays. Currently only a single listener can be defined.

```
icecast_source_pass: hackme

icecast_relay_user: relay
icecast_relay_pass: hackme

icecast_admin_user: admin
icecast_admin_pass: hackme
```

These configure all the usernames or passwords 

You can define "normal" type mounts with the `icecast_mounts` variable. The properties per each mountpoint should match the options listed in the [Mount Specific Settings documentation](http://icecast.org/docs/icecast-2.4.1/config-file.html#mountsettings).

The following example defines two mounts:

```
icecast_mounts:
  - mount-name: /stream
  - mount-name: /other
    stream-description: Alternative stream.
```

Settings relevant to multiple mounts can instead be defined in the `icecast_default_mount variable`.

```
icecast_default_mount:
  public: 0
  intro: welcome.mp3
```

Settings common to multiple mount points.

```
icecast_log_level: warn
```

Valid options for log levels are `debug`, `info` (default), `warn`, or `error`.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: danielwhite.icecast }

## License

BSD

## Author Information

This role was created in 2016 by [Daniel White](https://github.com/danielwhite).

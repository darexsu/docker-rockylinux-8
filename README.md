# Dockerfile: Rockylinux-8 for Molecule CI 

[![Build](https://github.com/darexsu/docker-rockylinux-8/actions/workflows/build.yml/badge.svg)](https://github.com/darexsu/docker-rockylinux-8/actions/workflows/build.yml)
[![Docker pulls](https://img.shields.io/docker/pulls/darexsu/molecule-rockylinux-8.svg?)](https://hub.docker.com/r/darexsu/molecule-rockylinux-8/)

Pre-build RockyLinux 8. Image already has Ansible inside, so Molecule doesn't need to waste time building it.

### Example molecule.yml
```yaml
---
dependency:
  name: galaxy
driver:
  name: docker
platforms:
  - name: instance
    image: "darexsu/molecule-rockylinux-8:latest"
    command: ${MOLECULE_DOCKER_COMMAND:-""}
    tmpfs:
      - /run
      - /tmp
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
    privileged: false
    pre_build_image: true
provisioner:
  name: ansible
  inventory:
    host_vars:
      instance:
        ansible_user: ansible
  playbooks:
    converge: ${MOLECULE_PLAYBOOK:-converge.yml}
```

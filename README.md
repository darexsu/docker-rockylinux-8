# Dokerfile: Rockylinux-8 for Molecule CI 

[![Build](https://github.com/darexsu/docker-rockylinux-8/actions/workflows/build.yml/badge.svg)](https://github.com/darexsu/docker-rockylinux-8/actions/workflows/build.yml)
[![Docker pulls](https://img.shields.io/docker/pulls/darexsu/molecule-rockylinux-8.svg?maxAge=2592000)](https://hub.docker.com/r/darexsu/molecule-rockylinux-8/)

RockyLinux-8 for Ansible Playbooks testing

### Example molecule.yml
```yaml
---
dependency:
  name: galaxy
driver:
  name: docker
platforms:
  - name: instance
    image: "darexsu/docker-rockylinux-8:latest"
    command: ${MOLECULE_DOCKER_COMMAND:-""}
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
    privileged: true    
provisioner:
  name: ansible
  playbooks:
    converge: converge.yml
```

# Ansible NFS Client

Install NFS Client packages and mounts an NFS share in fstab.

##  Requirements

N/A

## Role Variables

`nfs_mount_name`: Name of the NFS mount

`nfs_mount_src`: URI of NFS mount

`nfs_mount_owner`: Mount directory owner

`nfs_mount_group`: Mount directory group

## Dependencies

N/A

## Example Playbook

```yaml
- hosts: servers
  become: true
  pre_tasks:
    - name: Update apt cache.
      apt:
        update_cache: true
        cache_valid_time: 600
      changed_when: false
      register: result
      until: result is success
      retries: 5
      delay: 5
      when: ansible_os_family == 'Debian'
  roles:
   - role: calvinbui.ansible_nfs_client
```

## License

GPLv3

## Author Information

http://calvin.me

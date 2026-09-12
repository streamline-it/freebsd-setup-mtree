Role Name
=========

Intrusion detection system utilizing mtree for FreeBSD hosts.  This system tries to secure the specfiles and scripts from modification by using chflags.  It will add append only to log files.  And it will add immutability for script files and spec files.  This will be best secured if the host is in security level 1 or higher.

Requirements
------------

Role Variables
--------------

# defaults file for freebsd-setup-mtree

# location for mtree spec files
freebsd_setup_mtree_base_dir: /var/db/mtree

# filepath to mtree execution log
freebsd_setup_mtree_log: /var/log/mtree.log

# filepath to mtree comparison results; only differences will be logged
freebsd_setup_mtree_compare_log: /var/log/mtree-compare.log

# script to compare mtree flagged directories to spec files
freebsd_setup_mtree_script_check: /usr/local/sbin/freebsd_setup_mtree_check.sh

# this script creates the specfiles to specified directories
freebsd_setup_mtree_script_create_specfile: /usr/local/sbin/freebsd_setup_mtree_create_specfile.sh

# mtree command filepath
freebsd_setup_mtree_command: /usr/sbin/mtree

# chflags command filepath
freebsd_setup_mtree_chflags_command: /bin/chflags

# directories to monitor with mtree
freebsd_setup_mtree_directories:
  - /bin
  - /sbin
  - /usr/bin
  - /usr/sbin
  - /usr/local/bin
  - /usr/local/sbin

# mtree algorithm
freebsd_setup_mtree_sha_algorithm: sha256digest

# mode for spec files
freebsd_setup_mtree_spec_mode: "0400"

# mode for setup mtree script 
freebsd_setup_mtree_script_mode: "0500"

# mode for compare mtree script
freebsd_setup_mtree_log_mode: "0600"

# name for cronjob file
freebsd_setup_mtree_cron_name: mtree_check

# cronjob minute argument
freebsd_setup_mtree_cron_minute: "*/30"

# cronjob hour argument
freebsd_setup_mtree_cron_hour: "*"

# cronjob argument for day 
freebsd_setup_mtree_cron_day: "*"

# cronjob argument for month
freebsd_setup_mtree_cron_month: "*"

# cronjob argument for day of week
freebsd_setup_mtree_cron_day_of_week: "*"



# vars file for freebsd-setup-mtree

freebsd_setup_mtree_sysctl_key: kern.securelevel
freebsd_setup_mtree_awk_cmd: /usr/bin/awk
freebsd_setup_mtree_sysctl_cmd: /sbin/sysctl

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

- name: freebsd-setup-mtree example
  hosts: servers
  become: true

  roles:

    - name: freebsd-setup-mtree

License
-------

BSD

Author Information
------------------
Rich O'Hara



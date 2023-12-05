infra
=========

- 호스트 운영/관리 및 모니터링 툴 설치
- 호스트 공통 zabbix 모니터링 설정 배포
- Zabbix 계정에 대한 기본 sudoers 설정
- Supported: CentOS, SmartOS

Requirements
------------

None

Role Variables
--------------

Linux resource limit 정의 (systemd) 
- number_of_open_files_systemd
- number_of_open_processes_systemd

Dependencies
------------

None

Example Playbook
----------------

```
ansible-playbook infra.yml --list-tasks 

playbook: infra.yml

  play #1 (all): all    TAGS: []
    tasks:
      infra : install a list of packages (ops tools)    TAGS: [ops_tools]
      infra : copy 'zabbix' account into place, after passing validation with visudo    TAGS: [sudoers]
      infra : install a list of packages        TAGS: [need_packages]
      infra : install pkgin package (SmartOS)   TAGS: [need_packages]
      infra : adding existing 'zabbix' user to group 'docker'   TAGS: []
      infra : adding existing 'zabbix' user to group 'frrvty'   TAGS: []
      infra : copy userparameter_conf   TAGS: [copy_zbx_userparam]
      copy userparameter template infra - CentOS        TAGS: [copy_zbx_userparam]
      copy userparameter template infra - SmartOS       TAGS: [copy_zbx_userparam]
      set_fact  TAGS: [copy_zbx_userparam, smartctl]
      set_fact  TAGS: [copy_zbx_userparam, smartctl]
      infra : copy smartctl-disks-discovery     TAGS: [copy_zbx_userparam, smartctl]
      infra : copy userparameter template S.M.A.R.T.    TAGS: [copy_zbx_userparam, smartctl]
      copy      TAGS: [copy_tor]
      copy      TAGS: [copy_tor]
      infra : copy check dmesg  TAGS: [copy_check_dmesg]
      infra : add execute permission script files       TAGS: [copy_zbx_userparam]
```
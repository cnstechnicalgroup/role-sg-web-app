Role: cns.sg-web-app
========

This role configures AWS security groups for a web project.

Requirements
------------

Nothing, it runs out of the box.

Role Variables
--------------

In the current version, you can specify the following variables:

| Name                  | Default |                                                                               |
|-----------------------|---------|-------------------------------------------------------------------------------|
| vpc                   |   ---   | Object containint entire VPC structure returned from cns.vpc-info.            |
| project               |   ---   | Object containing project details (see example).                              |

Dependencies
------------

[cns.vpc-info](https://github.com/cnstechnicalgroup/role-vpc-info)

License
-------

GPLv2

Author Information
------------------

Created by Sam Morrison [@samcns](https://www.twitter.com/samcns)

Examples
--------

```yaml
# Var file
# Dict containing project configuration details
project:
  prefix: exampleproject
  mode: prod
  domain: exampleproject.com
  use_elb: false
  ssl_arn: ""
# EC2 instance configuration
  ec2_prod:
  ...
  rds_prod:
  ...
```

```yaml
---
# Playbook
- name: cns.provision-site-sg example
  hosts: localhost
  roles:
    - { role: cns.vpc-info, tags: "vpc" }
    - { role: cns.sg-web-app, tags: "sg" }
```

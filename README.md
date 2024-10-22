<p><img src="https://restic.readthedocs.io/en/stable/_static/logo.png" alt="restic logo" title="restic" align="right" height="60" /></p>

# Ansible Role: restic

![](https://i.imgur.com/waxVImv.png)
### [View all Roadmaps](https://github.com/nholuongut/all-roadmaps) &nbsp;&middot;&nbsp; [Best Practices](https://github.com/nholuongut/all-roadmaps/blob/main/public/best-practices/) &nbsp;&middot;&nbsp; [Questions](https://www.linkedin.com/in/nholuong/)
<br/>

## Description

Deploy [restic](https://restic.net/) - fast, secure, efficient backup program.

## Requirements

- Ansible > 2.2
- bzip2 installed on deployer machine (same one where ansible is installed)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `restic_version` | 0.9.3 | restic package version. Also accepts latest as parameter. |
| `restic_user` | "root" | system user to run restic |
| `restic_group` | "root" | system group to run restic |
| `restic_shell` | "/bin/false" | the shell for the restic user, change this if you want to be able to su to it |
| `restic_install_path` | "/usr/local/bin" | directory where restic binary will be installed |
| `restic_cron_mailto` | restic_user | who to mail results of the restic crons to, set to "" to not mail |
| `restic_cron_stdout_file` | null | what file to log restic output to, null means include in mailto, use /dev/null to discard |
| `restic_cron_stderr_file` | null | what file to log restic errors to, null means include in mailto, use /dev/null to discard |
| `restic_repos` | [] | restic repositories and cron jobs configuration. More in [defaults/main.yml](defaults/main.yml) |

## Security

To ensure high security this role can allow restic to be run as different user than root and still allowing read-only access to files. This is implemented by following [PR#1483](https://github.com/restic/restic/pull/1483) from restic repository.

## Helpers

This role also installs helper scripts to `restic_install_path`. These scripts are named after your repository and will ensure environment variables are correct for that repository.

For example, if you have a restic repository named `testrepo`, you could use the `restic-testrepo` command, which will execute `restic` with the correct environment variables to manipulate that repository.

## Example

### Playbook

Use it in a playbook as follows:
```yaml
- hosts: all
  become: yes
  roles:
    - paulfantom.restic
```

## Local Testing

The preferred way of locally testing the role is to use Docker and [molecule](https://github.com/metacloud/molecule) (v2.x). You will have to install Docker on your system. See Get started for a Docker package suitable to for your system.
All packages you need to can be specified in one line:
```sh
pip install ansible 'ansible-lint>=3.4.15' 'molecule>2.13.0' docker 'testinfra>=1.7.0' jmespath
```
This should be similar to one listed in `.travis.yml` file in `install` section.
After installing test suit you can run test by running
```sh
molecule test --all
```
For more information about molecule go to their [docs](http://molecule.readthedocs.io/en/latest/).

## Travis CI

Combining molecule and travis CI allows to test how new PRs will behave when used with multiple ansible versions and multiple operating systems. This also allows to create test scenarios for different role configurations. As a result test matrix is quite large and takes more time than local testing, so please be patient.

# 🚀 I'm are always open to your feedback.  Please contact as bellow information:
### [Contact ]
* [Name: nho Luong]
* [Skype](luongutnho_skype)
* [Github](https://github.com/nholuongut/)
* [Linkedin](https://www.linkedin.com/in/nholuong/)
* [Email Address](luongutnho@hotmail.com)

![](https://i.imgur.com/waxVImv.png)
![](Donate.png)
[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/nholuong)

# License
* Nho Luong (c). All Rights Reserved.🌟
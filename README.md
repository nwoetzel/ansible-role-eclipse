Ansible role eclipse
====================

[![Build Status](https://travis-ci.org/nwoetzel/ansible-role-eclipse.svg?branch=master)](https://travis-ci.org/nwoetzel/ansible-role-eclipse)
[![Branch](https://img.shields.io/github/tag/nwoetzel/ansible-role-eclipse.svg)](https://galaxy.ansible.com/nwoetzel/eclipse)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-nwoetzel.eclipse-660198.svg)](https://galaxy.ansible.com/nwoetzel/eclipse)

This Ansible Eclipse role is based on the work from [Alban Andrieu](fr.linkedin.com/in/nabla/) which one may find [here](https://github.com/AlbanAndrieu/ansible-eclipse). It has been extensively rewritten to support anysier installation and configuration of plugins, different eclipse distributions and packages (downloads).

## Description

This ansible roles installs a eclipse distribution and optional plugins.

## Dependencies

- ansible >= 2
- nwoetzel.java-oracle

## Role Variables

All defaults are documented also in the [defaults](defaults/main.yml) file.

| variable | required | default | description |
|--:|:-:|:-:|:--|
| eclipse_distro | yes | - | the eclipse distribution, e.g. mars, neon |
| eclipse_package | yes | - | the package (i.e. which default plugins are installed), e.g. java, php, cpp ... |
| eclipse_mirror_id | no | - | an optional mirror_id for downloading the package, if the default behavior of picking the best one, does not work |
| eclipse_plugins_custom | no | {} | a dictionary of plugin declarations (to add more to the defaults in vars/main.yml or to overwrite) - read more in defaults/main.yml |
| eclipse_plugins_install | no | [] | list of plugin names to be installed, as they are defined in the [vars](vars/main.yml) or with the variable eclipse_plugins_custom |
| package_list_eclipse | no | [] | additional apt package names that should be installed |
| eclipse_download_folder_remote | no | - | when set, the file is downloaded to the installation host |
| eclipse_service_release | no | set by this [role](vars/main.yml) | the latest known is used when not set - depending on the distro can be 'SR2' (<=luna) or just '2' (>=mars) |
| eclipse_ini_overwrite | no | false | modify eclipse.ini |
| eclipse_ini_flags_next_line | no | {} | a dictionary of ini flags for eclipse, e.g. '"-vm": /opt/bin/java' |
| eclipse_ini_flags_vmargs | no | {} | a dictionary of vmargs for the java virtual machine, e.g. '"-XX:MaxPermSize=": "1024m"' |
| eclipse_ui_id_prefs_settings | no | { SHOW_WORKSPACE_SELECTION_DIALOG: "false",  RECENT_WORKSPACES: ""} | key-value pairs to insert/overwrite in the org.eclipse.ui.ide.prefs file |

## Facts

| variable | description |
|--:|:--|
| eclipse_install_dir | the directory eclipse is installed to |

## Possibilities

It is possible to install almost any [eclipse package of any distribution](http://www.eclipse.org/downloads/packages/). Currently, incubation packages and classic distributions are not supported.
Additinally, many plugins are preconfigured and can just be installed through their name.

## Limitations

Eclipse packages with incubation components or classic distributions are not supported yet.
Plugins need to be configured in the role, before they can be installed trough their name or repository url.
Adaption for either limitation can be easily implemented.

## Dependencies

This role depends on [nwoetzel/ansible-role-oracle-java](https://github.com/nwoetzel/ansible-role-oracle-java) to install a jdk and to set the '-vm' argument in the eclipse.ini. This dependency can be removed from meta/main.yml - and the role will work but will require a java to be in the PATH or JAVA_HOME to be set.

## License

[GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)

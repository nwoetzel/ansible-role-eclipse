Ansible role eclipse
====================

[![Build Status](https://travis-ci.org/nwoetzel/ansible-role-eclipse.svg?branch=master)](https://travis-ci.org/nwoetzel/ansible-role-eclipse)

This Ansible Eclipse role is based on the work from [Alban Andrieu](fr.linkedin.com/in/nabla/) which one may find [here](https://github.com/AlbanAndrieu/ansible-eclipse). It has been extensively rewritten to support anysier installation and configuration of plugins, different eclipse distributions and packages (downloads).

### Possibilities

It is possible to install almost any [eclipse package of any distribution](http://www.eclipse.org/downloads/packages/). Currently, incubation packages and classic distributions are not supported.
Additinally, many plugins are preconfigured and can just be installed through their name.

### Limitations

Eclipse packages with incubation components or classic distributions are not supported yet.
Plugins need to be configured in the role, before they can be installed trough their name or repository url.
Adaption for either limitation can be easily implemented.

### Dependencies

This role depends on [nwoetzel/ansible-role-oracle-java](https://github.com/nwoetzel/ansible-role-oracle-java) to install a jdk and to set the '-vm' argument in the eclipse.ini. This dependency can be removed from meta/main.yml - and the role will work but will require a java to be in the PATH or JAVA_HOME to be set.

### License

[GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)

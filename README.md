easy-ansible-role-archetype
===========================
[![Build Status](https://travis-ci.org/DANS-KNAW/easy-ansible-role-archetype.png?branch=master)](https://travis-ci.org/DANS-KNAW/easy-ansible-role-archetype)


SYNOPSIS
--------

      mvn archetype:generate -DarchetypeGroupId=nl.knaw.dans.easy \
                -DarchetypeArtifactId=easy-ansible-role-archetype \
                -DarchetypeVersion=1.x-SNAPSHOT \
                -DartifactId=dans.easy-test-module \
                -Dmodule_name=easy-test-module \
                -Dmodule_name_underscores=easy_test_module \
                -Dname="EASY Test Module Ansible Role" \
                -Ddescription="An Ansible role to install easy-test-module on RHEL 6 or 7" 


DESCRIPTION
-----------

Creates an [EASY] ansible role project, prepopulated with common files and structure as required by Ansible.
It uses the [maven archetype plugin]. Each EASY module should have an accompanying [Ansible role] that installs
and configures it on a target machine. If the role is made available as a GitHub project, it can be
installed directly with the [ansible-galaxy] command. 

[maven archetype plugin]: http://maven.apache.org/archetype/maven-archetype-plugin
[Ansible role]: http://docs.ansible.com/ansible/playbooks_roles.html
[ansible-galaxy]: http://docs.ansible.com/ansible/galaxy.html#installing-roles


### Example usage

Like the synopsis the example below will create a project called `dans.easy-test-module`.
The variables prevent typo variations in the actual name of the module but you will still have
to adjust the value for the `-Dname` parameter. You won't get a chance to correct the name as
is possible for the version and package.
Note that trailing white space invalidates the continuation symbols.

      export MODULE_NAME=test-module
      export MODULE_NAME_UNDERSCORES="echo $MODULE_NAME | sed 's/-/_/g'"
      mvn archetype:generate -DarchetypeGroupId=nl.knaw.dans.easy \
                -DarchetypeArtifactId=easy-ansible-role-archetype \
                -DarchetypeVersion=1.x-SNAPSHOT \
                -DartifactId=dans.easy-$MODULE_NAME \
                -Dmodule_name=easy-$MODULE_NAME \
                -Dmodule_name_underscores=easy_$MODULE_NAME_UNDERSCORES \
                -Dname="EASY Test Module Ansible Role" \
                -Ddescription="An Ansible role to install easy-$MODULE_NAME on RHEL 6 or 7"

**Further conventions at [DANS]**

Create the project while you are in the directory `~/git/dtap/roles`. Finish project creation with a commit.
No variable in the initial commit example, this time autocompletion can prevent typos:

      cd dans.easy-test-module
      git init; git stage -A; git commit -m "created by archetype"

[DANS]: https://github.com/DANS-KNAW
[EASY]: https://dans.knaw.nl/nl/over/diensten/data-archiveren-en-hergebruiken/easy


ARGUMENTS
----------




INSTALLATION AND CONFIGURATION
------------------------------

* Add `http://maven.dans.knaw.nl/` as a plug-in repository if you want to use a release version of this plug-in.
* Clone and build the project if you want to use a snapshot.


BUILDING FROM SOURCE
--------------------

Prerequisites:

* Maven 3.3.3 or higher

Steps:

        git clone https://github.com/DANS-KNAW/easy-module-archetype.git
        cd easy-module-archetype
        mvn install

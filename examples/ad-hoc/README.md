# Ad-Hoc Command

* Linux

Run the following commands for learning Windows modules:

```sh
$ ansible linux -m copy -a "src=/etc/hosts dest=/tmp/hosts"

$ ansible linux -b -m file -a "dest=/srv/foo/b.txt mode=600 owner=root group=root"
$ ansible linux -m file -a "dest=/tmp/dir mode=755 owner=vagrant group=vagrant state=directory"
$ ansible linux -m file -a "dest=/tmp/dir state=absent"

$ ansible linux -m yum -a "name=acme state=present"

$ ansible linux -m shell -a 'echo $TERM'
$ ansible linux -m command -a 'uname -n'
```

* Windows

Run the following commands for learning Windows modules:

```sh
$ ansible windows -m win_copy -a "src=/etc/hosts dest=C:/Users/vagrant/hosts"

$ ansible windows -m win_file -a "path=C:/Users/vagrant/subfolder state=directory"
$ ansible windows -m win_file -a "path=C:/Users/vagrant/subfolder state=absent"

$ ansible windows -m win_shell -a "echo %HOMEDIR%"
$ ansible windows -m win_feature -a "name=Web-Server state=present"
```
Since Fedora 26, the Dnf repoquery subcommand supports has a new option for listing all user-installed packages:
```
$ dnf repoquery --qf '%{name}' --userinstalled \
 | grep -v -- '-debuginfo$' \
 | grep -v '^\(kernel-modules\|kernel\|kernel-core\|kernel-devel\)$' > pkgs_a.lst
 
```

In contrast to other methods, it also lists all debuginfo packages. The additional grep in the above example filters them out.

To install the list on host B:
`$ < pkgs_a.lst xargs dnf -y install`

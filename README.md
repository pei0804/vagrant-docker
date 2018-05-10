# Docker on vagrant

- [virtualbox 5.1](https://www.virtualbox.org/wiki/Download_Old_Builds_5_1)
- vagrant 2.0.0

```console
$ vagrant up
```

## vbguest error

```console
$ vagrant plugin install vagrant-vbguest
$ vagrant vbguest
$ vagrant up
$ vagrant ssh -c 'sudo yum update -y kernel'
$ vagrant vbguest --status
GuestAdditions 5.0.16 running --- OK.
$ vagrant reload
```

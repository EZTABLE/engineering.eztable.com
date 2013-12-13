title: setup-runit-in-three-seconds
date: 2013-12-13 19:30:40
tags: devops
---

### install runit

```
$ sudo apt-get install runit
```

### create nessesary folders

```
$ sudo mkdir /etc/service
```

```
$ sudo mkdir /etc/runit/your_daemon
```

### write a `run` script

```
touch /etc/runit/your_daemon/run
chmod +x /etc/runit/your_daemon/run
```

the content would be like this:

```
#!/bin/sh -e
exec echo "hi"
```

### make a symlink to `/etc/service`

```
ln -s /etc/runit/your_daemon /var/service/your_daemon
```

## Explanation

Two key programs in runit: `runsv`, `runsvdir`
`runsvdir` will monitor the folder: `/etc/service/`

1. We can manage each daemon under `/etc/runit` by creating subfolder
2. Make a symlink link to `/etc/service/`
3. done

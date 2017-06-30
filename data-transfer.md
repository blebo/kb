Data can be recovered on mountable drive with `rsync` 
(used as a more resilient, resume-able copy method):

```
rsync -avP PATH/TO/SOURCE/ PATH/TO/DESTINATION/
```
Copies content of `SOURCE` to content of `DESTINATION`. Note trailing `/`.

* `-a`: Archive mode.
* `-v`: Verbose output.
* `-P`: Keep partially transmitted files and show progess of transfer.
* `--no-perms`: Useful for copying to Windows shares to avoid operation not permitted on Freenas. May also need to use -A to preserve ACL from source.

---
Data transferred with `rsync` via ssh:
From remote to local:

```
rsync -avP -e ssh user@host:PATH/TO/SOURCE/ PATH/TO/DESTINATION/
```

From local to remote:

```
rsync -avP -e ssh PATH/TO/SOURCE/ user@host:PATH/TO/DESTINATION/
```

Copies content of `SOURCE` to content of `DESTINATION`. Note trailing `/`.

* `-a`: Archive mode.
* `-v`: Verbose output.
* `-P`: Keep partially transmitted files and show progess of transfer.

See [rsync](https://download.samba.org/pub/rsync/rsync.html) man page for further documentation.

---
Download multiple files with `wget` in parallel 
(where `N` is the number of downloads in parallel):

```
cat PATH/TO/URL.LIST | parallel --will-cite -j N wget -c {}
```

* `-j N`: `parallel` switch for `N` number of parallel processes to run.
* `-c`: `wget` switch to resume download if applicable.
* `{}`: Placeholder for current URL from `URL.LIST`.
* `--will-cite`: Silences obnoxious `parallel` citation message, citation below:
```
O. Tange (2011): GNU Parallel - The Command-Line Power Tool,
  ;login: The USENIX Magazine, February 2011:42-47.
```

---
Copy folder and sub-tree, into another folder:

```
cp -R SOURCE PATH/TO/DEST/
```

---
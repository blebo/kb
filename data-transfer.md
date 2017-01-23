Data can be recovered on mountable drive with `rsync` 
(used as a more resilient, resume-able copy method):

```
rsync -avP source/ destination/
```
Copies content of `source` to content of `destination`.
* `-a`: Archive mode.
* `-v`: Verbose output.
* `-P`: Keep partially transmitted files and show progess of transfer.

See [rsync](https://download.samba.org/pub/rsync/rsync.html) man page for further documentation.

---
Download multiple files with `wget` in parallel 
(where `N` is the number of downloads in parallel):

```
cat path/to/url.list | parallel --will-cite -j N wget -c {}
```
* `-j N`: `parallel` switch for `N` number of parallel processes to run.
* `-c`: `wget` switch to resume download if applicable.
* `--will-cite`: Silences obnoxious `parallel` citation message, citation below:
```
O. Tange (2011): GNU Parallel - The Command-Line Power Tool,
  ;login: The USENIX Magazine, February 2011:42-47.
```

---

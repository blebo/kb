Data can be recovered on mountable drive with `rsync`:

```
rsync -avP source/ destination/
```


Download multiple files with `wget` in parallel 
(where `N` is the number of downloads in parallel):

```
cat path/to/url.list | parallel --will-cite -j N wget -c {}
```

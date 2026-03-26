To tar and gzip a folder, the syntax is:
```bash
tar czf name_of_archive_file.tar.gz name_of_directory_to_tar
```
Adding - before the options (czf) is optional with tar. The effect of czf is as follows:

c — create an archive file (as opposed to extract, which is x)
f — filename of the archive file
z — filter archive through gzip (remove this option to create a .tar file)
If you want to tar the current directory, use . to designate that.

# Go Koans

This repo is forked from [cdarwin/go-koans](
https://github.com/cdarwin/go-koans). I am adding the solutions in an encrypted
form (`<filename>_solution.gpg`) so I can still access the solutions at a later
date and don't spoil the fun for others. Cheers!

## Steps to access solutions

_Warning: These steps won't work for you, because you don't have my GPG key
:stuck_out_tongue:. They're just for me in the future if I want to
access the solutions_

1. Encrypt
```bash
gpg --output about_<name>_solution.gpg --encrypt --armor --recipient mbtamuli@gmail.com about_<name>.go
```

2. Decrypt
```
gpg --output about_<name>.go --decrypt about_<name>_solution.gpg
```

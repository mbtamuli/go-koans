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

## Bash fu

Since I love bash and am lazy enough to not want to repeat uninteresting stuff
, here are a few points related to solving these koans.

1. I was having to run `go test` every time I made the changes, so I made the
   command run every time I saved the file

```bash
git clone https://github.com/mbtamuli/go-koans/ && cd $_
while true; do
  inotifywait -qe modify,create,delete -r $PWD -o /dev/null &&\
  clear && \
  docker run --rm -ti -v "$PWD":/go/src/ -w /go/src/ golang:1.11-alpine go test
done
```

2. Trying to access the solution or encrypting the solution, you'll have to
   run the encrypt or the decrypt steps for each and every file, but not if
   you do this

```bash
# Encrypt
for file in ./*.go; do
 if [[ $file != *"setup_koans_test"* ]] && gpg --output "${file%%.go}_solution.gpg" --encrypt --armor --recipient mbtamuli@gmail.com "$file"
done
```

```bash
# Decrypt
for file in ./*.gpg; do
 gpg --batch --yes --output "${file%%_solution.gpg}.go" --decrypt "$file"
done
```


### Deployment
Contains deployment steps and examples for various as per current versions.

### LOC
```bash
sudo apt install cloc
```
Make script cloc-git and place in path, chmod +x:
```bash
#!/usr/bin/env bash
git clone --depth 1 "$1" temp-linecount-repo &&
  printf "('temp-linecount-repo' will be deleted automatically)\n\n\n" &&
  cloc temp-linecount-repo &&
  rm -rf temp-linecount-repo
```
Usage
```bash
cloc-git https://github.com/evalEmpire/perl5i.git
```

#### Get OS
```bash
cat /etc/os-release
```
#### Get X type
```bash
ls /usr/bin/*session
```
#### Linux Tips
```html
https://dev.to/javinpaul/10-simple-linux-tips-which-save-50-of-my-time-in-the-command-line-4moo?utm_source=digest_mailer&utm_medium=email&utm_campaign=digest_email
```
#### Grep
```bash
grep -rnw '/path/to/somewhere/' -e 'pattern'
# -r or -R is recursive,
# -n is line number,
# -w stands for match the whole word,
# -l (lower-case L) can be added to just give the file name of matching files.
```
#### Get TBWritten
```bash
sudo smartctl -A /dev/sdb | awk '/^241/ { print "TBW: "($10 * 512) * 1.0e-12, "TB" } '
```


# ubuntu-debian-tricks
For calculating which sub-directories consume how much disk size, you can use this command:
```bash
du -h --max-depth=1 | sort -hr
```

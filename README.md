# ubuntu-debian-tricks
##For calculating which sub-directories consume how much disk size, you can use this command:
```bash
du -h --max-depth=1 | sort -hr
du -bsh * |sort -hr
```
##Get number of thread
##Num of threads by process
```bash
ps -o nlwp <pid>
```
##Sum of threads
```bash
ps -eo nlwp | tail -n +2 | awk '{ num_threads += $1 } END { print num_threads }'
```
##Max threads on server
```bash
cat /proc/sys/kernel/threads-max
```
##Restart printer service
```bash
sudo service cups restart
```
##Clear cache page
```bash
sync; echo 1 > /proc/sys/vm/drop_caches
```

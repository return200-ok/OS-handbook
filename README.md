# ubuntu-debian-tricks
 For calculating which sub-directories consume how much disk size, you can use this command:
```bash
du -h --max-depth=1 | sort -hr
du -bsh * |sort -hr
```
Get number of thread
Num of threads by process
```bash
ps -o nlwp <pid>
```
Sum of threads
```bash
ps -eo nlwp | tail -n +2 | awk '{ num_threads += $1 } END { print num_threads }'
```
Max threads on server= (max_threads = mempages / (8 * THREAD_SIZE / PAGE_SIZE);)
```bash
cat /proc/sys/kernel/threads-max
```
Restart printer service
```bash
sudo service cups restart
```
Clear cache page
```bash
sync; echo 1 > /proc/sys/vm/drop_caches
```
make some data change
```bash
rm -f data/file5
fallocate -l 10K data/file6
```

# Zoombie process
To kill a zombie (process) you have to kill its parent process (just like real zombies!), but the question was how to find it.

Find the zombie (The question answered this part):
```

a@SERVER:~$ ps aux | grep 'Z'
```

What you get is Zombies and anything else with a Z in it, so you will also get the grep:
```
USER       PID     %CPU %MEM  VSZ    RSS TTY      STAT START   TIME COMMAND
usera      13572   0.0  0.0   7628   992 pts/2    S+   19:40   0:00 grep --color=auto Z
usera      93572   0.0  0.0   0      0   ??       Z    19:40   0:00 something
```
Find the zombie's parent:
```
a@SERVER:~$ pstree -p -s 93572
```
Will give you:
```
init(1)---cnid_metad(1311)---cnid_dbd(5145)
```
In this case you do not want to kill that parent process and you should be quite happy with one zombie, but killing the immediate parent process 5145 should get rid of it.
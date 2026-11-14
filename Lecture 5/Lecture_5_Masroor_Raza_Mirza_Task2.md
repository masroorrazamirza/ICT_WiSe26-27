# Lecture 5 - Task 2: Search and Filter

## 1. Filter processes matching username (mmirza)
```bash
ps aux | grep mmirza
```
```text
root        1037  0.0  0.3   8760  5644 ?        Ss   16:43   0:00 login -- mmirza
mmirza      1321  0.0  0.7  22072 12836 ?        Ss   16:44   0:00 /usr/lib/systemd/systemd --user
mmirza      1324  0.0  0.2  23016  4116 ?        S    16:44   0:00 (sd-pam)
mmirza      1347  0.0  0.3   8856  5936 tty1     Ss+  16:44   0:00 -bash
root        1399  0.0  0.7  18272 12284 ?        Ss   16:50   0:00 sshd-session: mmirza [priv]
mmirza      1454  0.0  0.4  18568  7680 ?        S    16:50   0:00 sshd-session: mmirza@pts/0
mmirza      1455  0.0  0.3   8844  5868 pts/0    Ss   16:50   0:00 -bash
mmirza      1628  0.0  0.2   9764  4680 pts/0    R+   17:01   0:00 ps aux
mmirza      1629  0.0  0.1   6716  2680 pts/0    S+   17:01   0:00 grep --color=auto mmirza
```

## 2. Filter only processes running as mmirza (Regex)
```bash
ps aux | grep "^mmirza"
```
```text
mmirza      1321  0.0  0.7  22072 12836 ?        Ss   16:44   0:00 /usr/lib/systemd/systemd --user
mmirza      1324  0.0  0.2  23016  4116 ?        S    16:44   0:00 (sd-pam)
mmirza      1347  0.0  0.3   8856  5936 tty1     Ss+  16:44   0:00 -bash
mmirza      1454  0.0  0.4  18568  7680 ?        S    16:50   0:00 sshd-session: mmirza@pts/0
mmirza      1455  0.0  0.3   8844  5868 pts/0    Ss   16:50   0:00 -bash
mmirza      1640  0.0  0.2   9764  4680 pts/0    R+   17:01   0:00 ps aux
mmirza      1641  0.0  0.1   6716  2652 pts/0    S+   17:01   0:00 grep --color=auto ^mmirza
```

## 3. List all processes except root
```bash
ps aux | grep -v "^root"
```
```text
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
systemd+     564  0.0  0.8  22632 14636 ?        Ss   16:43   0:00 /usr/lib/systemd/systemd-resolved
systemd+     784  0.0  0.7  21436 12368 ?        Ss   16:43   0:00 /usr/lib/systemd/systemd-networkd
message+     970  0.0  0.3   9008  5612 ?        Ss   16:43   0:00 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
polkitd      979  0.0  0.5 306448  8456 ?        Ssl  16:43   0:00 /usr/lib/polkit-1/polkitd --no-debug --log-level=notice
_chrony     1046  0.0  0.6  23864 11252 ?        S    16:43   0:00 /usr/sbin/chronyd -n -F 1
syslog      1051  0.0  0.3 220548  6268 ?        Ssl  16:43   0:00 /usr/sbin/rsyslogd -n -iNONE
_chrony     1070  0.0  0.1  12096  2460 ?        S    16:43   0:00 /usr/sbin/chronyd -n -F 1
mmirza      1321  0.0  0.7  22072 12836 ?        Ss   16:44   0:00 /usr/lib/systemd/systemd --user
mmirza      1324  0.0  0.2  23016  4116 ?        S    16:44   0:00 (sd-pam)
mmirza      1347  0.0  0.3   8856  5936 tty1     Ss+  16:44   0:00 -bash
mmirza      1454  0.0  0.4  18568  7680 ?        S    16:50   0:00 sshd-session: mmirza@pts/0
mmirza      1455  0.0  0.3   8844  5868 pts/0    Ss   16:50   0:00 -bash
mmirza      1652  0.0  0.2   9764  4676 pts/0    R+   17:01   0:00 ps aux
mmirza      1653  0.0  0.1   6716  2668 pts/0    S+   17:01   0:00 grep --color=auto -v ^root
```

## 4. Filter out kworker and irq processes
```bash
ps aux | grep -vE "kworker|irq"
```
```text
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root           1  0.2  0.9  24856 16328 ?        Ss   16:43   0:02 /usr/lib/systemd/systemd --switched-root --system --deserialize=49
root           2  0.0  0.0      0     0 ?        S    16:43   0:00 [kthreadd]
root           3  0.0  0.0      0     0 ?        S    16:43   0:00 [pool_workqueue_release]
root          15  0.0  0.0      0     0 ?        I    16:43   0:00 [rcu_preempt]
root          16  0.0  0.0      0     0 ?        S    16:43   0:00 [rcu_exp_par_gp_kthread_worker/0]
root          17  0.0  0.0      0     0 ?        S    16:43   0:00 [rcu_exp_gp_kthread_worker]
root          18  0.0  0.0      0     0 ?        S    16:43   0:00 [migration/0]
root          19  0.0  0.0      0     0 ?        S    16:43   0:00 [kprobe-optimizer]
root          20  0.0  0.0      0     0 ?        S    16:43   0:00 [idle_inject/0]
root          21  0.0  0.0      0     0 ?        S    16:43   0:00 [cpuhp/0]
root          22  0.0  0.0      0     0 ?        S    16:43   0:00 [kdevtmpfs]
root          24  0.0  0.0      0     0 ?        I    16:43   0:00 [rcu_tasks_kthread]
root          25  0.0  0.0      0     0 ?        I    16:43   0:00 [rcu_tasks_rude_kthread]
root          26  0.0  0.0      0     0 ?        S    16:43   0:00 [kauditd]
root          27  0.0  0.0      0     0 ?        S    16:43   0:00 [khungtaskd]
root          28  0.0  0.0      0     0 ?        S    16:43   0:00 [oom_reaper]
root          32  0.0  0.0      0     0 ?        S    16:43   0:00 [kcompactd0]
root          33  0.0  0.0      0     0 ?        SN   16:43   0:00 [ksmd]
root          34  0.0  0.0      0     0 ?        SN   16:43   0:00 [khugepaged]
root          46  0.0  0.0      0     0 ?        S    16:43   0:00 [watchdogd]
root          48  0.0  0.0      0     0 ?        S    16:43   0:00 [kswapd0]
root          49  0.0  0.0      0     0 ?        S    16:43   0:00 [ecryptfs-kthread]
root          53  0.0  0.0      0     0 ?        S    16:43   0:00 [scsi_eh_0]
root          55  0.0  0.0      0     0 ?        S    16:43   0:00 [scsi_eh_1]
root         298  0.0  0.0      0     0 ?        S    16:43   0:00 [scsi_eh_2]
root         412  0.0  0.0      0     0 ?        S    16:43   0:00 [jbd2/dm-0-8]
root         507  0.0  0.0      0     0 ?        S    16:43   0:00 [psimon]
root         513  0.0  1.0  50652 17352 ?        S<s  16:43   0:00 /usr/lib/systemd/systemd-journald
root         546  0.0  0.5 279492  9644 ?        SLsl 16:43   0:00 /usr/sbin/multipathd -d -s
systemd+     564  0.0  0.8  22632 14636 ?        Ss   16:43   0:00 /usr/lib/systemd/systemd-resolved
root         566  0.0  0.8  40056 14236 ?        Ss   16:43   0:00 /usr/lib/systemd/systemd-udevd
root         585  0.0  0.0      0     0 ?        S    16:43   0:00 [psimon]
root         704  0.0  0.0      0     0 ?        S    16:43   0:00 [jbd2/sda2-8]
systemd+     784  0.0  0.7  21436 12368 ?        Ss   16:43   0:00 /usr/lib/systemd/systemd-networkd
root         968  0.0  0.1   2888  2008 ?        Ss   16:43   0:00 /bin/sh /usr/lib/systemd/scripts/chronyd-starter.sh -n -F 1
root         969  0.0  0.2   7060  3436 ?        Ss   16:43   0:00 /usr/sbin/cron -f -P
message+     970  0.0  0.3   9008  5612 ?        Ss   16:43   0:00 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
root         977  0.0  1.7  46744 30204 ?        Ss   16:43   0:00 /usr/bin/python3 /usr/bin/networkd-dispatcher --run-startup-triggers
polkitd      979  0.0  0.5 306448  8456 ?        Ssl  16:43   0:00 /usr/lib/polkit-1/polkitd --no-debug --log-level=notice
root         982  0.0  2.5 1780576 42184 ?       Ssl  16:43   0:00 /snap/snapd/current/usr/lib/snapd/snapd
root         986  0.0  0.5  18560  9608 ?        Ss   16:43   0:00 /usr/lib/systemd/systemd-logind
root         988  0.0  0.9 543452 15256 ?        Ssl  16:43   0:00 /usr/libexec/udisks2/udisksd
root        1016  0.0  0.4  10744  7832 ?        Ss   16:43   0:00 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups
root        1037  0.0  0.3   8760  5644 ?        Ss   16:43   0:00 login -- mmirza
_chrony     1046  0.0  0.6  23864 11252 ?        S    16:43   0:00 /usr/sbin/chronyd -n -F 1
syslog      1051  0.0  0.3 220548  6268 ?        Ssl  16:43   0:00 /usr/sbin/rsyslogd -n -iNONE
root        1058  0.0  1.9 126112 33004 ?        Ssl  16:43   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
_chrony     1070  0.0  0.1  12096  2460 ?        S    16:43   0:00 /usr/sbin/chronyd -n -F 1
root        1081  0.0  0.8 391608 14132 ?        Ssl  16:43   0:00 /usr/sbin/ModemManager
mmirza      1321  0.0  0.7  22072 12836 ?        Ss   16:44   0:00 /usr/lib/systemd/systemd --user
mmirza      1324  0.0  0.2  23016  4116 ?        S    16:44   0:00 (sd-pam)
mmirza      1347  0.0  0.3   8856  5936 tty1     Ss+  16:44   0:00 -bash
root        1399  0.0  0.7  18272 12284 ?        Ss   16:50   0:00 sshd-session: mmirza [priv]
mmirza      1454  0.0  0.4  18568  7680 ?        S    16:50   0:00 sshd-session: mmirza@pts/0
mmirza      1455  0.0  0.3   8844  5868 pts/0    Ss   16:50   0:00 -bash
mmirza      1664  0.0  0.2   9764  4696 pts/0    R+   17:01   0:00 ps aux
```

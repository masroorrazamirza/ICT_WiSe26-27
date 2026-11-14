# Lecture 5 - Task 3: Data Manipulation with sed and awk

## 1. Replace root with ROOT in processes.log
```text
USER         PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
ROOT           1  0.3  0.9  24856 16328 ?        Ss   16:43   0:02 /usr/lib/systemd/systemd --switched-root --system --deserialize=49
ROOT           2  0.0  0.0      0     0 ?        S    16:43   0:00 [kthreadd]
ROOT           3  0.0  0.0      0     0 ?        S    16:43   0:00 [pool_workqueue_release]
ROOT           4  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-rcu_gp]
ROOT           5  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-sync_wq]
ROOT           6  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-kvfree_rcu_reclaim]
ROOT           7  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-slub_flushwq]
ROOT           8  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-netns]
ROOT          13  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-mm_percpu_wq]
ROOT          14  0.0  0.0      0     0 ?        S    16:43   0:00 [ksoftirqd/0]
ROOT          15  0.0  0.0      0     0 ?        I    16:43   0:00 [rcu_preempt]
ROOT          16  0.0  0.0      0     0 ?        S    16:43   0:00 [rcu_exp_par_gp_kthread_worker/0]
ROOT          17  0.0  0.0      0     0 ?        S    16:43   0:00 [rcu_exp_gp_kthread_worker]
ROOT          18  0.0  0.0      0     0 ?        S    16:43   0:00 [migration/0]
ROOT          19  0.0  0.0      0     0 ?        S    16:43   0:00 [kprobe-optimizer]
ROOT          20  0.0  0.0      0     0 ?        S    16:43   0:00 [idle_inject/0]
ROOT          21  0.0  0.0      0     0 ?        S    16:43   0:00 [cpuhp/0]
ROOT          22  0.0  0.0      0     0 ?        S    16:43   0:00 [kdevtmpfs]
ROOT          23  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-inet_frag_wq]
ROOT          24  0.0  0.0      0     0 ?        I    16:43   0:00 [rcu_tasks_kthread]
ROOT          25  0.0  0.0      0     0 ?        I    16:43   0:00 [rcu_tasks_rude_kthread]
ROOT          26  0.0  0.0      0     0 ?        S    16:43   0:00 [kauditd]
ROOT          27  0.0  0.0      0     0 ?        S    16:43   0:00 [khungtaskd]
ROOT          28  0.0  0.0      0     0 ?        S    16:43   0:00 [oom_reaper]
ROOT          29  0.0  0.0      0     0 ?        I    16:43   0:00 [kworker/u4:1-events_power_efficient]
ROOT          30  0.0  0.0      0     0 ?        I    16:43   0:00 [kworker/u4:2-events_unbound]
ROOT          31  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-writeback]
ROOT          32  0.0  0.0      0     0 ?        S    16:43   0:00 [kcompactd0]
ROOT          33  0.0  0.0      0     0 ?        SN   16:43   0:00 [ksmd]
ROOT          34  0.0  0.0      0     0 ?        SN   16:43   0:00 [khugepaged]
ROOT          35  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-kblockd]
ROOT          36  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-blkcg_punt_bio]
ROOT          37  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-kintegrityd]
ROOT          38  0.0  0.0      0     0 ?        S    16:43   0:00 [irq/9-acpi]
ROOT          39  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-tpm_dev_wq]
ROOT          40  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-ata_sff]
ROOT          41  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-md_bitmap]
ROOT          42  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-md_llbitmap_io]
ROOT          43  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-md_llbitmap_unplug]
ROOT          44  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-edac-poller]
ROOT          45  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-devfreq_wq]
ROOT          46  0.0  0.0      0     0 ?        S    16:43   0:00 [watchdogd]
ROOT          47  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-quota_events_unbound]
ROOT          48  0.0  0.0      0     0 ?        S    16:43   0:00 [kswapd0]
ROOT          49  0.0  0.0      0     0 ?        S    16:43   0:00 [ecryptfs-kthread]
ROOT          50  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-kthrotld]
ROOT          51  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-acpi_thermal_pm]
ROOT          52  0.0  0.0      0     0 ?        I    16:43   0:00 [kworker/u4:3-flush-252:0]
ROOT          53  0.0  0.0      0     0 ?        S    16:43   0:00 [scsi_eh_0]
ROOT          54  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-scsi_tmf_0]
ROOT          55  0.0  0.0      0     0 ?        S    16:43   0:00 [scsi_eh_1]
ROOT          56  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-scsi_tmf_1]
ROOT          59  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/0:1H-kblockd]
ROOT          61  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-mld]
ROOT          62  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-ipv6_addrconf]
ROOT          63  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-kstrp]
ROOT          65  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/u5:0]
ROOT          76  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-charger_manager]
ROOT         298  0.0  0.0      0     0 ?        S    16:43   0:00 [scsi_eh_2]
ROOT         299  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-scsi_tmf_2]
ROOT         303  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/0:2H-kblockd]
ROOT         377  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-kdmflush/252:0]
ROOT         412  0.0  0.0      0     0 ?        S    16:43   0:00 [jbd2/dm-0-8]
ROOT         413  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-ext4-rsv-conversion]
ROOT         507  0.0  0.0      0     0 ?        S    16:43   0:00 [psimon]
ROOT         513  0.0  1.0  50652 17344 ?        S<s  16:43   0:00 /usr/lib/systemd/systemd-journald
ROOT         539  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-kmpathd]
ROOT         540  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-kmpath_handlerd]
ROOT         546  0.0  0.5 279492  9644 ?        SLsl 16:43   0:00 /usr/sbin/multipathd -d -s
systemd+     564  0.0  0.8  22632 14636 ?        Ss   16:43   0:00 /usr/lib/systemd/systemd-resolved
ROOT         566  0.0  0.8  40056 14236 ?        Ss   16:43   0:00 /usr/lib/systemd/systemd-udevd
ROOT         585  0.0  0.0      0     0 ?        S    16:43   0:00 [psimon]
ROOT         669  0.0  0.0      0     0 ?        S    16:43   0:00 [irq/18-vmwgfx]
ROOT         670  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-ttm]
ROOT         704  0.0  0.0      0     0 ?        S    16:43   0:00 [jbd2/sda2-8]
ROOT         705  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-ext4-rsv-conversion]
systemd+     784  0.0  0.7  21436 12368 ?        Ss   16:43   0:00 /usr/lib/systemd/systemd-networkd
ROOT         816  0.0  0.0      0     0 ?        I<   16:43   0:00 [kworker/R-cfg80211]
ROOT         968  0.0  0.1   2888  2008 ?        Ss   16:43   0:00 /bin/sh /usr/lib/systemd/scripts/chronyd-starter.sh -n -F 1
ROOT         969  0.0  0.2   7060  3436 ?        Ss   16:43   0:00 /usr/sbin/cron -f -P
message+     970  0.0  0.3   9008  5612 ?        Ss   16:43   0:00 @dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation --syslog-only
ROOT         977  0.0  1.7  46744 30204 ?        Ss   16:43   0:00 /usr/bin/python3 /usr/bin/networkd-dispatcher --run-startup-triggers
polkitd      979  0.0  0.5 306448  8456 ?        Ssl  16:43   0:00 /usr/lib/polkit-1/polkitd --no-debug --log-level=notice
ROOT         982  0.1  2.5 1780576 42164 ?       Ssl  16:43   0:00 /snap/snapd/current/usr/lib/snapd/snapd
ROOT         986  0.0  0.5  18560  9608 ?        Ss   16:43   0:00 /usr/lib/systemd/systemd-logind
ROOT         988  0.0  0.9 543452 15256 ?        Ssl  16:43   0:00 /usr/libexec/udisks2/udisksd
ROOT        1012  0.7  0.0      0     0 ?        I    16:43   0:05 [kworker/0:3-events]
ROOT        1016  0.0  0.4  10744  7832 ?        Ss   16:43   0:00 sshd: /usr/sbin/sshd -D [listener] 0 of 10-100 startups
ROOT        1037  0.0  0.3   8760  5644 ?        Ss   16:43   0:00 login -- mmirza
_chrony     1046  0.0  0.6  23864 11252 ?        S    16:43   0:00 /usr/sbin/chronyd -n -F 1
syslog      1051  0.0  0.3 220548  6264 ?        Ssl  16:43   0:00 /usr/sbin/rsyslogd -n -iNONE
ROOT        1058  0.0  1.9 126112 33004 ?        Ssl  16:43   0:00 /usr/bin/python3 /usr/share/unattended-upgrades/unattended-upgrade-shutdown --wait-for-signal
_chrony     1070  0.0  0.1  12096  2460 ?        S    16:43   0:00 /usr/sbin/chronyd -n -F 1
ROOT        1081  0.0  0.8 391608 14132 ?        Ssl  16:43   0:00 /usr/sbin/ModemManager
mmirza      1321  0.0  0.7  22072 12836 ?        Ss   16:44   0:00 /usr/lib/systemd/systemd --user
mmirza      1324  0.0  0.2  23016  4116 ?        S    16:44   0:00 (sd-pam)
mmirza      1347  0.0  0.3   8856  5936 tty1     Ss+  16:44   0:00 -bash
ROOT        1398  0.0  0.0      0     0 ?        I    16:50   0:00 [kworker/0:0-ata_sff]
ROOT        1399  0.0  0.7  18272 12284 ?        Ss   16:50   0:00 sshd-session: mmirza [priv]
mmirza      1454  0.0  0.4  18568  7680 ?        R    16:50   0:00 sshd-session: mmirza@pts/0
mmirza      1455  0.0  0.3   8844  5868 pts/0    Ss   16:50   0:00 -bash
ROOT        1527  0.0  0.0      0     0 ?        I    16:55   0:00 [kworker/u4:0-ext4-rsv-conversion]
mmirza      1575  100  0.2   9764  4708 pts/0    R+   16:57   0:00 ps aux
103 processes are running
```

## 2. Users with UID and GID from /etc/passwd
```text
User root has UID 0 and GID 0
User daemon has UID 1 and GID 1
User bin has UID 2 and GID 2
User sys has UID 3 and GID 3
User sync has UID 4 and GID 65534
User games has UID 5 and GID 60
User man has UID 6 and GID 12
User lp has UID 7 and GID 7
User mail has UID 8 and GID 8
User news has UID 9 and GID 9
User uucp has UID 10 and GID 10
User proxy has UID 13 and GID 13
User www-data has UID 33 and GID 33
User backup has UID 34 and GID 34
User list has UID 38 and GID 38
User irc has UID 39 and GID 39
User _apt has UID 42 and GID 65534
User nobody has UID 65534 and GID 65534
User systemd-network has UID 998 and GID 998
User dhcpcd has UID 997 and GID 997
User messagebus has UID 996 and GID 996
User systemd-resolve has UID 990 and GID 990
User _chrony has UID 989 and GID 989
User usbmux has UID 100 and GID 46
User polkitd has UID 988 and GID 988
User syslog has UID 101 and GID 103
User uuidd has UID 102 and GID 104
User tcpdump has UID 986 and GID 986
User tss has UID 985 and GID 985
User landscape has UID 103 and GID 106
User fwupd-refresh has UID 984 and GID 984
User mmirza has UID 1000 and GID 1000
User sshd has UID 983 and GID 65534
```

## 3. Username and process name from processes.log
```text
USER COMMAND
root /usr/lib/systemd/systemd
root [kthreadd]
root [pool_workqueue_release]
root [kworker/R-rcu_gp]
root [kworker/R-sync_wq]
root [kworker/R-kvfree_rcu_reclaim]
root [kworker/R-slub_flushwq]
root [kworker/R-netns]
root [kworker/R-mm_percpu_wq]
root [ksoftirqd/0]
root [rcu_preempt]
root [rcu_exp_par_gp_kthread_worker/0]
root [rcu_exp_gp_kthread_worker]
root [migration/0]
root [kprobe-optimizer]
root [idle_inject/0]
root [cpuhp/0]
root [kdevtmpfs]
root [kworker/R-inet_frag_wq]
root [rcu_tasks_kthread]
root [rcu_tasks_rude_kthread]
root [kauditd]
root [khungtaskd]
root [oom_reaper]
root [kworker/u4:1-events_power_efficient]
root [kworker/u4:2-events_unbound]
root [kworker/R-writeback]
root [kcompactd0]
root [ksmd]
root [khugepaged]
root [kworker/R-kblockd]
root [kworker/R-blkcg_punt_bio]
root [kworker/R-kintegrityd]
root [irq/9-acpi]
root [kworker/R-tpm_dev_wq]
root [kworker/R-ata_sff]
root [kworker/R-md_bitmap]
root [kworker/R-md_llbitmap_io]
root [kworker/R-md_llbitmap_unplug]
root [kworker/R-edac-poller]
root [kworker/R-devfreq_wq]
root [watchdogd]
root [kworker/R-quota_events_unbound]
root [kswapd0]
root [ecryptfs-kthread]
root [kworker/R-kthrotld]
root [kworker/R-acpi_thermal_pm]
root [kworker/u4:3-flush-252:0]
root [scsi_eh_0]
root [kworker/R-scsi_tmf_0]
root [scsi_eh_1]
root [kworker/R-scsi_tmf_1]
root [kworker/0:1H-kblockd]
root [kworker/R-mld]
root [kworker/R-ipv6_addrconf]
root [kworker/R-kstrp]
root [kworker/u5:0]
root [kworker/R-charger_manager]
root [scsi_eh_2]
root [kworker/R-scsi_tmf_2]
root [kworker/0:2H-kblockd]
root [kworker/R-kdmflush/252:0]
root [jbd2/dm-0-8]
root [kworker/R-ext4-rsv-conversion]
root [psimon]
root /usr/lib/systemd/systemd-journald
root [kworker/R-kmpathd]
root [kworker/R-kmpath_handlerd]
root /usr/sbin/multipathd
systemd+ /usr/lib/systemd/systemd-resolved
root /usr/lib/systemd/systemd-udevd
root [psimon]
root [irq/18-vmwgfx]
root [kworker/R-ttm]
root [jbd2/sda2-8]
root [kworker/R-ext4-rsv-conversion]
systemd+ /usr/lib/systemd/systemd-networkd
root [kworker/R-cfg80211]
root /bin/sh
root /usr/sbin/cron
message+ @dbus-daemon
root /usr/bin/python3
polkitd /usr/lib/polkit-1/polkitd
root /snap/snapd/current/usr/lib/snapd/snapd
root /usr/lib/systemd/systemd-logind
root /usr/libexec/udisks2/udisksd
root [kworker/0:3-events]
root sshd:
root login
_chrony /usr/sbin/chronyd
syslog /usr/sbin/rsyslogd
root /usr/bin/python3
_chrony /usr/sbin/chronyd
root /usr/sbin/ModemManager
mmirza /usr/lib/systemd/systemd
mmirza (sd-pam)
mmirza -bash
root [kworker/0:0-ata_sff]
root sshd-session:
mmirza sshd-session:
mmirza -bash
root [kworker/u4:0-ext4-rsv-conversion]
mmirza ps
103 
```

## 4. Total CPU usage sum
```text
Total CPU usage: 101.1%
```

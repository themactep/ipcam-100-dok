---
lang: eo
lang-niv: auto
lang-ref: 071-originala_firmvaro
layout: page
title: 'Originala firmvaro'
---

# malfermaj havenoj

TCP: 80(http), 443(HTP ankaŭ!), 554(RTSP), 8004, 8006, 9527(Telnetd), 9999  
UDP: 67(DHCP), 3702, 8002, 39642

Haveno 80: HTTP  
http: // ip: ensaluto: _admin:_, pasvorto: _admin_

Haveno 443: HTTP  
http: // ip: 443: ensaluto: _admin:_, pasvorto: _admin_

Haveno 554: RTSP  
* Ĉefa fluo: 


    ```
    IP=xxx.xxx.xxx.xxx
    ffplay -i rtsp://admin:admin@$IP/stream1
    ffplay -i rtsp://admin:admin@$IP/mpeg4/ch0/main/av_stream


    ```
* flux secondaire :


    ```
    IP=xxx.xxx.xxx.xxx
    ffplay -i rtsp://admin:admin@$IP/stream2
    ffplay -i rtsp://admin:admin@$IP/mpeg4/ch1/main/av_stream
    ````

haveno 8004 :? , malfermita de jco_server


haveno 8006 :? , malfermita de jco_server



Haveno 9527: Telnet  
`telnetd IP 9527` : Ensalutu: _root_, pasvorto: _jco66688_, alirebla dum 5 minutoj, fermiĝis post.  
Ne esti malkonektita post 5 minutoj: `killall -9 auto_run.sh`  
Ĉesi JCO_server : 
 

```
killall -9 auto_run.sh
killall -9 jco_server;echo 'V'>/dev/watchdog;echo 'V'>/dev/watchdog0
```

haveno 9999: uzata por regi la fotilon, ekzemplo:

```
IP=xxx.xxx.xxx.xxx
echo "checkuser -act set -user admin -password admin" | nc $IP 9999
echo "list" | nc $IP 9999
echo "pelcod20ctrl -?" | nc $IP 9999
echo "pelcod20ctrl -type 1" | nc $IP 9999
```

UDP 67: malfermita de udhcpd

UDP 3702 :? , malfermita de jco_server



# interna fulmmemoro
Fulmmemoro estas dispartigita jene:

poentaro | priskribo |
--- | --- |
mtdblock0 | u-startŝargilo |
mtdblock1 | boot config |
mtdblock2 | u-boot hereda uImage, linux-kerno |
mtdblock3 | kukurboj = / |
mtdblock4 | squashfs, muntita sur / ipc |
mtdblock5 | jffs2, muntita sur / opt |

u-boot (subdisko mtdblock0) ŝarĝas la kernon en mtdblock2.  
defaŭltaj opcioj en u-startŝargilo:  
* bootargs = konzolo = ttyS1,115200n8 mem = 43M @ 0x0 rmem = 21M @ 0x2B00000 init = / linuxrc rootfstype = squashfs root = / dev / mtdblock3

* bootcmd = sf probe; sf read 0x80600000 0x48000 0x280000; bootm 0x80600000

* bootdelay = 1

* baudrate = 115200

* ŝarĝoj\_eoo = 1

* ethaddr = 00: 11: 22: 33: 44: 74

* ipaddr = 192.168.2.84

* serverip = 192.168.2.81

* gatewayip = 192.168.2.1

* retmasko = 255.255.255.0


opcioj en mtdblock1:
* baudrato = 115200
* bootcmd = sf probe; sf read 0x80600000 0x48000 0x280000; bootm 0x80600000
* bootdelay = 1
* ethact = Jz4775-9161
* gatewayip = 192.168.2.1
* ipaddr = 192.168.2.84
* ŝarĝoj\_eoo = 1
* retmasko = 255.255.255.0
* serverip = 192.168.2.81
* stderr = seria
* stdin = seria
* stdout = seria
* ethaddr =**:**:**:**:**:**
* aparato\_id =***********
* devinfo = jcoxa***************************************************
* bootargs = konzolo = ttyS1,115200n8 mem = 42M @ 0x0 rmem = 22M @ 0x2A00000 init = / linuxrc rootfstype = squashfs root = / dev / mtdblock3 flash = SF sensor = GC2053 maxheight = 1080 device\_id =*********** ethaddr =**:**:**:**:**:** devinfo = jcoxa*************************************************** cpu = T21 ddr = 64M mtdparts = jz\_sfc: 256K @ 0K(sf-bootloader), 32K @ 256K(sf-bootenv), 1440K @ 288K(sf-kernel), 832K @ 1728K(sf-rootfs), 4928K @ 2560K(sf-ipcfs), 704K @ 7488 K(sf-miscfs)


linuksa versio:  
Linukso-versio 3.10.14\_\_isvp\_meleagro\_1.0\_\_ (root@localhost.localdomain) (gcc-versio 4.7.2 (Ingenic r2.3.3 2016.12) ) # 3 PREEMPT Sab Jun 22 10:40:55 CST 2019


Rimarkindaj dosieroj en /:
* _/bin/busybox_ : 
  *     [, [[, cindro, awk, base64, baznomo , blockdev, bootchartd, bunzip2, bzcat, bzip2, cat, chmod, chown, cmp, cp, cut, date, dd, depmod, devmem, df,
  *     dhcprelay, diff, dirname, dmesg , dnsdomainname, du, dumpleases, echo, egrep, expr, fdflush, fdformat, fdisk, fgrep, find, flash\_eraseall,
  *     grego, libera, fandilo, getty, grep , gzip, halt, hd, head, hexdump, hostname, hwclock, ifconfig, init, insmod, iostat, kill, killall, klogd, less,
  *     linuxrc, ln, logger, login, logread , ls, lsmod, md5sum, mdev, mesg, mkdir, mkdosfs, mkfs.vfat, mknod, mktemp, modinfo, modprobe, mount,
  *     montopunkto, mpstat, mv, nc, netstat, passwd , ping, pmap, poweroff, powertop, printf, ps, pstree, pwd, pwdx, readahead, reboot, rev, rm, rmdir,
  *     rmmod, itinero, sed, sh, dormo, smemcap , ordigi, stat, kordoj, interŝanĝi, interŝanĝi, sinkronigi, sistemon, sistemon, voston, gudron, ekrankopion, telnet, teston, tftp, tempon,
  *     paŭzo, supro, tuŝo, tr, vera, tty, udhcpc, udhcpd, umount, unxz, unzip, uptime, uzantoj, usleep, vi, volname, watch, wc, kiu, xargs, xz ,
  *     xzcat

* / lib: normaj bibliotekoj.


rimarkindaj dosieroj en _/ipc_ :
* _/ipc/app/jco\_server_
  * ĉefa programo, farita samtempe servilo http, rtsp, ...
* _/ipc/drv_ : linux-peliloj
  * motor.ko
* _/ipc/lib_ : bibliotekoj
  * libimp.so: biblioteko _ingenic_ _IMP_ ( _Ingenic Media Platform_ )


**noto: libimp.so diferencas de tiu liverita por la T20, kaj tiu liverita kun la T20 ne taŭgas.**

# GPIO-havenoj

* havenoj blokitaj de motor.ko: 18? 38 39 40 41 47 48 49 60?

* havenoj blokitaj de audio.ko: 63?

* haveno 46 = infraruĝaj LED-oj.

* haveno 52 =?

* haveno 64 =?

* haveno 81 = bluaj LEDoj.


# Kerna recenzo:
(° 1 ° Informo:
    `binwalk mtdblock2.bin`
    * Rezulto:
decimala deksesuma priskribo
--------------------------------------------------------------------------------
0 0x0 Uimage Header, Header Grandeco: 64 Bajtoj, Header CRC: 0x7b9DE864, kreita: 2019-06-22 02:41:00, Bildo Grandeco: 1466358 BYTES, DATA Adreso: 0x80010000, Eniro Punkto: 0x80388340, Datumoj CRC: 0xb83DCA15, OS: Linukso, CPU: MIPS, Bildo Tipo: OS Kernel Bildo, Kunpremo Tipo: LZMA, Bildo Nomo: "Linukso-3.10.14__. 1.0__]"(° 7 ° 7 ° 64 0x40 lzma kunpremitaj datumoj, ecoj: 0x5d, vortaro Grandeco: 16777216 bajtoj, nekompresita grandeco: -1 bajtoj

(° 1 ° eltiro de datumoj de MTDBlock2:
    `tail -c+65  < mtdblock2.bin >mtdblock2.dataz`

Kerna eltiro:
    `cat mtdblock2.dataz|lzma -d -c -f - >kernel`
(° 13 ° ° Listo de ŝoforoj inkluzivita:    `strings kernel|grep "^drivers"`

Listo de dosieroj:
    `strings kernel|grep "\.[cChTsS]$"`









(° 30 ° ° 31 ° Listo de simboloj (° 32 ° 32 ° Https://github.com/marin-m/vmlinux-to-lf devus permesi trovi la simbolojn, sed ĝi ne atingas
. Tablo_token_: 0x3AA1B4

# mk-livestatus_nagios-4.5

We are running Nagios 4.5 and Thruk 3.18 with Livestatus 1.5 (mk-livestatus-1.5.0p25).
We upgraded Nagios from 4.4 to 4.5 recently and it broke livestatus. Everything started correctly, but at some point it did a SIG_SEGV.
this can also be checked with the following :
```bash
echo "GET hosts" | /usr/local/bin/unixcat /opt/nagios/sock/live.sock
echo "GET services" | /usr/local/bin/unixcat /opt/nagios/sock/live.sock
```
both commands will return null and will crash the nagios daemon with a SIGSEGV.

you can download the files here or go to the official website and download the latest version available : https://download.checkmk.com/checkmk/1.5.0p25/mk-livestatus-1.5.0p25.tar.gz
then download the fix.patch file and run the following command from the mk-livestatus-1.5.0p25 directory.

```bash
patch -p0 < fix.patch
```

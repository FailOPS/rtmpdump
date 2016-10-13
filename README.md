rtmpdump for nicolive timeshift recording
======================================
Supports recording for live broadcasts at http://live.nicovideo.jp

Nicolive has 3 different type of providers where each provider type could either be a live or timeshifted video.

In total, there are 6 type of videos:
- official live video
- official timeshifted video
- channel live video
- channel timeshifted video **(tested)**
- Community live video
- Community timeshifted video **(tested)**

Modifications
=========================================
Added AMF parameters to support nlPlayNotice command for nicolive.

Some modifications are based on https://github.com/silenvx/PKGBUILD/blob/master/rtmpdump/nico_live.patch

Install
==============================================
Environment: Ubuntu 14.04
```
    cd rtmpdump-ksv-nicolive
    make
    sudo make install
```

Usage
=================================================
Community
```
rtmpdump -vr <rtmp><url></url></rtmp>/lv[id] -N <stream><quesheet><que></que></quesheet></stream> -C S:<rtmp><ticket></ticket></rtmp> -o out.flv

Example:
rtmpdump -vr rtmp://nleu22.live.nicovideo.jp:1935/liveedge/ts_150509_00_0 -C S:151356:lv200000000:0:1430000000:28078a7a50bca2d4 -N rtmp://nlpoca143.live.nicovideo.jp:1935/fileorigin/ts_00,/content/20150506/lv200000000_224815576000_3_3d715a.f4v?1430000000:30:98f4e9bc83f491f1 -o out.flv
```

Channel
```
rtmpdump -r <rtmp><url></url></rtmp> -y mp4:/<stream><quesheet><que></que></quesheet></stream> -C S:<rtmp><ticket></ticket></rtmp> -e -o out.flv

Example:
rtmpdump -r rtmp://nlace01.live.nicovideo.jp:1935/fileorigin/00 -y mp4:/content/150509/lv200000000_203510899000_2_1eb707.f4v -C S:151356:lv200000000:0:1430000000:067e232cc6900011 -e -o outflv
```

Get parameters by using getplayerstatus API - http://watch.live.nicovideo.jp/api/getplayerstatus?v=

References: http://nico-lab.net/nicolive_rtmpdump_commands

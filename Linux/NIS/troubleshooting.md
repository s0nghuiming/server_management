## User name can't disappear.

Last login: Tue Aug 10 11:03:45 2021 from 10.112.228.162
/usr/bin/id: cannot find name for user ID 1184
/usr/bin/id: cannot find name for group ID 1185
/usr/bin/id: cannot find name for user ID 1184
[I have no name!@mlp-spr-04 ~]$

Phenomenon:
- Service of ypbind is running. 
- Domainname is correct.
- ls /var/yp/binding shows some files of domainname like mlt-network.1 , mlt-network.2 , ...
- On one client shows the error, but other clients are normal.
- yptest seems normal
  Test 1: domainname
Configured domainname is "mlt-network"

Test 2: ypbind
Use Protocol V1: Used NIS server: 10.239.60.4
Use Protocol V2: Used NIS server: 10.239.60.4
Use Protocol V3:
ypbind_nconf:
        nc_netid: udp
        nc_semantics: 1
        nc_flag: 1
        nc_protofmly: 'inet'
        nc_proto: 'udp'
        nc_device: '-'
        nc_nlookups: 0
ypbind_svcaddr: 10.239.60.4:983
ypbind_servername: 10.239.60.4
ypbind_hi_vers: 2
ypbind_lo_vers: 2

Test 3: yp_match
WARNING: No such key in map (Map passwd.byname, key nobody)

Test 4: yp_first
a a:$6$n/d96nal$tLpnGHWnezsAp8B6gR0RKIZOI1/qjBAocACFC07x4Er9ZvgSWeDxxQBLbLDljHRWRx6XSq.cMfhWQqd2ZYIKr/:1146:1147::/home/a:/bin/bash

Test 5: yp_next
a a:$6$DPrNCG10$N3XHpHn8S9XYjpyUEVv9dgPA7weav2wFp/p80T.eUzCNekb1SVbTEIfptVabpeHUrfhsme4J8yOVklzeo/KRw/:1219:1220::/home2/a:/bin/bash
b b:$6$XiTHC3VB$YDN79A8/oP8BrdApe/U4nABcLnHx1ygGzXvTECbDSVu796KfqI8YOW8kMt2T5/b3cPjL.cI5QPCyqW5gLfjZc1:1241:1242::/home2/b:/bin/bash

Test 6: yp_master
mlt-ace

Test 7: yp_order
1628562101

Test 8: yp_maplist
passwd.byname
group.byname
passwd.byuid
group.bygid
hosts.byaddr
hosts.byname
netid.byname
mail.aliases
protocols.byname
protocols.bynumber
services.byservicename
services.byname
rpc.bynumber
rpc.byname
ypservers

Test 9: yp_all
a a:$6$n/d96nal$tLpnGHWnezsAp8B6gR0RKIZOI1/qjBAocACFC07x4Er9ZvgSWeDxxQBLbLDljHRWRx6XSq.cMfhWQqd2ZYIKr/:1146:1147::/home/a:/bin/bash
b b:$6$DPrNCG10$N3XHpHn8S9XYjpyUEVv9dgPA7weav2wFp/p80T.eUzCNekb1SVbTEIfptVabpeHUrfhsme4J8yOVklzeo/KRw/:1219:1220::/home2/b:/bin/bash


1
# Add user
# QOS is comma separated.
USER=
QOS=dev # as default, or ask shufan to confirm it.
# QOS= # as default

useradd $USER
passwd $USER
pushd /var/yp; make; popd
echo y | sacctmgr add user $USER DefaultAccount=mlt
sacctmgr -i modify user $USER set GrpTRES=node=4 GrpJobs=1 GrpSubmitJobs=1 qos+=$QOS

#
# cluster user approved on 
Hi ,
You have granted a new account to login to .
User name is <> with password 1.
QOS is dev.

You can use your account to login by:      ssh  <>@
to issue jobs with your QoS by:            srun  -p <partition>  --qos dev  --pty bash
in which partition name can be gotten from the 1st column of ‘sinfo’.

If meet any problem when you are using , feel free to let us know. We’ll respond you a.s.a.p.
Kind remind that vscode is not allowed on cluster center or on cluster nodes.

# blue
# cluster user approved on 
Hi ,

You have granted a new account to login to .
User name is <> with password 1.
QOS is dev.

You can use your account to login by:      ssh  <>@
to issue jobs with your QoS by:            srun  -p <partition>  --qos dev  --pty bash
in which partition name can be gotten from the 1st column of ‘sinfo’.

If meet any problem when you are using , feel free to let us know. We’ll respond you a.s.a.p.
Kind remind that vscode is not allowed on cluster center or on cluster nodes.


# new
# cluster user approved on 

You have granted a new account to login to .

Username: 
Password: 1
QoS: dev

Use the following steps to get in a compute node:
1. You can use your account to login by:            ssh  <username>@
2. Get idle node’s partition by:                    sinfo                                # the 1st column is partition name.
3. Issue jobs with your QoS by:                     salloc -N1 -p <partition> --qos dev  # <partition> is from sinfo
•	If there is idle node in partition, you can go directly to next step.
•	If there is no idle node in partition, command will hung until idle node appears.
4. Find the job ID and compute node name:           squeue | grep <username>
5. Ssh to computer node:                            ssh <node name>                      # <node name> is from output of squeue

If meet any problem when you are using , feel free to let us know. We’ll respond you a.s.a.p.
Kind remind that vscode is not allowed on cluster center or on cluster nodes.




# docker permission
usermod -aG docker username
systemctl restart docker

# to remove the user from docker. NEED re-login to enable.
gpasswd -G docker username
gpasswd -d username docker



# Env on cluster
Hi.

Here is a list of required software and how to setup the environment.

1. conda
$ sh Anaconda3-5.0.0.1-Linux-x86_64.sh
It will prompt to ask some questions, just please follow the hints from screen.

Do you accept the license terms? [yes|no]
[no] >>> yes


Anaconda3 will now be installed into this location:
/home2//anaconda3

  - Press ENTER to confirm the location
  - Press CTRL-C to abort the installation
  - Or specify a different location below

[/home2//anaconda3] >>> /home2//anaconda3-2

Do you wish to proceed with the installation of Microsoft VSCode? [yes|no]
>>> no

After the completion of installation, as hint says, enable the conda env by typing:
export PATH=/home2//anaconda3-2/bin:$PATH


2. gcc
We provide 4 versions of GCC. They can be enabled by the scl command as below.

# Default GCC 4
gcc --version

# To enable GCC 5
scl enable devtoolset-4 bash
gcc --version

# To enable GCC 6
scl enable devtoolset-6 bash
gcc --version

# To enbale GCC 7
scl enable devtoolset-7 bash
gcc --version




# Nodes list

# User list


recovery/拔电池upgrade bios恢复recovery/拔电池  bios setup load default/set os imagereboot
基本是按照这个顺序。

cd /opt/intel/vtune_amplifier_2019/sepdk/src 
./insmod-sep
 

# mpi what?
source /opt/intel/compilers_and_libraries/linux/bin/compilervars.sh intel64 
mpiexec.hydra -n 2 -ppn 1 -hosts 192.169.20.15,192.169.20.17 hostname 

# nfs remount
sed -i "s/\s\+nfs\s\+rsize=32768,wsize=32768,async,auto/ nfs sync,vers=4.0,auto/" /etc/fstab && cat /etc/fstab
umount -f -l /opt /home && mount -a && mount


for nd in $nodes; do if [ "$(state $nd)" == "idle" ]; then srun -p $(part $nd) -N1 -w $nd bash /opt/mng/remount; else echo "passing by $nd"; fi; done

# NFS client list 
netstat -an | grep 192.169.10.3:2049 | awk -F' ' '{ print $5 }' | cut -d':' -f1 | sort | uniq


# MESSAGE BOX
mmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmm
d                                                         b
d                                                         b
d     Warning! ! !                                        b
d                                                         b
d       This window is under test of Data preparing.      b
d       Please don't close it.                            b
d                                                         b
d                                                         b
d                                                         b
mmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmmm


─━│┃╌╍╎╏┄┅┆┇┈┉┊┋┌┍┎┏┐┑┒┓└┕┖┗┘┙┚┛├┝┞┟┠┡┢┣┤┥┦┧┨┩┪┫┬┭┮┯┰┱┲┳┴┵┶┷┸┹┺┻┼┽┾┿╀╁╂╃╄╅╆╇╈╉╊╋╪╫╬═║╒╓╔╕╖╗╘╙╚╛╜╝╞╟╠╡╢╣╤╥╦╧╨╩╔╗╝╚╬═╓╩┠┨┯┷┏┓┗┛┳⊥﹃﹄┌╮╭╯╰╳


# General replies for users' requests.
## 1. account new add
Generally one account on one cluster, but if you indeed have the request, you can email to Shufan to ask one on both clusters.


# Commands

# parse all nodes except for some nodes                                                                                 | * hop node ignore!
for id in $(sinfo -O all | grep -Po "mlt-\w+" | sort | uniq | grep -Po "[1-9]\d+" | grep -v 190 ); do ssh 192.168.10.${id} "hostname" 2>/dev/null; done

# check mount point
for id in $(sinfo -O all | grep -Po "mlt-\w+" | sort | uniq | grep -Po "[1-9]\d+" | grep -v 190 ); do ssh 192.168.10.${id} "if [ 1 -eq $(df -h | grep /lustre | wc -l) ]; then echo -n; else hostname; fi" 2>/dev/null; done

## blue
for id in $(sinfo -O all | grep -Po "mlt2-\w+" | sort | uniq | grep -Po "[1-9]\d+" ); do ssh 192.169.10.${id} "hostname" 2>/dev/null; done



# Get node list
sinfo -O all | grep -Po "mlt-\w+" | sort | uniq
sinfo -O nodehost,partition,statelong

# Get all associations with format 
sacctmgr show association format=User%20,GrpJobs,GrpTRES,GrpSubmit,QOS%80


# history of job
sacct --starttime 2019-10-18 --format=User,JobID,Jobname,partition,state,time,start,end,elapsed,MaxRss,MaxVMSize,nnodes,ncpus,nodelist | less


sacctmgr -i modify user $USER set GrpTRES=node=8 GrpJobs=1 GrpSubmitJobs=1 qos+=$QOS


sacctmgr -i modify qos long set GrpTRES=node=8 MaxTRES=node=8 

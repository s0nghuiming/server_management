# clear buff/cache 
#free# shows many memory space is occupied by buff/cache. Execute the command to release them.
echo 3 >/proc/sys/vm/drop_caches 

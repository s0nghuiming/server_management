# Memory settings on performance

## clear buff/cache 
"free" shows many memory space is occupied by buff/cache. Execute the command to release them.
```bash
echo 3 >/proc/sys/vm/drop_caches
```

### more about free on buff/cache
You don't need to free "buff/cache".

"buff/cache" is memory that Linux uses for disk caching, and that will be freed when applications require it. So you don't have to worry if a large amount is being shown in this field, as it doesn't count as "used" memory.

Quoted from http://www.linuxatemyram.com (emphasis mine):

Both you and Linux agree that memory taken by applications is "used", while memory that isn't used for anything is "free".

But how do you count memory that is currently used for something, but can still be made available to applications?

You might count that memory as "free" and/or "available". Linux instead counts it as "used", but also "available". (...) This "something" is (roughly) what top and free calls "buffers" and "cached". Since your and Linux's terminology differs, you might think you are low on ram when you're not.


# CPU settings on performance

## Intel CPU governor
```bash
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor  # show current governor
cpupower frequency-set -g performance  # set governor to performance
```

# BIOS settings on performance

## Intel BIOS tool (syscfg)
url: https://www.intel.com/content/dam/support/us/en/documents/server-products/server-boards/intel-syscfg-userguide-v1-03.pdf

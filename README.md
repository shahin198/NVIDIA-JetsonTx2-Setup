# NVIDIA-JetsonTx2-Setup
How to setup nvidia jetsonTx2
# Flowing link JetsonTx2 install step by step
https://docs.nvidia.com/jetpack-l4t/index.html#jetpack/3.2.1/install.htm

https://www.youtube.com/watch?v=D7lkth34rgM

# Enable CPU
```
# To see what is enabled:
sudo cat /sys/devices/system/cpu/online
# To see available modes:
sudo nvpmodel -p --verbose
# Set performance:
sudo nvpmodel -m0
# Also:
sudo /home/nvidia/jetson_clocks.sh


Try your test when all cores are guaranteed online.

Consider also that unless you specifically force a given core that the scheduler may be picking the best core. The obvious answer to always use all cores may not actually be the correct answer. The problem is that cache has a lot to do with performance, and a cache miss is very expensive relative to a cache hit. If the threads share data it may be a case of the scheduler trying to take advantage of cache. Whether you would want to override this or not might depend on whether you believe it is compute bound or if it is instead data bound as the speed bottleneck. Once all cores are enabled you probably need to profile before you try to outguess the scheduler.
```
# GPU View
```
sudo ~/tegrastats

sudo ~/jetson_clocks.sh --show
```

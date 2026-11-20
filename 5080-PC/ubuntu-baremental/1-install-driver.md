# Install Driver
## Get Available Drivers 
```ubuntu-driver devices``` 

-open: recommended for > Blackwell on linux

-server: recommended for date center 
## Install Driver
```apt install nvidia-driver-595-open ```

Why not .run downloaded from Nvidia - .run will break when upgrading kernel

apt version install with DKMS, will re-compile when kernel upgrade

## MOK Registry (Required When Secure Boot Enabled)
Enroll MOK -> Continue -> Password -> Reboot

# Nvidia-smi Output
## Sample
```
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 595.99.02              Driver Version: 595.99.02      CUDA Version: 13.2     |
+-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 5080        Off |   00000000:01:00.0  On |                  N/A |
|  0%   38C    P8             24W /  360W |    1106MiB /  16303MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI              PID   Type   Process name                        GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A            1823      G   /usr/lib/xorg/Xorg                      400MiB |
|    0   N/A  N/A            2039      G   /usr/bin/gnome-shell                    137MiB |
|    0   N/A  N/A            2630      G   ...exec/xdg-desktop-portal-gnome          6MiB |
|    0   N/A  N/A           13665      G   /usr/bin/nautilus                        24MiB |
|    0   N/A  N/A           14736      G   ...nap-store/1270/bin/snap-store         45MiB |
|    0   N/A  N/A           15045      G   /usr/bin/FlClash                        128MiB |
|    0   N/A  N/A           23821      G   .../6565/usr/lib/firefox/firefox        192MiB |
|    0   N/A  N/A           26163      G   ...3/log/jcef_chromium_25809.log          8MiB |
+-----------------------------------------------------------------------------------------+
```
## Key INFO 
1: Driver Version

2: CUDA Version

3: GPU name

4: Power Usage

5: GPU-util

6: Memory Usage

7: Processes

# Nvidia-smi -topo -m
## Sample
```
	GPU0	CPU Affinity	NUMA Affinity	GPU NUMA ID
GPU0	 X 	0-15	0		N/A

Legend:

  X    = Self
  SYS  = Connection traversing PCIe as well as the SMP interconnect between NUMA nodes (e.g., QPI/UPI)
  NODE = Connection traversing PCIe as well as the interconnect between PCIe Host Bridges within a NUMA node
  PHB  = Connection traversing PCIe as well as a PCIe Host Bridge (typically the CPU)
  PXB  = Connection traversing multiple PCIe bridges (without traversing the PCIe Host Bridge)
  PIX  = Connection traversing at most a single PCIe bridge
  NV#  = Connection traversing a bonded set of # NVLinks
```
## Key INFO 
1: Single card and single NUMA on my PC
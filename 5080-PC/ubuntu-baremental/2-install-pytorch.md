# PyTorch Registry
https://pytorch.org/get-started/locally/

# Check Supported GPU Arch
```
import torch
print(torch.cuda.get_arch_list())
```
ouptput ```['sm_75', 'sm_80', 'sm_86', 'sm_90', 'sm_100', 'sm_120']```

# Verify GPU 
```
import torch
print("PyTorch:", torch.__version__)
print("CUDA available:", torch.cuda.is_available())
if torch.cuda.is_available():
    print("GPU:", torch.cuda.get_device_name(0))
    print("Compute capability:", torch.cuda.get_device_capability(0))
```
output
```
PyTorch: 2.15.0+cu132
CUDA available: True
GPU: NVIDIA GeForce RTX 5080
Compute capability: (12, 0)
```

# Math Test

```
x = torch.randn(100, 100, device="cuda")
y = x @ x
torch.cuda.synchronize()
print("Computation OK, device:", y.device)
```
ouptut
```
Computation OK, device: cuda:0
```

# Version Match Table

|  | PyTorch 2.15.0 | PyTorch 2.5.1 (Does Not Support SM_120) |
|-------|-------|-------|
| Driver595/CUDA 13.2/GPU Arch SM_120  | Good | RuntimeError: CUDA error: no kernel image is available for execution on the device
|
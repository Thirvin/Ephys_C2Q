# Ephys_C2Q

## packages：
pennylane 0.33.1

torch 2.1.0

os

time

copy
## 作業系統：
colab

python 3.10.12
## 硬體設備：
1. CPU: Intel(R) Xeon(R) CPU @ 2.20GHz
2. GPU: T4

(provided by google colab)
## 模型架構：
#### Input
- Conv2d(3, 64, kernel_size=(7, 7), stride=(2, 2), padding=(3, 3), bias=False)
- BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- ReLU(inplace=True)
- MaxPool2d(kernel_size=3, stride=2, padding=1, dilation=1, ceil_mode=False)

#### Layer 1
##### BasicBlock 1
- Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- ReLU(inplace=True)
- Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)

##### BasicBlock 2
- Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- ReLU(inplace=True)
- Conv2d(64, 64, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(64, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)

#### Layer 2
##### BasicBlock 1
- Conv2d(64, 128, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False)
- BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- ReLU(inplace=True)
- Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- Sequential
  - Conv2d(64, 128, kernel_size=(1, 1), stride=(2, 2), bias=False)
  - BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)

##### BasicBlock 2
- Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- ReLU(inplace=True)
- Conv2d(128, 128, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(128, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)

#### Layer 3
##### BasicBlock 1
- Conv2d(128, 256, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False)
- BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- ReLU(inplace=True)
- Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- Sequential
  - Conv2d(128, 256, kernel_size=(1, 1), stride=(2, 2), bias=False)
  - BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)

##### BasicBlock 2
- Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- ReLU(inplace=True)
- Conv2d(256, 256, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(256, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)

#### Layer 4
##### BasicBlock 1
- Conv2d(256, 512, kernel_size=(3, 3), stride=(2, 2), padding=(1, 1), bias=False)
- BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- ReLU(inplace=True)
- Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- Sequential
  - Conv2d(256, 512, kernel_size=(1, 1), stride=(2, 2), bias=False)
  - BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)

##### BasicBlock 2
- Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)
- ReLU(inplace=True)
- Conv2d(512, 512, kernel_size=(3, 3), stride=(1, 1), padding=(1, 1), bias=False)
- BatchNorm2d(512, eps=1e-05, momentum=0.1, affine=True, track_running_stats=True)

#### Layer 5
- AdaptiveAvgPool2d(output_size=(1, 1))

#### Layer 6
- DressedQuantumNet
  - Linear(in_features=512, out_features=4, bias=True)
  - Linear(in_features=4, out_features=2, bias=True)

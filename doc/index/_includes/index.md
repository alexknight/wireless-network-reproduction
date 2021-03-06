## Introduction

[Wireless Network Reproduction](https://github.com/FinalTheory/wireless-network-reproduction) (aka WNR) is a network emulator which allows developers to exactly reproduce any kind of terrible network condition on your own mobile device, or even Android/iOS emulators running on Mac OS.

<img src="/wireless-network-reproduction/images/interface.png" width="500px"></img>


## Features

Aspects that can be controlled by WNR include:

- Bandwidth
- Latency
- Packet loss
- Packet corruption
- Packet reordering
- Packet duplication
- Packet throttling

You could run WNR in two different mode:

1. Gateway Mode: First share your internet connection through [Internet-Sharing](https://support.apple.com/kb/PH18704), and then WNR would shape / interfere the network traffic between your MacBook and your mobile device, just like a router.
2. Emulator Mode: Just start an Android / iOS emulator, specify the process name in WNR, and then you will have emulated network condition in your virtual machine. In this mode you don't need a real mobile phone.


## Advantages

- **Extremely Customizable**: WNR is designed to **reproduce** any type of network condition, which means that it is not just simply shaping the network traffic like [`tc`](http://linux.die.net/man/8/tc) or [`ATC`](http://facebook.github.io/augmented-traffic-control/), but forcing the network to act as some specific pattern. With WNR, we could not only produce a bandwidth limited network, but also make the bandwidth vary by time, and even approach a user defined curve. The example configuration is [here](https://github.com/FinalTheory/wireless-network-reproduction/blob/master/macdivert/examples/bandwidth.json), and its actual effect is shown below.
- **Apply on Process**: When running WNR on your host, you can choose to shape network traffic **only for a specific process**, and dump the entire conversation into a `.pcap` file, which could be used for detailed analyze.


## Requirements

- A MacBook running OS X Yosemite / EI Capitan
- An Android/iOS mobile phone, or emulators like [GenyMotion](https://www.genymotion.com), [Droid4X](http://www.droid4x.com), etc.


## Download

For Chinese users, please download WNR through [Baidu Yun](http://pan.baidu.com/s/1eRwLDQy).

For other users, check [Github releases](https://github.com/FinalTheory/wireless-network-reproduction/releases) for latest build.


## Getting Started

1. Download WNR from URL links above.
2. Extract and save it into your hard drive.
3. Run this app, click "Network Emulator" button, and enter your root password.
4. If this is your first time to run this, you need to disable kernel extension checking according to the prompt.
5. Restart your Mac and run this app again, you may see the emulator interface shown above.
6. Click "Add Configuration" and select a default configuration or your customized ones.
7. If you need to inspect on packets transmitted from / to your device, then select a position to save `.pcap` files.
8. If you want to run emulation on real device, then start "Internet-Sharing" of macOS, and switch emulator mode to "WiFi" instead of "Local".
9. If you want to run emulation on Android virtual machine, you need to specify the PID or process name ("vboxheadless" for VirtualBox based Android emulators) of your Android emulator.
10. Finally, when everything is ready, click "Start" and check if the emulator is working as expected.


## Notice

- **DO NOT** run this application directly in dmg image!!! You should first extract it from image, save it into a local folder, and then try to run it.
- Path to the application should **NOT** contain any non-ASCII characters, otherwise it would encounter an error.


## Examples

### Network Emulation

The following animation shows the basic usages of WNR.

<img src="/wireless-network-reproduction/images/demo.gif"></img>


### Bandwidth Limitation

The following animation shows how to limit bandwidth of a specific process such as `wget`.

<img src="/wireless-network-reproduction/images/bandwidth.gif"></img>


### TCP Connection Analyze

We use a time-related function `bandwidth(t) = 256 + 1024 * sin(t/4) (KB/s)` to emulate some sort of dynamic bandwidth limitation, and then use TCP data visualization of WNR to show the actual bandwidth variation, which results in the figure shown below:

<img src="/wireless-network-reproduction/images/bandwidth.png"></img>


## Contributions

Please use [Github issues](https://github.com/FinalTheory/wireless-network-reproduction/issues) for requests.

**We guarantee that we will try our best to meet the need of new features / bug fixes in first 30 issues;** and we actively welcome pull requests.


## ChangeLog

Changes are tracked as Github [commits](https://github.com/FinalTheory/wireless-network-reproduction/commits/master) and [releases](https://github.com/FinalTheory/wireless-network-reproduction/releases).


## License

Wireless Network Reproduction is [BSD-licensed](https://github.com/FinalTheory/wireless-network-reproduction/blob/master/LICENSE).

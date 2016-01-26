![](http://www.emlid.com/wp-content/uploads/2014/10/APM.png)

#### Where to get the code

Navio2 will soon be supported in the main [APM repository](https://github.com/diydrones/ardupilot).

#### How to build

APM binary for Navio2 can be built using two ways:

1) Directly on your Raspberry Pi. Simpler, but slower. Build takes approximately 15 minutes.

2) Using a cross-compiler (on Linux PC or virtual machine). This is much faster, but requires one-time setup.

If you'd like to build on Raspberry Pi skip the next step.

#### Cross-compiler setup on Linux (optional)

Recommended compiler is the one that is provided by Raspberry Pi Foundation. Download and extract it somewhere, for example in /opt/:

```bash
sudo git clone --depth 1 https://github.com/raspberrypi/tools.git /opt/tools
```

If you're using 32-bit distro add the following to your PATH:

```bash
export PATH=/opt/tools/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian/bin:$PATH
```

For 64-bit distro add this to your PATH

```bash
export PATH=/opt/tools/arm-bcm2708/gcc-linaro-arm-linux-gnueabihf-raspbian-x64/bin:$PATH
```

If you would like to add the compiler to the PATH permanently edit /etc/environment.

#### Building APM

These steps are the same both for compiling APM directly on Raspberry Pi and cross-compiling.

Download the APM code:

```bash
git clone https://github.com/diydrones/ardupilot.git
```

Navigate to the autopilot’s directory: APMrover, ArduCopter or ArduPlane. For example ArduCopter:

```bash
cd ardupilot/ArduCopter
```
Build for quadcopter:

```bash
make navio2-quad
```
To build for other frame types replace quad with one of the following options:

```bash
quad tri hexa y6 octa octa-quad heli single obc nologging
```

In the end of compilation binary file with the name ArduCopter.elf will be placed in the same directory.

If you're using cross-compiler transfer the binary to your Raspberry Pi:

```bash
rsync -avz ArduCopter.elf pi@192.168.1.3:/home/pi/
```

Where 192.168.1.3 is an IP address of your Raspberry Pi with Navio.

Instructions how to run APM on Raspberry Pi and to connect GCS to it are available in  [Installation and running section](installation-and-running.md).

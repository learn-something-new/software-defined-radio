# Trunked Digital Radio (P25)

## Requirements

**Hardware**
- 2x RTL-SDR Receiver (1 is fine however 2 will give the best performance)

**Software**
- [SDRTrunk](https://github.com/DSheirer/sdrtrunk)
- [JMBE](https://github.com/DSheirer/jmbe) (used for decoding the audio)

## Steps

**Installation** 
First download the latest version of SDRTrunk from the [releases](https://github.com/DSheirer/sdrtrunk/releases) page on there GitHub, at the time this was 0.4.0 Beta 5.
![releases](../screenshots/sdrtrunk-1.png)

Next we need the JMBE library so we can decode the audio and hear what people are saying, this is a bit more complicated because a binary isn't provided, however the installation uses Gradle and they have good documentation.
![releases](../screenshots/sdrtrunk-2.png)

You can install it using the [instructions](https://github.com/DSheirer/jmbe/blob/master/README.md) on the JMBE Wiki and when you are done you should have a file (in your build directory) `codec\build\libs\jmbe-1.0.0.jar`, you can store this anywheres because you set it's location in SDRTrunk however I personally like to store it in the libs folder of the SDRTrunk source (`sdr-trunk-linux-x86_64-v0.4.0-beta.5/lib`).


## References
- [SDRTrunk](https://github.com/DSheirer/sdrtrunk)
- [JMBE](https://github.com/DSheirer/jmbe)
- [SDRTrunk Setup and Use Tutorial - rtl-sdr.com](https://www.rtl-sdr.com/sdrtrunk-setup-and-use-tutorial/)

## License 
This tool is protected by the GNU General Public License v2.

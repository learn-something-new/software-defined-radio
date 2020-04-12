# Spectrum Painting

## Warning

Only do this on bands that are unlicensed or you have a license for, additionally be careful not to cause interfearance by transmitting too high. I was under 1w when I did this and monitored that the frequency range in I chose was not in use within range of me.

## Requirements

- An SDR that can transmit, I chose the HackRF however the spectrum_painter tool supports the BladeRF as well as a pure float output that can be used by other devices.
- spectrum_painter
- *optional* GQRX or similar and a second SDR, this can be RX only as it would be just for monitoring

## Guide

### Step 1

We need to convert our image to binary format that the HackRF can transmit. Note I used a 2500x2500px PNG of our logo with a solid black background for the source image.

```bash
pwntoo@ISeeRadioWaves ~/spectrum_painter $ python2 -W ignore /opt/build/spectrum_painter/spectrum_painter/img2iqstream.py \
	-s 3200000 \
	-l 0.004 \
	-o dc902.iqhackrf \
	--format hackrf \
	DC902-v2-2.png
```

Lets talk a little bit about the settings:

- `-s 1e6`: Sample rate of 1Msps or 1 million samples per second
- `-l 0.004`: The duration time (assumibly in seconds) that each line is "written" to screen
- `-o DC902-v2-2-small.iqhackrf`: Output file
- `--format hackrf`: Format (device specific)
- `DC902-v2-2-small.png`: Source image


### Step 2

```bash
pwntoo@ISeeRadioWaves ~/spectrum_painter $ hackrf_transfer -t dc902.iqhackrf -f 433000000 -b 10000000 -s 3200000 -x 20 -a 1
call hackrf_set_sample_rate(3200000 Hz/3.200 MHz)
call hackrf_baseband_filter_bandwidth_set(10000000 Hz/10.000 MHz)
call hackrf_set_freq(433000000 Hz/433.000 MHz)
call hackrf_set_amp_enable(1)
Stop with Ctrl-C
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.6 MiB / 1.000 sec =  6.6 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.6 MiB / 1.000 sec =  6.6 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.6 MiB / 1.000 sec =  6.6 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.6 MiB / 1.000 sec =  6.6 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.6 MiB / 1.000 sec =  6.6 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.6 MiB / 1.000 sec =  6.6 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.6 MiB / 1.000 sec =  6.6 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
6.6 MiB / 1.000 sec =  6.6 MiB/second
6.3 MiB / 1.000 sec =  6.3 MiB/second
0.3 MiB / 1.000 sec =  0.3 MiB/second

Exiting... hackrf_is_streaming() result: streaming terminated (-1004)
Total time: 21.00194 s
hackrf_stop_tx() done
hackrf_close() done
hackrf_exit() done
fclose(fd) done
exit

```

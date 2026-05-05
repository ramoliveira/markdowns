# Wireless Networking

## Wireless Standards

Is a standard maintained by the Institute of Electrical and Electronics Engineers (IEEE)
*802.11*: Standard related to wireless networks

### Major Wi-Fi Standards

|IEEE Standard|Generation Name|Frequencies|Maximum theoretical link rate|
|:-:|:-:|:-:|:-:|
|802.11a|-|5 GHz|6-54 Mbit/s|
|802.11b|-|2.4 GHz|1-11 Mbit/s|
|802.11g|-|2.4 GHz|6-54 Mbit/s|
|802.11n|Wi-Fi 4|2.4 GHz / 5 GHz|72-600 Mbit/s|
|802.11ac|Wi-Fi 5|5 GHz|433-6.933 Mbit/s|
|802.11ax|Wi-Fi 6 and 6E|2.4 GHz / 5 GHz / 6 GHz|574-9.608 Mbit/s|
|802.11be|Wi-Fi 7|2.4 GHz / 5 GHz / 6 GHz|1.376-46.120 Mbit/s|

## 4G and LTE

Long Term Evolution (LTE) is a converged standard of GSM and CDMA providers.
Is a *4G* technology.
It's based on GSM and EDGE (Enhanced Data Rates for GSM Evolution).

> [!INFO]
> Standard supports download rates of 150 Mbit/s.
>
> LTE Advanced (LTE-A) standard supports download rates of 300 Mbit/s.

## 5G

Fifth generation cellular networking. Launched worldwide in 2020. Has significant performance improvements.

* Works at higher frequencies.
* Eventually gets to 10 Gbit/s.
* Slower speeds from 100-900 Mbit/s.

### IoT Impact
* Bandwidth becomes less of a constraint
* Larger data transfers
* Faster monitoring and notification
* Additional cloud processing

## Satellite Networking

Communication to a satellite. Non-terrestrial communication.

* Has higher cost relative to terrestrial networking.
* 100 Mbit/s down, 5 Mbit/s up are common.
* Most used on remote sites, difficuclt-to-network sites.
* Has relatively high latency.
    * 250 ms up, 250 ms down.
    * Starlink advertises 40 ms and is working on 20 ms.
* High frequencies of 2 GHz, avoids loosing connection whenever rains.

> [!ABSTRACT]
> Satellite Networking has high latency due to packets travelling to space and comming back to earth.
> 
> Usually, satellites are $\approx 36.000 \text{Km}$ height from Earth. So travelling back and forth sums $\approx 72.000 \text{Km}$ (without routing).
> Considering: $v \aprox 3 \times 10^8 m/s$ (light speed), $ km would take $\approx 240 \text{ms}$



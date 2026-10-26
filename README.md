# meta-linht-sdr

A Yocto Project layer providing GNU Radio and Software Defined Radio (SDR) support for the LinHT Handheld Transceiver project.

## Overview

This layer is a **fork of [meta-sdr](https://github.com/balister/meta-sdr)** by Philip Balister. We extend our sincere gratitude to Philip Balister and the meta-sdr community for their excellent work in providing GNU Radio and SDR support for Yocto Project.

The layer has been adapted and customized to support the specific requirements of the LinHT project while maintaining compatibility with the broader SDR ecosystem.

The LinHT image itself is defined in [meta-linht-software](https://github.com/M17-Project/meta-linht-software). The full build procedure is described on the M17 wiki: [LinHT Image Build](https://wiki.m17foundation.org/index.php?title=LinHT_Image_Build).

## Contents

### GNU Radio
- **gnuradio**: GNU Radio 3.10
- **volk**: Vector Optimized Library of Kernels
- **gnuradio-oot.bbclass**: Helper class for building GNU Radio out-of-tree modules

### GNU Radio out-of-tree modules
- **gr-foo**: General purpose GNU Radio blocks (used by the LinHT image)
- **gr-osmosdr**: Common source/sink blocks for SDR hardware
- **gr-satellites**: Telemetry decoders for amateur satellites
- **gr-lora-sdr**: LoRa transceiver
- **gr-adsb**, **gr-air-modes**: ADS-B / Mode S decoding
- **gr-ais**: AIS decoding
- **gr-pager**: Motorola FLEX pager decoding
- **gr-ieee80211**: IEEE 802.11 a/g/p transceiver
- **gr-mesa**, **gr-lfast**: Signal processing and flowgraph performance blocks
- **gr-ettus**: Experimental UHD and USRP features

### SDR hardware support and tools
- **rtl-sdr**, **libhackrf**, **libairspy** / **airspy-tools**, **uhd** / **uhd-firmware**
- **rtl433**: Generic data receiver for ISM band devices

### Images and package groups
- Example images from meta-sdr: `gnuradio-image`, `gnuradio-dev-image`, `gnuradio-demo-image`, `gnuradio-video-demo-image`, `gnuradio-ptest-image`, `gqrx-demo-image`, `uhd-dev-image`, `base-dev-image`
- Package groups: `packagegroup-sdr`, `packagegroup-sdr-base`, `packagegroup-uhd`

## Dependencies

This layer is used with the **scarthgap** release (see `LAYERSERIES_COMPAT_sdr-layer` in [conf/layer.conf](conf/layer.conf) for all compatible releases). It depends on the following layers:

### Core dependencies
```
URI: git://git.openembedded.org/openembedded-core (or poky)
branch: scarthgap
```

### Meta-OpenEmbedded layers
```
URI: git://github.com/openembedded/meta-openembedded.git
branch: scarthgap
```

**Required meta-openembedded sublayers:**
- **meta-oe**: OpenEmbedded layer
- **meta-filesystems**: Filesystem support
- **meta-networking**: Network protocols and tools
- **meta-python**: Python packages and runtime

## Integration instructions

### Adding to build configuration

Add the required layers to your `bblayers.conf`:

```bash
# Core dependencies
BBLAYERS += "/path/to/openembedded-core/meta"

# Meta-OpenEmbedded layers
BBLAYERS += "/path/to/meta-openembedded/meta-oe"
BBLAYERS += "/path/to/meta-openembedded/meta-filesystems"
BBLAYERS += "/path/to/meta-openembedded/meta-networking"
BBLAYERS += "/path/to/meta-openembedded/meta-python"

# LinHT SDR layer
BBLAYERS += "/path/to/meta-linht-sdr"
```

## License

This layer maintains the same licensing as the original meta-sdr layer. Individual recipes may have their own specific licenses.

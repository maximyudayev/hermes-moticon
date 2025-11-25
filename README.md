# HERMES - Moticon OpenGO Insoles

Support package to interface the [Moticon OpenGo](https://moticon.com/opengo/sensor-insoles) commercial pressure insole sensors in [HERMES](https://github.com/maximyudayev/hermes). The interface connects to the UDP output stream of the [OpenGo desktop software](https://moticon.com/opengo/software) endpoint, which receives streaming data from the [OpenGo mobile app](https://moticon.com/opengo/app) endpoint connected over BLE to the insoles.

> [!NOTE]
> This package relies on the complementary software provided along with the insoles kit. Moticon also offers the [Insole SDK](https://moticon.com/solutions-integrations) via a paid license, which enables direct communication to the insoles over BLE instead of through the 2 OEM software endpoints. The option is not covered by this package for costs reasons.

> [!WARNING]
> (October, 2025): [unresolved] Previously working version interfacing `03.05.00_11804` of OpenGo desktop app and `03.10.00 (80)`/`03.13.01 (99)` mobile app is experiencing unexpected prolong dropout in streamed data.

## Installation
Node available under the same HERMES namespace of `hermes.moticon` as `MoticonProducer`. Follow [these instructions](https://moticon.com/opengo/docs#tutorials) to prepare the insoles and configure live streaming, setup the stream out of the mobile app, configure UDP output streaming from the desktop app to the `localhost`.

### From PyPI
```bash
pip install pysio-hermes-moticon
```

### From source
```bash
git clone https://github.com/maximyudayev/hermes-moticon.git
pip install -e hermes-moticon
```

## Usage
Using the device follows the standard [configuration file specification](https://maximyudayev.github.io/hermes/) process of HERMES nodes.

### Desktop app
Turn on OpenGo software on the desktop, take note of IP address. Select all desired modalities to stream out of the app over UDP to the localhost.

### Mobile app
Zero the insoles, calibrate the weight of the person, connect to the desktop endpoint over IP.

> [!TIP]
> Use USB tethering between smartphone and desktop for lower latency and a robust connection.

Start capturing the data in the mobile app. The desktop app should begin to visualize streaming data and retransmit it on the localhost at the specified port number. Default port `8888` will automatically receive data in HERMES.

## Citation
When using any parts of this repository outside of its intended use, please cite the parent project [HERMES](https://github.com/maximyudayev/hermes).

# How AWS IoT works

AWS IoT help us to connect things / devices to the AWS cloud and also with another devices, if we need it. The communication protocol\(s\) that AWS IoT supports are:

* **MQTT**

[MQTT](http://mqtt.org/faq) stands for MQ Telemetry Transport. It is a publish/subscribe, extremely simple and lightweight messaging protocol, designed for constrained devices and low-bandwidth, high-latency or unreliable networks. The design principles are to minimize network bandwidth and device resource requirements whilst also attempting to ensure reliability and some degree of assurance of delivery. These principles also turn out to make the protocol ideal of the emerging “machine-to-machine” \(M2M\) or “Internet of Things” world of connected devices, and for mobile applications where bandwidth and battery power are at a premium.

* **TLS**

The [TLS protocol](https://en.wikipedia.org/wiki/Transport_Layer_Security) allows client-server applications to communicate across a network in a way designed to prevent [eavesdropping](https://en.wikipedia.org/wiki/Eavesdropping) and [tampering](https://en.wikipedia.org/wiki/Tampering). Since protocols can operate either with or without TLS \(or SSL\), it is necessary for the client to indicate to the server the setup of a TLS connection. There are two main ways of achieving this. One option is to use a different port number for TLS connections \(for example, port 443 for HTTPS\). The other is for the client to use a protocol-specific mechanism \(for example, STARTTLS for mail and news protocols\) to request that the server switch the connection to TLS. \]

* **Ports used by MQTT**

The \[port\(s\)\]\([https://en.wikipedia.org/wiki/Port\_\(computer\_networking](https://en.wikipedia.org/wiki/Port_%28computer_networking)\) that are being used by MQTT are:

* [TCP/IP](https://en.wikipedia.org/wiki/Internet_protocol_suite) port 1883 is reserved with IANA for use with MQTT. 
* [TCP/IP](https://en.wikipedia.org/wiki/Internet_protocol_suite) port 8883 is also registered, for using MQTT over SSL.

### More information can be read it [**here**](http://docs.aws.amazon.com/iot/latest/developerguide/aws-iot-how-it-works.html)


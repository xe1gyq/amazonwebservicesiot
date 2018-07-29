# IoT devices

**The Internet of Things \(IoT\)** is the network of physical objects or "things" embedded with electronics, software, sensors, and network connectivity, which enables these objects to collect and exchange data. The Internet of Things allows objects to be sensed and controlled remotely across existing network infrastructure, creating opportunities for more direct integration between the physical world and computer-based systems, and resulting in improved efficiency, accuracy and economic benefit. Each thing is uniquely identifiable through its embedded computing system but is able to interoperate within the existing Internet infrastructure. Experts estimate that the IoT will consist of almost 50 billion objects by 2020.

![](http://eecatalog.com/caciufo/wp-content/uploads/2014/06/IoT-devices.png)

**Internet of Things \(IoT\)** are connected devices, applications, or physical objects that are supported by your cloud application. On the AWS IoT technology, Amazon includes the Registry and Device Shadows, with this options you can register any Thing you wish to represent in the cloud with a name, some attributes, and a persistent virtual 'shadow'.

**The Registry:** You can use thing attributes to describe, identity the capabilities of your device. For example, you can describe whether a sensor reports temperature, and if the data are Fahrenheit or Celsius. You can also use attributes to search/filter within a list of things. The Registry lets you **store attributes at no additional charge**, and metadata in the Registry does not expire as long as you access or update your Registry entry at least once **every 7 years**.

Click [here](https://docs.aws.amazon.com/console/iot/thing-registry) to learn more about the Registry.

**Device Shadows:** Are a persistent virtual version of each thing that includes the IoT devices last reported state and desired future state, even when the underlying thing is not connected. You can retrieve the last reported state of a thing or set the desired future state through the API or using the rules engine. Device Shadows let you store the state of your things for up to a year at no additional charge. **Shadows persist forever if you update them at least once per year, otherwise they expire**.

Click [here](https://docs.aws.amazon.com/console/iot/thing-shadows) to learn more about Device Shadows.


# AWS IoT Components

**Message broker:** Provides a secure mechanism for Iot devices and IoT applications to publish and receive messages from each other. You can use the [MQTT](http://mqtt.org/faq) protocol to publish and subscribe. You can use the [HTTP REST](https://en.wikipedia.org/wiki/Representational_state_transfer) interface to publish.

**Rules engine:** Provides message processing and integration with other AWS services. You can use a SQL-based language to select data from message payloads, process the data, and send the data to other services, such as Amazon S3, Amazon DynamoDB, and AWS Lambda. You can also use the message broker to republish messages to other subscribers.

**Thing Registry:** Sometimes referred to as the Device Registry. Organizes the resources associated with each thing. You register your things and associate up to three custom attributes with each thing. You can also associate certificates and MQTT client IDs with each thing to improve your ability to manage and troubleshoot your things.

**Thing Shadows service:** Provides persistent representations of your things in the AWS cloud. You can publish updated state information to a thing shadow, and your thing can synchronize its state when it connects. Your things can also publish their current state to a thing shadow for use by applications or devices.

**Thing shadow:** Sometimes referred to as a device shadow. A JSON document used to store and retrieve current state information for a thing \(device, app, and so on\).

**Device gateway:** Enables devices to securely and efficiently communicate with AWS IoT.

**Security and identity service:**  Provides shared responsibility for security in the AWS cloud. Your things must keep their credentials safe in order to send data securely to the message broker. The message broker and rules engine use AWS security features to send data securely to devices or other AWS services.


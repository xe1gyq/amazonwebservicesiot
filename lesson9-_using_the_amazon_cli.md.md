# lesson9-\_using\_the\_amazon\_cli.md

AWS Command Line Interface \(AWS CLI\)—Run commands for AWS IoT on Windows, Mac, and Linux. To get started, see the [AWS Command Line Interface User Guide](http://docs.aws.amazon.com/cli/latest/userguide/). For more information about the commands for AWS IoT, see [IoT](http://docs.aws.amazon.com/cli/latest/reference/iot/index.html) in the AWS Command Line Interface Reference.

In our previous sessions \(Lesson 3 to 9\) we use the graphical interface to create and configure the IoT devices to report to the AWS infrastructure. In this lesson we will install the AWS CLI \(Client Line Interface to configure our IoT device on the AWS infrastructure\)

First we need to install the AWS CLI folow this tutorial to install the software:

* [http://docs.aws.amazon.com/cli/latest/userguide/installing.html](http://docs.aws.amazon.com/cli/latest/userguide/installing.html)

After you complete the installation, just test it:

```text
$ aws help
```

You must see something like this:

![](.gitbook/assets/51.jpg)

Execute the command aws configure to set up our credentials

![](.gitbook/assets/52.jpg)

The credentials was created on the Lesson 2. The default amazon region must be selected from this table:

![](.gitbook/assets/53.jpg)

**Note:** In the example, I'm using US West \(Oregon\) us-west-2

The next step is grant to our CLI user the AWS IoT access.

Use the create-role command to create an IAM role:

```text
$ aws iam create-role --role-name IOTrole --assume-role-policy-document file:///root/role.json
```

Specify the following trust policy document, which grants AWS IoT permission to assume the role: { "Version":"2012-10-17", "Statement":\[{ "Effect": "Allow", "Principal": { "Service": "iot.amazonaws.com" }, "Action": "sts:AssumeRole" }\] }

You will see this:

![](.gitbook/assets/54.jpg)

Note: The Amazon Resource Name \(ARN\) of the role in the command output. In this example the ARN value its **"arn:aws:iam::362639364520:role/IOTrole"**

On the amazon console you can check the role on the IAM option:

![](.gitbook/assets/55%20%281%29.jpg)

Under Roles, you will see the IOTrole that we create with the last command:

![](.gitbook/assets/56.jpg)

Use the create-policy command to grant AWS IoT access to your AWS resources upon assuming the role:

```text
$ aws iam create-policy --policy-name IOTpolicy --policy-document file:///root/policy.json
```

The following is an example policy document that grants AWS IoT administrator access to DynamoDB:

```text
{
    "Version": "2012-10-17",
    "Statement": [{
        "Effect": "Allow",
        "Action": "dynamodb:*",
        "Resource": "*"
    }]
}
```

You must see this:

![](.gitbook/assets/57.jpg)

Note: In this example the value of the ARN can be checked on the line:

```text
"Arn": "arn:aws:iam::362639364520:policy/IOTpolicy",
```

On the amazon console you can check the role on the IAM option

![](.gitbook/assets/55.jpg)

Under Policies use the filter and type **IOTp**, you will see the policy that the code creates.

![](.gitbook/assets/59.jpg)

Use the attach-role-policy command to attach your policy to your role:

```text
$ aws iam attach-role-policy --role-name IOTrole --policy-arn  "arn:aws:iam::362639364520:policy/IOTpolicy"
```

Return to the console and check that the IOTpolicy have 1 attached entities

![](.gitbook/assets/60.jpg)

Now we can proceed and create via the CLI our first IoT on AWS, we just need to execute:

```text
aws iot create-thing --thing-name MYNEWIOTdevice
```

You will see this result:

![](.gitbook/assets/61.jpg)

**Note:** Check the ARN value of the our new IoT device this willbe used later:

**"thingArn": "arn:aws:iot:us-west-2:362639364520:thing/MYNEWIOTdevice",**

Create a policy for the IoT device.

```text
aws iot create-policy --policy-name MYNEWIOTpolicy --policy-document file:///root/IOTpolicy.json
```

The IOTpolicy.json file must contain this:

```text
{
    "Version": "2012-10-17", 
    "Statement": [{
        "Effect": "Allow",
        "Action":["iot:*"],
        "Resource": ["*"]
    }]
}
```

You will see this result:

![](.gitbook/assets/62.jpg)

**Note:** check the **Policy ARN** value:

```text
policyArn": "arn:aws:iot:us-west-2:362639364520:policy/MYNEWIOTpolicy"
```

We will proceed and create the certificates to establish a secure communication between the IoT device and the AWS server.This command generates a certificate, a public key, and a private key.

```text
aws iot create-keys-and-certificate --set-as-active --certificate-pem-outfile cert.pem --public-key-outfile publicKey.pem --private-key-outfile privateKey.pem
```

You will see this result:

![](.gitbook/assets/63.jpg)

**Note:** The certificate ARN will be used on our next step please copy the value.

```text
"certificateArn": "arn:aws:iot:us-west-2:362639364520:cert/a2a6bfe011f07e4289e17f494bade5ee9d9ae0deb6cc5a9692247e8274ff022a",
```

We will proceed and attach the certificate to our IoT device:

```text
aws iot attach-thing-principal --thing-name MYNEWIOTdevice --principal arn:aws:iot:us-west-2:362639364520:cert/a2a6bfe011f07e4289e17f494bade5ee9d9ae0deb6cc5a9692247e8274ff022a
```

We need to see this result:

![](.gitbook/assets/64.jpg)

and also in the graphical interface of the IoT:

![](.gitbook/assets/65.jpg)


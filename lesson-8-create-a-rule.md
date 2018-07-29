# Lesson 8: Create a Rule

Return to the AWS IoT dashboard and click on the **Create a resource** button.

![](.gitbook/assets/40.jpg)

Select the option **Create a rule**

![](.gitbook/assets/39.jpg)

Now you just need to complete the following information:

* Name, its the Name of the rule, in our case we called RuleInsertDynamoDB
* Description, is optional you can type a description of the rule.
* Rule query statement cant be modified.
* Attribute, its the attribute that we can catch from the device in our case we will catch all the information we will use an asterisk \(\*\) to indicate that we need all the information. 
* Topic Filter: We must use the topic filter that our Edison sensor is using in my case its: **$aws/things/EdisonLab/shadow/update**, this information can be extracted from the EdisonLab resource on the Details page under the MQTT topic. 

![](.gitbook/assets/42.jpg)

* Condition, for this test we will leave it, blank we will catch and store all the messages.

![](.gitbook/assets/41.jpg)

Now in the Choose and action filed select **Insert message into a database table \(Dynamo DB\)** On the Table name field sleect the name of the table that we create on the Lesson 7, EdisonResultsTable

Hash key Value type ${topic\(3\)}

Range key value type ${timestamp\(\)}

Payload field leave it blank we need all the payload to understand the information that we are sending from the Edison.

In the Role name click on the create a new role link, this will help you to create a role in IAM.

Just check the name that Amazon will assing to teh role and clik in the buton Allow, in this case the IAM Role is called aws\_iot\_dynamoDB

## Note : If you can't see information on the database, please review the role aws\_iot\_dynamoDB and the permission that this role have on the IAM module.

![](.gitbook/assets/43.jpg)

After you finish this task just select the new role that you created.

Now click on the Add Action button \(blue square\) and after click on the Create button \(red square\)

![](.gitbook/assets/44.jpg)

Return to the Dynamo DB module and check your table you must see the information that you are sending from the Edison sensor:

![](.gitbook/assets/45.jpg)

Also, you can check one of the registries click on the EdsionLab hyperlink, expand all the information and you will see the following information:

![](.gitbook/assets/46.jpg)

We are receiving The time stamp is the value when the message arrives to AWS The payload is all the information that we send from the Edison sensor to AWS this example includes the clientToken information EdisonLab-22063, gas information with the value 25 and the hardwareID that is Edison\_PYMELab.


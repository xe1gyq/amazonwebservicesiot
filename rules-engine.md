# Rules Engine

The real-time Rules Engine transforms messages based on expressions that you define, and routes them to AWS endpoints \(Amazon DynamoDB, Amazon Simple Storage Service \(S3\), AWS Lambda, Amazon Simple Notification Service \(SNS\), Amazon Simple Queue Service \(SQS\), Amazon Kinesis, and Amazon Kinesis Firehose\) all expressed using a SQL-like syntax. Routing is driven by the contents of individual messages and by context. For example, routine readings from a temperature sensor could be tracked in a DynamoDB table; an aberrant reading that exceeds a value stored in the thing shadow can trigger a Lambda function .


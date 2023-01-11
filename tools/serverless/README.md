# Serverless

## Testing SQS Trigger locally

```sh
sam local generate-event sqs receive-message --body "{\\\"text\\\": \\\"world\\\"}" | serverless invoke local --function readMessage --env SQS_QUEUE_URL=http://aws.amaz.com

```

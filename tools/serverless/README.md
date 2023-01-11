# Serverless

## Testing SQS Trigger locally

```sh
sam local generate-event sqs receive-message --body "{\\\"text\\\": \\\"world\\\"}" | serverless invoke local --function readMessage --env SQS_QUEUE_URL=http://aws.amaz.com

```

## Viewing Lambda logs during development
```sh
serverless logs -f readMessage -t
##where readMessage is the function name
```
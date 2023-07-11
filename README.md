# Scala.js AWS Lambda Slack Bot Example

**THIS REPO IS WORK IN PROGRESS**

## Acknowledgements

- [Yris-ops/slack-bot-aws-lambda](https://github.com/Yris-ops/slack-bot-aws-lambda)
- [bgahagan/scalajs-lambda.g8](https://github.com/bgahagan/scalajs-lambda.g8)
- [How to Create a Slack Bot using AWS Lambda in < 1 Hour](https://medium.com/glasswall-engineering/how-to-create-a-slack-bot-using-aws-lambda-in-1-hour-1dbc1b6f021c)

## Run locally

### As lambda container

```
sbt fastOptJS::webpack
./scripts/run-local-lambda-container.sh
curl -XPOST "http://localhost:9000/2015-03-31/functions/function/invocations" -d '{"payload":"hello world!"}'
```

### Through scalajs local server
This will expose your lambda through an http endpoint served by http4s on nodejs.

```
sbt local-run/run
## nodejs debugger available on port 9229. It's compatible with Intellij "Attach to Node.js/Chrome" debug option
```

### Alternatives

This bot can be deployed to localstack but with significant limitations:

* `AWS::ApiGatewayV2::Api` recource is not supported in localstack community edition, so this part has to be done
  separately (outside fo cloud formation)
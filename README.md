This Terraform module installs the Genesys Cloud AWS EventBridge integration into a Genesys Cloud org.  The AWS EventBridge integration allows events generated by 
Genesys Cloud to be published to AWS EventBridge. The documentation for the Genesys Cloud AWS EventBridge can be found [here](https://developer.genesys.cloud/api/rest/v2/notifications/event_bridge).

## Usage

```hcl
module "AwsEventBridgeIntegration" {
   source             = "git::https://github.com/GenesysCloudDevOps/aws-event-bridge-module.git?ref=v0.0.3"
   aws_account_id   = "335611188682"
   aws_account_region   = "us-west-2"
   event_source_suffix     = "-sample-eb"
   topic_filters = ["v2.audits.entitytype.{id}.entityid.{id}","v2.analytics.flow.{id}.aggregates"]
}
```

## Requirements

| Name | Version |
|------|---------|
| <a name="provider_terraform"></a>[terraform](https://www.terraform.io/) | >= 1.0 |

## Providers

| Name | Version |
|------|---------|
| <a name="provider_genesyscloud"></a> [genesyscloud](https://registry.terraform.io/providers/MyPureCloud/genesyscloud/latest) | >= 0.13.3 |

source             = "git::https://github.com/GenesysCloudDevOps/aws-event-bridge-module.git?ref=v0.0.1"
   aws_account_id   = "335611188682"
   aws_account_region   = "us-west-2"
   event_source_suffix     = "-sample-eb"
   topic_filters = ["v2.audits.entitytype.{id}.entityid.{id}","v2.analytics.flow.{id}.aggregates"]

## Inputs

| Name | Description | Type | Required |
|------|-------------|------|:--------:|
| <a name="aws_account_id"></a> [aws_account_id](#aws\_account\_id)  |  The 12 digit AWS account ID where the event source will be made available for an event bus.| `string` | yes |
| <a name="aws_account_region"></a> [aws_account_region](#aws\_account\_region) |  The AWS region where the event source will be made available for an event bus. (e.g. us-east-1) | `string` | yes |
| <a name="event_source_suffix"></a> [event_source_suffix](#event\_\source_\suffix) | A unique name appended to the Event Source in the AWS account. Maximum of 64 characters consisting of lower/upper case letters, numbers, ., -, _. | `string` | yes |
| <a name="topic_filters"></a>   [topic_filters](#topic\_filters) | List of notification topics to send to EventBridge. A full list of events can be found [here](https://developer.genesys.cloud/api/rest/v2/notifications/available_topics) | `list(string)` | yes |
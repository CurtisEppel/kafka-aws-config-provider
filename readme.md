# Kafka AWS Config Provider

Kafak ConfigProvider implementation using AWS System Manger Parameter Store.

## Kafka Connenct Getting started

This package can be used as an [external secrets](https://docs.confluent.io/current/connect/security.html#externalizing-secrets) provider for Kafka Connect.

Here is an example of how to use `SsmConfigProvider` in the worker configuration:

```
# Additional properties for the worker configuration
config.providers=ssm   # multiple comma-separated provider types can be specified here
config.providers.ssm.class=com.cultureamp.kafka.config.provider.SsmConfingProvider
# Other ConfigProvider implementations might require parameters passed in to configure() as follows:
#config.providers.other-provider.param.foo=value1
#config.providers.other-provider.param.bar=value2
```

Then you can reference the configuration variables in the connector configuration as follows:

```
# Additional properties for the connector configuration
# Variable references are of the form ${provider:[path:]key} where the path is optional,
# depending on the ConfigProvider implementation.
my.secret=${ssm:/super/secret/password}
```

# Get Account Id and Region in AWS CDK

The (recommended way by the CDK team)[https://github.com/aws/aws-cdk/issues/1754#issuecomment-513542145]

```
    console.log('accountId: ', cdk.Stack.of(this).account);
    console.log('region: ', cdk.Stack.of(this).region);
    console.log('availability zones: ', cdk.Stack.of(this).availabilityZones);
```

We can also get region and account from process environmental variable but these environmental variables depends on, whether we pass in a --profile flag when we issue the cdk deploy command.

```
{
    region: process.env.CDK_DEFAULT_REGION,
    account: process.env.CDK_DEFAULT_ACCOUNT,
}
```

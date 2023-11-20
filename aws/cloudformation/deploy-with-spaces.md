# Deploy Cloudformation with spaces in arguments

Imagine you want deploy a cloudformation template with AWS CLI command. It is straigth forward process with `aws cloudformation deploy` command.
The deploy command has several argument that accept argument value in form of "string" "string" ... and each string should looks like key=value.
If you have spaces in the arguments you send to the command (lets say on --tags), you most probably will get an error message like follows:
`['Test'] value passed to --tags must be of format Key=Value`

You need to parse the key=value as an array of string. Furthermore, you need to stop bash from expanding on anything other than a line return. with `export IFS=$'\n'`

Example:
Let's say to have a config.json file as follows:

```
{
  "Parameters": {
    "QueueName": "prod-queue"
  },
  "Tags": {
    "Owner": "Build",
    "Project": "test-cloudformation",
    "Service": "Andys Test Service",
    "Component": "Andys Test Component",
    "Domain": "Build",
    "Version": "24",
    "SemanticVersion": "1.0.0",
    "Name": "test-cloudformation"
  }
}
```

Expanding bash only on new line
`export IFS=$'\n'`

parse parameter:

```
tags_array=($(cat $CONFIG_FILE | jq -r '.Tags | to_entries | map("\(.key|tostring)=\(.value|tostring)") | .[]'))
parameter_array=($(cat $CONFIG_FILE | jq -r '.Parameters | to_entries | map("\(.key|tostring)=\(.value|tostring)") | .[]'))
```

then deploy cloudformation
`aws cloudformation deploy --capabilities "CAPABILITY_NAMED_IAM" --template-file template.yaml --stack-name test-cloudformation --parameter-overrides "${parameter_array[@]}" --tags "${tags_array[@]}" --region eu-west-1`

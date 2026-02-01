IAM policies control what users can and cannot do in AWS. 

One common way to manage permissions is by using groups.
When you attach a policy to a group, every user inside that group automatically gets the same permissions.

For example, if Alice, Bob, and Charles are all in the Developers group, and you attach a policy to that group, all three will inherit that policy.

Users can also belong to multiple groups. 

A user does not have to belong to a group. For example, Fred can exist as a user without being part of any group. In this case, you can attach an inline policy directly to Fred.

Policy Structure example:

```json
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:ListBucket"
      ],
      "Resource": "arn:aws:s3:::my-example-bucket"
    },
    {
      "Effect": "Allow",
      "Action": [
        "s3:GetObject"
      ],
      "Resource": "arn:aws:s3:::my-example-bucket/*"
    }
  ]
}
```

Consists of 

- Policy version
- Id (identifier to the policy)
- Statement one or more individuals statements

Statements consist of
- Sid: an identifier to the statement
- Effect: wether if the policy allows or denies (allow, deny)
- Principal: account/user/role which this policy is applied to
- Action: list of actions the policy allows or denies
- Resource: list of resources which this policy will be applied to
KMS - key mgmt service

7.1
- to create and control encryption keys
- integrated with many aws services
- when to use? Dealing with sensitive info. Customer, financial data, db pass, secrets, creds.
- s3, rds, dynamo, lambda, ebs, efs, cloudtrail, devtools
- customer master key (cmk). cmk is used to  encrypt/decrypt data up to 4kb Data Key. DK is used to encrypt/decrypt data. Envelope encryption

7.3 cmk
- alias, creation date, description, key material, key state
- key material
- stays inside kms
1. set up cmk. Alias, desc, key material
2. key admin permissions
3. key usage permission
- aws-managed key. Used on your behalf with the aws ervices integrated with kms
- cmk. Created and owned by yourself
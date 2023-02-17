# Deploy

## Criar bucket para artefatos do deploy:
```
export REGION=sa-east-1
aws s3api create-bucket --bucket poc-eks-batch \
    --create-bucket-configuration LocationConstraint=$REGION
```
## Deploy da Stack
```
sam deploy --stack-name poc-eks-batch \
    --s3-bucket poc-eks-batch \
    --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM CAPABILITY_AUTO_EXPAND
```
## Undeploy:
```
sam delete --stack-name poc-eks-batch --no-prompts --region sa-east-1
```
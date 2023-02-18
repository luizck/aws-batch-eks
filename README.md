# Deploy

## Criar bucket para artefatos do deploy:
```
export REGION=sa-east-1
aws s3api create-bucket --bucket test-eks-batch   --create-bucket-configuration LocationConstraint=$REGION
```
## Deploy da Stack
```
sam deploy --stack-name test-eks-batch --s3-bucket test-eks-batch  --capabilities CAPABILITY_IAM CAPABILITY_NAMED_IAM CAPABILITY_AUTO_EXPAND
```
## Undeploy:
```
sam delete --stack-name test-eks-batch --no-prompts --region us-east-1
```

## Submit a job:
```
aws --region us-east-1 batch submit-job --job-name hello-world-batch-job --job-queue test-eks-batch --job-definition TestApplicationJob-6d610e40b0a52c2:1
```
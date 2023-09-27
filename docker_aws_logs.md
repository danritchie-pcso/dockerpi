# AWS CLI Reference for ECR
https://awscli.amazonaws.com/v2/documentation/api/latest/reference/ecr/index.html
# Created a repository
```
aws ecr create-repository --repository-name fota-registry --region ap-southeast-1 --profile devdan
{
    "repository": {
        "repositoryArn": "arn:aws:ecr:ap-southeast-1:600582092527:repository/fota-registry",
        "registryId": "600582092527",
        "repositoryName": "fota-registry",
        "repositoryUri": "600582092527.dkr.ecr.ap-southeast-1.amazonaws.com/fota-registry",
        "createdAt": "2023-08-18T17:55:26+08:00",
        "imageTagMutability": "MUTABLE",
        "imageScanningConfiguration": {
            "scanOnPush": false
        },
        "encryptionConfiguration": {
            "encryptionType": "AES256"
        }
    }
}
```
# Docker Login with AWS CLI
```
aws ecr get-login-password --region ap-southeast-1 --profile devdan | docker login --username AWS --password-stdin 600582092527.dkr.ecr.ap-southeast-1.amazonaws.com
WARNING! Your password will be stored unencrypted in /home/joel/.docker/config.json.
Configure a credential helper to remove this warning. See
https://docs.docker.com/engine/reference/commandline/login/#credentials-store

Login Succeeded
```
# Tagging Docker Image
```
docker tag mypi:latest 600582092527.dkr.ecr.ap-southeast-1.amazonaws.com/fota-registry:mypi
```
# Pushing my docker image
```
docker push 600582092527.dkr.ecr.ap-southeast-1.amazonaws.com/fota-registry:mypi
```

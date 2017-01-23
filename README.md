
# docker-registry-login

Shell script for automatically `docker login` in cloud image registries based on env variables.

Currently supported:
 - Google GCR
 - AWS ECR (depends on [`aws-cli`](https://github.com/aws/aws-cli))

## Usage


```sh
export GCR_KEYFILE_JSON=(cat ./json_key.json)
export GCR_PROJECT=some-org-some-awesome-project

./docker-registry-login

# Or

export AWS_ECR_ACCOUNT_ID=682952434345
export AWS_ECR_REPOSITORY=some-org/some-awesome-project
export AWS_ACCESS_KEY_ID=AKIAYROEXODTG9NUQVKF
export AWS_SECRET_ACCESS_KEY=4CPCKXzBcrfk8b8N8b39fTTuLgL3fxCqUiDNMNad
export AWS_ECR_REGION=eu-west-1

./docker-registry-login
```
Finally use $DOCKER_IMAGE_PREFIX for push a docker image
```sh
image=$DOCKER_IMAGE_PREFIX/app:latest

docker build -t $image .
docker push $image
```

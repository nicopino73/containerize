https://aws.amazon.com/blogs/containers/new-using-amazon-ecs-exec-access-your-containers-fargate-ec2/

https://www.ernestchiang.com/en/posts/2021/using-amazon-ecs-exec/

curl "https://s3.amazonaws.com/session-manager-downloads/plugin/latest/mac/sessionmanager-bundle.zip" -o "sessionmanager-bundle.zip"

unzip sessionmanager-bundle.zip

sudo ./sessionmanager-bundle/install -i /usr/local/sessionmanagerplugin -b /usr/local/bin/session-manager-plugin

aws ecs update-service --service mecinov-service --cluster default --enable-execute-command

aws ecs execute-command --profile cg \
    --region us-east-1 \
    --cluster default \
    --task 2092d622234f41a7a92ffc19109a3af5 \
    --command "/bin/bash" \
    --interactive

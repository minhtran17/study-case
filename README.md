# Useful command lines

- Force shell to exit with non-zero exit code if any command fails.
```shell script
set -e
```

- Tracing
```shell script
strace -p <pid>
strace php -h
```

- AWK
```shell script
ls -lah > pu_state.txt
cat pu_state.txt | grep Lazada_MY | awk -F' ' '{sum += substr($5,1,length($5)-1)} END {print sum}'
```

- Terraform

```shell script
image_tag=branch-a
env=qa
instance_name=component1-${env}-${image_tag}
terraform init -backend-config "key=qa/${image_tag}/terraform.tfstate" -force-copy -input=false
terraform apply -auto-approve -var instance_type=t2.micro -var env=${env} -var image_tag=${image_tag} -var instance_name=${instance_name}
terraform destroy -auto-approve -var env=${env} -var image_tag=${image_tag} -var instance_name=${instance_name}
```

- Ansible
```shell script
ansible-galaxy install -f -r requirements.yml -p roles
ansible-playbook playbook-production-cassandra.yml -i production.ini  -vvv
```

- GIT cleanup unused branches
```shell script
git branch --merged | egrep -v "(^\*|master|develop)" | xargs git branch -d
git branch -r | awk '{print $1}' | egrep -v -f /dev/fd/0 <(git branch -vv | grep origin) | awk '{print $1}' | xargs git branch -d
```

- Docker
```shell script
# Mounted volumes
docker inspect -f '{{ .Mounts }}' <containerid>

# Cleanup volumes
docker system prune --volumes
```

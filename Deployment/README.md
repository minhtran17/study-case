# Terraform vs Ansible
- [terraform.pptx](https://github.com/minhtran17/study-case/Deployment/terraform.pptx)
- Orchestration (infrastructure, provision and termination) vs configuration management

## Cache installed plugins (in teamcity)
```dockerfile
RUN mkdir -p /home/buildagent/.terraform.d/plugin-cache
RUN chown -R buildagent:buildagent /home/buildagent/.terraform.d/plugin-cache
COPY .terraformrc /home/buildagent/.terraformrc
```

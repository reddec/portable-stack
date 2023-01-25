# Portable stack

This is "clonable" [portable stack](https://reddec.net/articles/portable-stack/) which can be used by anyone.

The playbook includes DNS records (if defined) updates in Cloudflare, however, you may use any other provider and update logic in `dns.yaml`.

## Checklist

- [ ] Update inventory.yaml and write down your hosts. Pick host name as somthing not bounded to provider: ie `web1`, not `aws-srv-1`. It will help migrate between providers. Optionally, you may set domains names for automatic records update.
- [ ] Update variables.yaml and define your parameters. Use [ansible-vault](https://docs.ansible.com/ansible/latest/vault_guide/index.html) for secrets or alternatives.
- [ ] Update or create stack per host in `deployments/<hostname>/docker-compose.yaml`. Everything in `deployments/<hostname>` will be copied to the remote host before execution, however, only volumes will be backuped by default.

## Deployment

    ansible-playbook -i inventory.yaml playbook.yaml
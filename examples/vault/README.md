# Vault Examples

```sh
$ ansible-vault create db.yml
New Vault password: 1234
Confirm New Vault password: 1234

$ ansible-vault encrypt examples/vault/db-raw.yml
$ ansible-vault edit db.yml

$ ansible localhost --ask-vault-pass -m debug -a var="db_password" -e "@examples/vault/db.yml"
$ ansible-playbook examples/vault/debug.yml --ask-vault-pass -e "@examples/vault/db.yml"
```
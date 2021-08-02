# Inventory

```sh
$ ansible -i inventory/hosts.ini all -m debug -a 'msg="Print var: {{ my_list }}"'
```
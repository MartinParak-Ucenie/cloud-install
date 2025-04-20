# Spustenie Ansible Playbook
zakladny priklad (ak mam inventory zadane v `ansible.cfg`)

`ansible-playbook playbook.yml`

ak chcem len test run bezo zmien na serveri

`ansible-playbook playbook.yml --check`

so zadanym inventarom

`ansible-playbook -i inventory.ini playbook.yml`

ak chcem spustit Playbook na konkretnom serveri (server1.mydomain)

`ansible-playbook playbook.yml --limit server1.mydomain`

ak chcem spustit Playbook na konkretnej skupine z inventara (my_web_servers)

`ansible-playbook playbook.yml --limit my_web_servers`

ak chcem spustit ulohy ako `sudo`

`ansible-playbook playbook.yml --become --ask-become-pass`

# CRUD operacie s vault.yml
## Vytvorenie vault.yml
`ansible-vault create vault.yml`

Pri vytvarani si vypyta heslo, ktore bude pouzivane k pristupu k suboru. Data sa ukladaju vo formate

```
db_user: "my_db_user"
db_password: "my_db_user_password"
api_key: "my_api_key_value"
```
## Zobrazenie vault.yml
`ansible-vault view vault.yml`
## Editovanie vault.yml
`ansible-vault edit vault.yml`
## Desifrovanie vault.yml
odstrani sifrovanie a ponecha subor v citatelnej podobe. 

`ansible-vault decrypt vault.yml`
## Znovuzasifrovanie vault.yml
`ansible-vault encrypt vault.yml`
## Pouzitie vault premennych (playbook)
rovnake to je v roli
```yaml
---
- name: Pouzitie Ansible vault premennych
  hosts: localhost
  tasks:
    - name: Zobrazenie prihlasovacich udajov DB
      debug:
        msg: "Pouzivatel: {{ my_db_user }}, heslo: {{ my_db_user_password }}"
```
### Ak nechcete zadavat heslo vzdy, ked sa pouzije vault premenna
spustajte Ansible playbook s parametrom `--ask-vault-pass`, napriklad

`ansible-playbook playbook.yml --ask-vault-pass`

heslo si vypyta raz, pri spusteni playbooku

#### Alternativne sa da pouzit subor s heslom, napr. `.vault_pass` 
```shell
echo 'moje_heslo_do_vault' > .vault_pass
chmod 400 .vault_pass
```
subor treba pridat do `.gitignore`, necommitovat

#### Spustenie playbooku pomocou suboru s heslom
`ansible-playbook playbook.yml --vault-password-file .vault_pass`
Ansible FreeRADIUS
=========

Installazione del pacchetto FreeRadius su Debian Buster con particolare attenzione alla configurazione (PostgrelSQL/MySQL) per l'uso con OpenWISP2.

Requirements
------------

E' preferibile accoppiare la role "Common" scaricabile da:

``ansible-galaxy install mikysal78.ninux_common``

Role Variables
--------------

Abbiamo queste variabile in defaults/main.yml

| Variable                  | Default              | Comments (type)       |
| :---                      | :---                 | :---                  |
| `freeradius_config`       | `/etc/freeradius/3.0`| E' la path di default che usa Debian per il pacchetto.  |        
| `freeradius_db`           | `postgresql`         | Scegliere di usare PostgreSQL, MySQL o SqLite |
| `freeradius_rest_conn_uri`| `http://127.0.0.1`   | In produzione usare il nome del dominio o `http://127.0.0.1:8000` |
| `freeradius_openwisp`     | `true`               | `False` installa solo FreeRadius; `True` importa i template per l'uso con OpenWisp |
| `conn_host`               | `localhost`          | Host dove risiede il database da usare (solo pgsql e mysql) |
| `conn_port`               | `5432`               | Postgresql porta `5432`, MySQL porta `3306` |
| `conn_loging`             | `openwisp`           | Username che ha accesso al database  |
| `conn_password`           | `CAmBiAmI`           | La password associata all'utente del database |
| `conn_db`                 | `radius`             | Il nome del database da utilizzare |


Dependencies
------------

Il pacchetto `psycopg2` viene installato via pip dalla role.

Example Playbook
----------------

Un esempio di playbook:

```yml
- hosts: freeradius
  become: "{{ sudo | default('yes') }}"
  become_user: root
  roles:
    - freeradius
```

License
-------

BSD

Author Information
------------------

- [MikySal78](https://github.com/mikysal78)

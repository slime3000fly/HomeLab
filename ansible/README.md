# Bitwarden + Ansible

## Vault się nie odblokowuje?

`bw unlock` jest zbugowane (CLI 2026.3.0/2026.4.1 — zwraca token, ale vault dalej "locked").
Zamiast tego:

```bash
bw logout
bw login                          # email + haslo + 2FA
export BW_SESSION="<token z outputu>"
bw status                         # musi byc "status":"unlocked"
```

Nie uzywaj `bw lock` — potem tylko logout/login pomoze.

## Uruchomienie playbooka

```bash
ansible-playbook update_linux.yaml -i host.ini
```


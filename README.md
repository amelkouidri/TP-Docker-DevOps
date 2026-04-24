# TP3 - Ansible

## Objectif
Déployer automatiquement une application 3 tiers sur un serveur distant avec Ansible et Github Actions.

---

## Architecture
```
Navigateur → Apache (port 80) → Backend Spring Boot → PostgreSQL
                             → Frontend Vue.js
```

---

## Structure Ansible
```
ansible/
├── inventories/setup.yml   # serveurs cibles
├── roles/
│   ├── docker/             # installe Docker
│   ├── network/            # crée le réseau app-network
│   ├── database/           # lance PostgreSQL
│   ├── app/                # lance le backend
│   ├── proxy/              # lance Apache
│   └── frontend/           # lance le frontend
└── playbook.yml            # orchestre les rôles
```

---

## Commandes essentielles

```bash
# Tester la connexion
ansible all -i inventories/setup.yml -m ping

# Déployer
ansible-playbook -i inventories/setup.yml playbook.yml
```

---

## Pipeline CI/CD

```
git push → test → sonar → build images → deploy ansible
```

---

## Questions

**3-1 Pourquoi un inventaire ?**
Centralise les serveurs et paramètres de connexion SSH.

**3-2 Pourquoi des rôles ?**
Organise les tâches en modules réutilisables avec une responsabilité unique.

**3-3 Pourquoi `docker_container` ?**
Gère les containers de façon déclarative — on décrit l'état souhaité, Ansible s'en occupe.

**CD automatique sécurisé ?**
Non — une image cassée serait déployée en prod. Solution : utiliser des tags versionnés (`v1.0.2`) au lieu de `latest`.

---

## Accès
- Frontend : http://amel-serine.kouidri.takima.school
- API : http://amel-serine.kouidri.takima.school/departments

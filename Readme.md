# 🕩 Lab 2 : Création et Gestion d'une Vagrant Box

## 🎯 **Objectif**

L'objectif de ce laboratoire est de :

1. Créer une **Vagrant Box** personnalisée à partir d'une version spécifique.
2. Déployer une machine virtuelle (VM) avec une box Ubuntu précise.
3. Installer **Nginx** pour valider la configuration.
4. Publier la Vagrant Box sur **HashiCorp Cloud Registry**.

---

## 🧮 **Prérequis**

Assure-toi d'avoir installé les outils suivants :

- **[Vagrant](https://www.vagrantup.com/downloads)**
- **[VirtualBox](https://www.virtualbox.org/)**
- **Compte sur [Vagrant Cloud](https://app.vagrantup.com/)**

---

## 🚀 **Étapes du Lab**

### 1. **Initialisation de la VM avec une version spécifique**

Initialise une VM à partir d'une version précise de la box `ubuntu/trusty64` :

```bash
vagrant init ubuntu/trusty64 --box-version=0989784874
```

Cela crée un fichier `Vagrantfile` avec la box et sa version.

---

### 2. **Déploiement et Connexion à la VM**

Déploie la VM avec :

```bash
vagrant up
```

Ensuite, connecte-toi à la VM via SSH :

```bash
vagrant ssh
```

---

### 3. **Installation de Nginx**

Une fois connecté à la VM, installe **Nginx** :

```bash
sudo apt-get update
sudo apt-get install -y nginx
```

Dans cette version d'Ubuntu, **systemctl** n'est pas encore disponible. Utilise **service** pour vérifier et gérer Nginx :

- **Démarrer Nginx** :
   ```bash
   sudo service nginx start
   ```
- **Vérifier l'état de Nginx** :
   ```bash
   sudo service nginx status
   ```

---

### 4. **Tester le Serveur Nginx**

Trouve l'adresse IP de la VM :

```bash
ip a
```

Depuis ton hôte, ouvre un navigateur et accède à l'adresse suivante :

```
http://<IP_DE_LA_VM>
```

Utilise `curl` pour vérifier directement depuis la VM :

```bash
curl http://<IP_DE_LA_VM>
```

---

### 5. **Création et Publication de la Box sur HashiCorp Cloud**

1. **Crée une nouvelle box** dans [HashiCorp Cloud Registry](https://app.vagrantup.com/).
2. **Définis les paramètres de base** (nom, version, provider, etc.).
3. **Packager la box existante** avec la commande suivante :

   ```bash
   vagrant package --output nom_de_la_box.box
   ```

4. **Uploader la box** sur HashiCorp Cloud selon les recommandations fournies (bouton "Upload").
5. Valide et publie la box pour la rendre accessible.

---

## 🔧 **Commandes Résumées**

| **Commande**                        | **Description**                                        |
|-------------------------------------|-------------------------------------------------------|
| `vagrant init ubuntu/trusty64 --box-version=0989784874` | Initialise un projet avec une box spécifique.        |
| `vagrant up`                        | Démarre et provisionne la machine virtuelle.          |
| `vagrant ssh`                       | Se connecte à la machine virtuelle via SSH.           |
| `sudo apt-get install -y nginx`     | Installe Nginx sur la VM.                             |
| `sudo service nginx start`          | Démarre Nginx avec la commande "service".             |
| `ip a`                              | Affiche l'adresse IP de la VM.                        |
| `vagrant package --output nom.box`  | Packager la box personnalisée.                        |

---

## 📋 **Conclusion**

Ce lab a permis d'apprendre à :

1. Déployer une VM à partir d'une version spécifique d'une Vagrant Box.
2. Installer et gérer un service comme **Nginx** dans un environnement ancien sans `systemctl`.
3. Packager une box Vagrant personnalisée avec `vagrant package`.
4. Publier et partager la box sur **HashiCorp Cloud Registry**.

Ce laboratoire a été très enrichissant pour comprendre la gestion des boxes et leur déploiement.

---

**🚀 Bon apprentissage avec Vagrant !** 😊

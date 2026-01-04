# `🐧`︲Documentation  : Installer et configurer Debian-13-sans-interface-graphique.

---

Ce dépôt présente un guide complet pour l’installation et la configuration d’un système Debian 13 sans interface graphique dans un environnement virtualisé VMware. Il couvre les différentes étapes du déploiement, de l’installation de la machine virtuelle à la configuration de base du système.

Tu y apprendras à mettre en place un serveur Debian minimal, à gérer le système via la ligne de commande et à préparer un environnement stable et optimisé pour des usages serveur ou d’infrastructure en contexte professionnel.

---

## `📑`︲Sommaire (cliquez pour accéder directement à la section souhaitée)

1. [`📘`︲Introduction.](#introduction)

   * [`❔`︲Contexte et objectifs.](#contexte-et-objectifs)
   * [`🧰`︲Présentation des outils et prérequis.](#presentation-outils-prerequis)

   ---

2. [`🛠️`︲Installation de Debian 13 sans interface graphique.](#installation-debian)

   * [`💿`︲Création et configuration de la VM.](#creation-vm)
   * [`⚙️`︲Installation du système Debian 13.](#installation-systeme)
   * [`🔐`︲Création des comptes et configuration SSH.](#configuration-ssh)

   ---
   
3. [`🧰`︲Outils et ressources utilisées.](#outils-ressources)

---

<a id="introduction"></a>
# `📘`︲Introduction.

---

<a id="contexte-et-objectifs"></a>
### `❔`︲Contexte et objectifs.
> [!NOTE]
> Tu apprendras à installer et configurer un système Debian 13 sans interface graphique au sein d’un environnement virtualisé VMware. Cette installation te permettra de comprendre les bases d’un système Linux minimal, la gestion des paquets, des services et des ressources d’une machine virtuelle.
> L’objectif est de maîtriser l’installation et l’administration d’un serveur Debian en ligne de commande, dans un contexte professionnel, afin de disposer d’un système stable, léger et adapté à des usages serveur ou d’infrastructure en environnement virtualisé.

---

<a id="presentation-outils-prerequis"></a>
### ` 🧰 `︲Présentation des outils et prérequis.
> [!IMPORTANT]
> **Présentation des outils et prérequis :**
> - ` 🐧 `︲**Serveur :** Debian 13 **sans interface graphique** ︲[`🌐`](https://www.debian.org/)
> 
> - ` 📦 `︲**VMWare :** ︲[`🌐`](https://www.vmware.com/)
> 
> - ` ⚡ `︲**PuTTY :** ︲[`🌐`](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

---

<a id="installation-debian"></a>
# ` 🛠️ `︲Installation de Debian 13 sans interface graphique.

---

<a id="creation-vm"></a>
## ` 💿 `︲Création et Configuration de la VM.

> [!IMPORTANT]
> * **Les captures d’écran seront ajoutées progressivement !**
> * **Si une image est peu lisible dans le menu, il suffit de cliquer dessus. L'image s'ouvrira dans un nouvel onglet, vous permettant ainsi de la consulter en taille réelle et d'utiliser la fonction zoom !**

> [!TIP]
> - **Pour afficher les captures d’écran, clique sur le menu déroulant avec l’émoji : `  📸  `.**
> - **Le menu s’ouvrira et affichera la ou les captures d’écran !**

---

` ⚙️ `︲**Configuration de la VM.**

* ` ❓ ` ︲**Hostname :** `srv-fog`.

* ` 📡 ` ︲**Adressage IP :** dynamique (`DHCP`) récupérer une adresse sur le réseau local physique.

* ` 🖼️ ` ︲**Interface graphique :** **__aucune__** (__installation en mode serveur / ligne de commande__).

* ` 🧩 ` ︲**Service à installer :** `ssh` **(SSH activé et démarré)**.

* ` 📏 ` ︲**Mémoire :** `1024 Mo`.

* ` 💾 ` ︲**Disque :** `100 Go`. (*allocation dynamique*).

* ` ❤️ ` ︲**Cœurs :** `1`. (*Optionel*)

<details>
  <summary><strong>📸︲Capture d'écran (Config VMWare).</strong></summary>
  
  <img width="887" height="880" alt="image" src="https://github.com/user-attachments/assets/8671256d-3603-45e0-af58-d9cf730d5d52" />
  
</details>

---

` 🚧 `︲**Couples d’identifiants (Exemple en Labo).**

```
ID : root    | MDP : btssio
ID : btssio  | MDP : btssio
```

* Créer les deux comptes avec ces mots de passe lors de l’installation / configuration.
* Vérifier les droits sudo si nécessaire pour l’utilisateur `btssio`.

---

<a id="installation-systeme"></a>
## ` ⚙️ `︲Installation du système Debian 13.

---

> [!NOTE]
> Cette partie couvre **l’installation de Debian 13 sans interface graphique**.
> Objectif : obtenir un serveur minimaliste, stable et prêt pour héberger FOG !

---

1️⃣︲**Lancement de l’installation depuis l’ISO Debian 13.**

* Sélectionner `Install` (pas “Graphical install”).
* Choisir la **langue :** `Français`
* Choisir le **pays :** `France`
* Disposition clavier : **Français (`AZERTY`)**

<details>
  <summary>📸︲Installation et sélection langue et clavier.</summary>

  <img width="641" height="482" alt="image" src="https://github.com/user-attachments/assets/f7a1f54b-9540-48ce-b3a9-bf605673302b" />
  
  --- 
  
  <img width="800" height="593" alt="image" src="https://github.com/user-attachments/assets/035692f5-ee65-4936-9856-041100e57798" />
</details>

---

2️⃣︲**Configuration réseau.**

* Nom de la machine : `srv-fog`
* Méthode d’adressage : **DHCP (automatique)**
* Domaine : *(laisser vide ou local)*

<details>
  <summary>📸︲Identifiants.</summary>

<img width="799" height="594" alt="image" src="https://github.com/user-attachments/assets/e74ab1d5-33ba-4686-b6c8-c50b86963e06" />

--- 

<img width="802" height="595" alt="image" src="https://github.com/user-attachments/assets/2266ccbd-f9a3-4ab6-8cd0-d2c079c9fecf" />

---

<img width="801" height="596" alt="image" src="https://github.com/user-attachments/assets/40ccea59-94b4-4ba1-88f4-25eeb0370e81" />

---

<img width="796" height="592" alt="image" src="https://github.com/user-attachments/assets/4c376e36-fd1f-439c-a746-8a3c903564aa" />

---

<img width="797" height="591" alt="image" src="https://github.com/user-attachments/assets/b0d8cc27-4859-451b-92a6-fd5cf0d9bc81" />

</details>

---

3️⃣︲**Partitionnement du disque.**

* Disque virtuel : `100Go` **dynamiquement alloué**
* Schéma recommandé :

  * `/` → `60Go`
  * `swap` → `2Go`
  * `/var` → reste du disque
* Type : **Guidé – utiliser tout le disque**, séparé selon les besoins.

<details>
  <summary>📸︲Partitionnement automatique.</summary>
<img width="802" height="594" alt="image" src="https://github.com/user-attachments/assets/ed6046dd-c312-47fb-bce0-79ef312d88bb" />
  
---
  
<img width="797" height="597" alt="image" src="https://github.com/user-attachments/assets/d401aafe-522b-4d87-9a58-c75c25c8f6ba" />

---

<img width="794" height="589" alt="image" src="https://github.com/user-attachments/assets/65948516-8dcc-40c3-883d-1375b6a9f65e" />

---

<img width="803" height="588" alt="image" src="https://github.com/user-attachments/assets/46bb2f9c-b96e-4986-b22c-91a0dae464a1" />

---

<img width="801" height="596" alt="image" src="https://github.com/user-attachments/assets/07d8ee6b-4e9b-406f-baf1-948ba7fe5bad" />

</details>

---

4️⃣︲**Sélection des paquets à installer.**

* Ne **pas** installer d’environnement graphique.
* **Cocher uniquement :**

- [ ] environnement de bureau Debian
- [ ] ... GNOME
- [ ] ... Xfce
- [ ] ... bureau GNOME Flashback
- [ ] ... KDE Plasma
- [ ] ... Cinnamon
- [ ] ... MATE
- [ ] ... LXDE
- [ ] ... LXQt
- [ ] serveur web
- [x] serveur SSH
- [x] utilitaires usuels du système
- [ ] choix d’un assemblage (Blend) de Debian lors de l’installation

---

5️⃣︲**Installation du chargeur de démarrage (GRUB).**

* Installer sur le disque principal `/dev/sda`.
* Une fois l’installation terminée : **retirer l’ISO et redémarrer.**

<details>
  <summary>📸︲Installation Grub et redémarrage.</summary>
  
<img width="803" height="595" alt="image" src="https://github.com/user-attachments/assets/171b3e92-fc9a-4348-8f36-5ea8fcfd55be" />

<img width="802" height="596" alt="image" src="https://github.com/user-attachments/assets/868f4416-77c3-4f45-a338-913e8c6595b3" />

</details>

---
> [!WARNING]
> **Prends un snapshot de ta VM à ce stade (avant de configurer SSH). Cela te permettra de revenir rapidement en arrière en cas de problème !**

---

<a id="configuration-ssh"></a>
## ` 🔐 `︲Création des comptes et configuration SSH.

---

> [!NOTE]
> Cette section configure les **utilisateurs**, le **SSH** et la **sécurisation basique du serveur**.

---

1️⃣︲**Création des utilisateurs.**

* Utilisateur root : `root / btssio`
* Utilisateur standard : `btssio / btssio`
* Vérifie que les deux existent avec :

  ```bash
  cat /etc/passwd | grep btssio
  ```

---

2️⃣︲**Activation du SSH.**

* S’assurer que le paquet est installé :
* En mode **ROOT** : 

  ```bash
   apt install openssh-server -y
  ```
* Démarrer et activer le service :

  ```bash
  $ systemctl enable ssh --now
  $ systemctl status ssh
  ```

<details>
  <summary>📸︲Vérification du service SSH.</summary>
  
<img width="857" height="814" alt="image" src="https://github.com/user-attachments/assets/22247b4e-f8f5-41a4-8da9-cb546dd40862" />

</details>

---

3️⃣︲**Autoriser la connexion root (optionnel).**

* Éditer le fichier de configuration :

  ```bash
  $ nano /etc/ssh/sshd_config
  ```
* Modifier / vérifier ces lignes :

  ```
  PermitRootLogin yes
  PasswordAuthentication yes
  ```
* Redémarrer SSH :

  ```bash
  $ systemctl restart ssh
  ```

> [!WARNING]
> **Ne laissez jamais le compte root activé en production : il ne doit être utilisé que pour les besoins du TP ou des tests internes.**

---

4️⃣︲**Test de connexion distante.**
Depuis la machine hôte :

```bash
ssh btssio@<ip_du_serveur>
```

ou

```bash
ssh root@<ip_du_serveur>
```

<details>
  <summary>📸︲Connexion SSH réussie (Putty).</summary>
  
<img width="1481" height="914" alt="image" src="https://github.com/user-attachments/assets/d71b108c-696f-42d7-a863-e7ebfb7f4b94" />

</details>

---

> [!WARNING]
> **Prends un instantané de la VM après avoir validé le SSH, afin de pouvoir y revenir en cas de problèmes !**

---

<a id="outils-ressources"></a>
# ` 🧰 `︲Outils et ressources utilisées.

---

> [!TIP]
> Vous trouverez ici la liste de tous les outils, ressources et services utilisés pour la création de cette documentation.
> Les liens correspondants sont accessibles en cliquant sur l’emoji  : `  🌐  ` .

--- 

* ` 🤖 ` **︲GPT `Mini`** ︲  [`🌐`](https://chatgpt.com/)
  
* ` ❓ ` **︲Markdownguide.org**   ︲[`🌐`](https://www.markdownguide.org/)
  
* ` 🤖 ` **︲NoteBookLM**   ︲[`🌐`](https://notebooklm.google.com/)
  
* ` ✂️ ` **︲Screenpresso**   ︲[`🌐`](https://www.screenpresso.com/fr/)
  
* ` 😀 ` **︲Smiley.cool**   ︲[`🌐`](https://smiley.cool/emoji-list.php)
  
* ` ❓ ` **︲Syntaxe de base pour l’écriture et la mise en forme**  ︲ [`🌐`](https://docs.github.com/fr/get-started/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

---

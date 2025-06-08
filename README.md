# Utilisation de Claude Desktop avec MCP pour accéder au système de fichiers

Permet à Claude Desktop de lire, écrire, déplacer et rechercher des fichiers sur votre ordinateur, avec votre permission.

---

    1. Télécharger Claude Desktop

- Téléchargez et installez la version macOS ou Windows.  
- Vérifiez d’avoir la dernière version via `Claude > Vérifier les mises à jour…`

---

     2. Configurer le serveur filesystem

- Ouvrez `Claude > Paramètres… > Développeur > Modifier la configuration`.  
- Remplacez le contenu du fichier `claude_desktop_config.json` par :

  ```json
  {
    "mcpServers": {
      "filesystem": {
        "command": "npx",
        "args": [
          "-y",
          "@modelcontextprotocol/server-filesystem",
          "C:\\Users\\username\\Desktop",
          "C:\\Users\\username\\Downloads"
        ]
      }
    }
  }


## Remplacez username par votre nom d’utilisateur et adaptez les chemins aux dossiers accessibles.

## Vérifiez que Node.js est installé (node --version dans terminal ou invite de commandes). Sinon, installez-le depuis nodejs.org.

    3. Redémarrer Claude Desktop
Après modification, redémarrez l’application.

## Une icône en forme de curseur apparaît dans la zone de saisie, donnant accès aux outils filesystem.

    4. Utilisation
## Exemples de commandes à tester :

    « Écris un poème sur mon bureau »

    « Trouve les fichiers liés au travail dans mes téléchargements »

    « Déplace les images du bureau vers un dossier ‘Images’ »

Claude demandera toujours votre approbation avant d’exécuter une action.





---

## Pourquoi installer Node.js ?

Claude Desktop utilise une commande `npx` (fournie avec Node.js) pour lancer un serveur qui permet d'accéder aux fichiers de votre ordinateur.

👉 Sans Node.js, Claude ne pourra pas lire, écrire ou déplacer des fichiers sur votre machine.

📦 Pour installer Node.js : [https://nodejs.org](https://nodejs.org)

Pour vérifier que Node est bien installé, utilisez cette commande dans votre terminal ou invite de commandes :

```bash
node --version































---

# Guide complet pour installer et lancer le serveur MCP avec MySQL (XAMPP)

---

## 0. Cloner le projet MCP depuis GitHub

Avant tout, il faut récupérer le projet sur ta machine.

1. Ouvre un terminal (cmd).
2. Place-toi dans le dossier où tu veux installer le projet, par exemple :

```bash
cd C:\Users\Moi
```

3. Clone le dépôt avec la commande (remplace l’URL par la bonne si nécessaire) :

```bash
git clone https://github.com/benborla29/mcp-server-mysql.git
```

4. Va dans le dossier du projet :

```bash
cd mcp-server-mysql
```

5. Installe les dépendances Node.js :

```bash
npm install
```

---

## 1. Démarrer MySQL via XAMPP

* Ouvre le **Panneau de contrôle XAMPP**.
* Clique sur **Start** à côté de **MySQL**.
* Assure-toi que MySQL tourne (bouton vert).

---

## 2. Créer la base de données dans phpMyAdmin

* Clique sur **Admin** dans XAMPP à côté de MySQL (ouvre phpMyAdmin).
* Clique sur **Bases de données**.
* Crée une nouvelle base : `mcp_mysql`.
* Clique sur **Créer**.

---

## 3. Créer un utilisateur MySQL et lui donner des droits

* Dans phpMyAdmin, onglet **Utilisateurs**.
* Clique sur **Ajouter un utilisateur**.
* Nom : `mcpuser`
* Hôte : `localhost`
* Mot de passe : `SANOUsalimata1998@`
* Donne-lui tous les privilèges (ou au moins sur la base `mcp_mysql`).
* Clique sur **Exécuter**.

---

## 4. Tester la connexion MySQL en ligne de commande

* Dans le terminal, tape :

```bash
mysql -u mcpuser -p
```

* Entre le mot de passe.
* Puis tape :

```sql
USE mcp_mysql;
```

* Si ça fonctionne, c’est bon !

---

## 5. Configurer le serveur MCP

Voici un exemple de fichier JSON de configuration (dans ton projet) :

```json
{
  "mcpServers": {
    "mcp_server": {
      "command": "node",
      "args": [
        "C:\\Users\\Moi\\mcp-server-mysql\\dist\\index.js"
      ],
      "env": {
        "MYSQL_HOST": "127.0.0.1",
        "MYSQL_PORT": "3306",
        "MYSQL_USER": "mcpuser",
        "MYSQL_PASS": "SANOUsalimata1998@",
        "MYSQL_DB": "mcp_mysql",
        "ALLOW_INSERT_OPERATION": "true",
        "ALLOW_UPDATE_OPERATION": "true",
        "ALLOW_DELETE_OPERATION": "true",
        "PATH": "C:\\Users\\Moi\\AppData\\Roaming\\npm",
        "NODE_PATH": "C:\\Users\\Moi\\AppData\\Roaming\\npm\\node_modules"
      }
    }
  }
}
```

---

## 6. Lancer le serveur MCP

* Dans le terminal, place-toi dans le dossier du projet :

```bash
cd C:\Users\Moi\mcp-server-mysql
```

* Puis lance :

```bash
node dist/index.js
```

* Tu devrais voir que le serveur se connecte à MySQL et démarre.

---

## Résumé rapide

| Étape                 | Commande / Action                                                             |
| --------------------- |-------------------------------------------------------------------------------|
| Cloner projet         | `git clone https://github.com/benborla29/mcp-server-mysql.git`                |
| Installer dépendances | `npm install`                                                                 |
| Démarrer MySQL        | Ouvrir XAMPP > Start MySQL                                                    |
| Créer base de données | Via phpMyAdmin, créer `mcp_mysql`                                             |
| Créer utilisateur     | Via phpMyAdmin, utilisateur `mcpuser`                                         |
| Tester connexion      | `mysql -u mcpuser -p` puis `USE mcp_mysql;`                                   |
| Configurer MCP        | Voir fichier JSON avec variables d’environnement (claude_desktop_config.json) |
| Lancer MCP            | `node dist/index.js`                                                          |

---

  Node (Node.js) : c’est l’environnement qui permet d’exécuter du code JavaScript en dehors du navigateur, par exemple sur ton ordinateur ou un serveur.

npm : c’est le gestionnaire de paquets (packages) pour Node.js. Il sert à installer, mettre à jour et gérer les bibliothèques et outils que tu utilises dans ton projet Node.js.

En résumé :

Node = le moteur qui fait tourner ton code JavaScript.

npm = l’outil qui te permet d’installer et gérer les modules pour Node.js.
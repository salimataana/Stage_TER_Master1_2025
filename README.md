# Utilisation de Claude Desktop avec accès au système de fichiers

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
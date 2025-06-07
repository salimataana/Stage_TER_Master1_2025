# Utilisation de Claude Desktop avec accès au système de fichiers

Ce guide explique comment étendre **Claude pour Desktop** afin qu'il puisse lire, écrire, déplacer et rechercher des fichiers sur votre ordinateur — toujours avec votre permission.

---

## 1. Télécharger Claude Desktop

- Choisissez la version **macOS** ou **Windows** (Linux non pris en charge).  
- Installez l’application.  
- Vérifiez que vous avez la dernière version via le menu :  
  `Claude` > **Vérifier les mises à jour…**

---

## 2. Ajouter le serveur MCP pour le système de fichiers

1. Ouvrez le menu **Claude** > **Paramètres…** > onglet **Développeur** > cliquez sur **Modifier la configuration**.  
2. Cela ouvre le fichier `claude_desktop_config.json`. Remplacez son contenu par exemple par :  

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
   


Remplacez username par votre nom d’utilisateur.

Adaptez les chemins aux dossiers que Claude peut accéder/modifier.

Assurez-vous que Node.js est installé :

Ouvrez le terminal (macOS) ou l’invite de commande (Windows).

Tapez node --version.

Si la commande n’est pas reconnue, installez Node depuis nodejs.org.

3. Redémarrer Claude Desktop
Après modification, redémarrez l’application.

Une icône en forme de curseur apparaîtra dans la zone de saisie, permettant d’accéder aux outils du serveur filesystem.

4. Tester les fonctionnalités
Essayez des commandes comme :

Peux-tu écrire un poème sur mon bureau ?

Quels fichiers liés au travail sont dans mes téléchargements ?

Déplace toutes les images de mon bureau dans un dossier "Images".

Claude demandera toujours votre permission avant d’exécuter une action.


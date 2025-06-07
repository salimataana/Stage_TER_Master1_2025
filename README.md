# Stage_TER_Master1_2025

                             ### EXPLICATION DU PROJET


                    1-- MCP POUR MON SYSTEME DE FICHIERS


# Utilisation de Claude Desktop avec accès au système de fichiers

**Ce guide explique comment étendre Claude pour Desktop afin qu'il puisse lire, écrire, déplacer et rechercher des fichiers sur votre ordinateur — toujours avec votre permission.

Étapes principales
Téléchargez Claude Desktop
Choisissez la version macOS ou Windows (Linux non supporté). Installez et assurez-vous d’avoir la dernière version via le menu Claude > « Vérifier les mises à jour… ».

Ajoutez le serveur MCP pour le système de fichiers

Ouvrez le menu Claude > « Paramètres… » > « Développeur » > « Modifier la configuration ».

Modifiez le fichier claude_desktop_config.json en y ajoutant la configuration du serveur filesystem, par exemple :


{
  "mcpServers": {
    "filesystem": {
      "command": "npx",
      "args": [
        "-y",
        "@modelcontextprotocol/server-filesystem",
        "C:\\Users\\username\\Desktop",
        "C:\\Users\\username\\Downloads"
        "C:\\Users\\username\\Documents"
      ]
    }
  }
}




Remplacez username par votre nom d’utilisateur et adaptez les chemins selon vos dossiers.

Node.js doit être installé (vérifiez avec node --version dans le terminal).

Redémarrez Claude Desktop
Une icône en forme de curseur apparaîtra dans la zone de saisie, donnant accès aux outils du serveur filesystem.

Testez les fonctionnalités
Demandez par exemple :

« Peux-tu écrire un poème sur mon bureau ? »

« Quels fichiers liés au travail sont dans mes téléchargements ? »

« Déplace toutes les images de mon bureau dans un dossier ‘Images’. »
Claude demandera votre autorisation avant toute action.
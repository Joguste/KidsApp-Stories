# KidsApp-Stories
A repository to store our app audio files. A great alternative for Cloud storage and easy way to get access to our files.

# 📚 KidsApp-Stories — Ajout de nouveaux audios

Ce guide explique étape par étape comment ajouter de nouveaux fichiers audio (MP3) dans le dépôt `KidsApp-Stories`, les intégrer proprement au JSON de configuration, et finaliser leur ajout dans la base de données via Laravel.

---

##  Étapes à suivre

### 1. 🎵 Ajouter le fichier MP3

- Placez le fichier `.mp3` dans le dossier désigné du dépôt (ex. : `public/audios/`, `assets/audio/`, ou un dossier équivalent selon la structure actuelle , on n'a pas de  dossier donc dans le repo direct).
- Assurez-vous que le nom du fichier est **lisible et sans espace** (utilisez des tirets ou des underscores).

---

### 2. 🌐 Obtenir le lien CDN via [jsDelivr](https://www.jsdelivr.com/)

Une fois le fichier commité et poussé sur GitHub, jsDelivr peut servir de CDN automatique.

- Utilisez la structure suivante pour générer le lien :
`https://cdn.jsdelivr.net/gh/<votre-utilisateur>/<votre-repo>@<branch>/chemin/vers/le/fichier.mp3`
Exemple :
`https://cdn.jsdelivr.net/gh/monUser/KidsApp-Stories@main/public/audios/histoire-lion.mp3`


---

### 3. 🧠 Ajouter l'entrée dans le fichier JSON

- Ouvrez le fichier JSON contenant la liste des audios (par exemple : `resources/data/audios.json`).
- Ajoutez une nouvelle entrée en respectant la structure suivante :

```json
{
    "id": 7,
    "title": "Le lion et la souris",
    "url": "https://cdn.jsdelivr.net/gh/monUser/KidsApp-Stories@main/(cheminDossier)/histoire-lion.mp3",
    "lang": "fr",
    "short_description": "Une histoire pour enfants",
    "author": "Horace van Offel",
    "duration": 322,
    "category": "Conte",
    "min_age": 3,
    "max_age": 8
}
```
---
### 4. 📤 Commit et push sur GitHub
 Enregistrez vos modifications, puis poussez-les sur le dépôt distant :

```bash 
git add .
git commit -m "Ajout d'un nouvel audio : Mon histoire audio"
git push origin main
```
---

### 5.⚙️ Lancer la commande artisan pour synchronisation
Une fois les fichiers mis à jour sur GitHub, exécutez la commande suivante dans le back office (depuis la racine du projet Laravel) :

```bash
php artisan audios:sync
```

[简体中文](README.md) | [English](README.en.md) | [Русский](README.ru.md) | [日本語](README.ja.md) | [한국어](README.ko.md) | [Español](README.es.md) | [العربية](README.ar.md) | [Čeština](README.cs.md) | [Dansk](README.da.md) | [Deutsch](README.de.md) | [Esperanto](README.eo.md) | [فارسی](README.fa.md) | [Suomi](README.fi.md) | [Français](README.fr.md) | [Ελληνικά](README.gr.md) | [Magyar](README.hu.md) | [Bahasa Indonesia](README.id.md) | [Italiano](README.it.md) | [മലയാളം](README.ml.md) | [Nederlands](README.nl.md) | [Norsk](README.no.md) | [Polski](README.pl.md) | [Português](README.ptbr.md) | [Română](README.ro.md) | [Türkçe](README.tr.md) | [Українська](README.ua.md) | [Tiếng Việt](README.vn.md)

# ☁️ cloud-browser — Navigateur cloud gratuit

Utilisez la machine virtuelle Ubuntu gratuite de GitHub Actions pour lancer un bureau cloud accessible depuis votre navigateur, avec Chrome intégré. Ouvrez une page web et vous avez un PC cloud connecté à Internet — éteignez-le quand vous avez fini. Entièrement gratuit.

## ✨ Fonctionnalités

- 🌐 Bureau Ubuntu + navigateur Chrome, piloté directement dans votre navigateur
- ⌨️ Méthode de saisie chinoise fcitx5 intégrée (Pinyin), basculez entre chinois et anglais avec `Ctrl+Space`
- 📋 Le texte chinois copié sur votre téléphone peut être collé directement dans le bureau distant
- 🖱️ Menu contextuel du bureau pour changer de méthode de saisie ou redémarrer Chrome en un clic
- 🌐 Accès via le tunnel Cloudflare — pas d'IP publique, pas de redirection de port nécessaire
- 🖱️ Connectez-vous depuis un téléphone, une tablette ou un ordinateur (client web noVNC)
- ⏱️ Chaque session dure jusqu'à ~6 heures, et vous pouvez l'annuler à tout moment

## 🚀 Utilisation (forkez et c'est parti)

### Étape 1 : Forkez ce projet

Cliquez sur le bouton **Fork** en haut à droite de cette page pour copier le projet dans votre propre compte GitHub. Après le fork, vous arriverez dans le dépôt `your-username/cloud-browser`.

> 💡 Pourquoi forker ? GitHub Actions ne peut s'exécuter que sur les dépôts de votre propre compte — le fork vous donne la permission de lancer des sessions.

### Étape 2 : Démarrez le navigateur cloud

1. Allez sur la page de votre dépôt forké et cliquez sur l'onglet **Actions** en haut
2. Trouvez **Free Cloud Browser** dans la barre latérale gauche et cliquez dessus
3. Cliquez sur le bouton **Run workflow** à droite — deux champs de saisie apparaissent :

| Paramètre | Description |
|-----------|-------------|
| Mot de passe VNC | Le mot de passe que vous saisirez pour vous connecter au bureau ; seuls les 8 premiers caractères sont pris en compte, utilisez lettres + chiffres (ex. `abc12345`), **notez-le** ; mot de passe jetable — n'utilisez pas un mot de passe que vous utilisez ailleurs |
| Durée d'exécution | Combien de minutes cette session reste active ; par défaut 300 (5 heures), maximum 350 |

4. Cliquez sur le bouton vert **Run workflow** pour confirmer, et votre navigateur cloud commence à démarrer

### Étape 3 : Obtenez l'URL d'accès

1. Sur la page Actions, cliquez sur la session que vous venez de lancer (celle du haut ; un point jaune signifie qu'elle est en cours)
2. Attendez environ 2 à 4 minutes que la VM finisse d'installer les logiciels et de configurer le tunnel
3. Cliquez sur l'étape de build pour développer les journaux, et faites défiler vers le bas pour trouver une URL comme celle-ci :

```
https://xxx-xxx-xxx.trycloudflare.com/vnc.html
```

4. Copiez cette URL et ouvrez-la dans un navigateur (le navigateur intégré de votre téléphone fonctionne très bien)

### Étape 4 : Connectez-vous et utilisez

1. Sur la page noVNC qui s'ouvre, cliquez sur **Connect**
2. Saisissez le mot de passe VNC défini à l'étape 2
3. Vous verrez le bureau Ubuntu et Chrome — profitez-en 🎉

> ⌨️ Méthode de saisie : Pinyin chinois par défaut ; appuyez sur **Ctrl+Space** pour basculer entre chinois et anglais, ou faites un clic droit sur le bureau et choisissez « Switch Input Method 中/英 ».
> 📋 Coller du chinois : copiez du texte chinois sur votre téléphone et collez-le directement dans le bureau distant.

### Étape 5 : N'oubliez pas de l'éteindre

- Retournez sur la page Actions, ouvrez cette session et cliquez sur **Cancel run** en haut à droite — la VM est détruite et le tunnel cesse de fonctionner
- Elle se termine aussi automatiquement une fois la durée définie écoulée, donc pas de souci

## ⚠️ Remarques

- **L'URL est différente à chaque fois** : les anciennes URL cessent de fonctionner une fois la session précédente terminée — utilisez toujours l'URL des journaux de la dernière session
- **Rien n'est enregistré** : une fois la VM détruite, les favoris du navigateur, les fichiers téléchargés et les sessions de connexion sont tous effacés — déplacez les fichiers importants à temps
- **Règles du mot de passe** : lettres et chiffres uniquement, 8 caractères maximum ; c'est un mot de passe jetable, n'utilisez pas un mot de passe que vous utilisez régulièrement
- **Ne cliquez pas sur Re-run** : pour démarrer une nouvelle session, cliquez sur **Run workflow** — Re-run exécuterait l'ancien code
- **Connexion lente/laggy** : le tunnel passe par Cloudflare, donc les vitesses depuis la Chine continentale dépendent de vos conditions réseau — utilisable, mais ne vous attendez pas à des miracles

## 🛠️ Vous voulez le personnaliser vous-même ?

Le fichier de workflow se trouve à `.github/workflows/cloud-browser.yml` — ouvrez-le directement dans l'interface web de GitHub, modifiez-le, et vos changements prennent effet au commit.

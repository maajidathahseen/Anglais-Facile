# Anglais-Facile
📌 1. Prérequis
Avant de commencer, assurez-vous d’avoir installé :

Python 3.12+
Git
VS Code (ou tout autre éditeur de code)
Une connexion internet
Vérifiez que Python fonctionne :

python --version
Vérifiez Git :

git --version
📌 2. Cloner le projet depuis GitHub
2.1. Copier l’URL du dépôt
Cliquez sur Code → Copy dans GitHub pour récupérer l’URL du dépôt.

Exemple :

https://github.com/Salma-AZIZ/wagtail-site-vitrine-starter.git
2.2. Ouvrir un terminal et cloner
Placez-vous dans le dossier où vous souhaitez mettre votre projet :

cd C:\Users\VotreNom\Documents
Clonez le dépôt :

git clone https://github.com/Salma-AZIZ/wagtail-site-vitrine-starter.git
Entrez dans le projet :

cd wagtail-site-vitrine-starter
2.3. Ouvrir dans VS Code
code .
📌 3. Installer et lancer le projet
3.1. Créer un environnement virtuel
python -m venv venv
Activer :

Windows :
venv\Scripts\Activate.ps1
macOS / Linux :
source venv/bin/activate
3.2. Installer les dépendances
Si le projet contient un requirements.txt :

pip install -r requirements.txt
Sinon :

pip install "Django>=5.2,<5.3" "wagtail>=7.2,<7.3"
3.3. Appliquer les migrations
python manage.py migrate
3.4. Créer un utilisateur admin
python manage.py createsuperuser
3.5. Lancer le serveur
python manage.py runserver
Accéder au site :

➡️ http://127.0.0.1:8000/

Accéder à l’administration :

➡️ http://127.0.0.1:8000/admin/

📌 4. Structure du projet
Voici les fichiers les plus importants du projet :

home/
│
├── models.py                  ← Définit les types de pages et leurs champs
│
└── templates/
       ├── base.html           ← Structure globale (header, footer)
       ├── home_page.html      ← Page d'accueil
       ├── services_page.html  ← Page "Nos services"
       ├── about_page.html     ← Page "À propos"
       └── contact_page.html   ← Page "Contact"
sitedemo
   └── templates/
       ├── base.html           ← Structure globale (header, footer)
       └── ...
Retenez :
models.py = structure des données (ce qui apparaît dans l’admin)
templates = design et mise en page
admin Wagtail = interface pour modifier le contenu du site
📌 5. Créer les pages dans Wagtail
Dans http://127.0.0.1:8000/admin/ :

Allez dans Pages

Cliquez sur Ajouter une page

Ajoutez :

HomePage → comme page d’accueil
ServicesPage → slug : nos-services
AboutPage → slug : a-propos
ContactPage → slug : contact
Ces slugs correspondent aux liens du menu dans le site.

📌 6. Modifier le contenu du site depuis l’admin Wagtail
✨ Page d'accueil (HomePage)
Vous pouvez modifier :

Titre principal
Sous-titre
Texte introductif
Image du hero
Boutons et leurs liens
Services présentés sur la home
Ajouter un service dans l'accueil
Dans “Aperçu des services” → cliquez sur Ajouter un service :

Badge (ex : 01)
Titre
Description
Image
Points clés (facultatif)
✨ Page "Nos services"
Vous pouvez :

Définir un titre et un sous-titre
Ajouter plusieurs services complets
Ajouter une image + une liste de points clés pour chaque service
✨ Page "À propos"
Vous pouvez :

Modifier le titre et le sous-titre
Ajouter du contenu riche (texte formaté)
Ajouter une image principale
Écrire une légende
✨ Page "Contact"
Vous pouvez modifier :

Email
Téléphone
Adresse
Texte introductif
Texte au-dessus du formulaire
De plus, vous pouvez ajouter les champs du formulaire un par un selon vos besoins (ex : nom, prénom, email, message, téléphone, sujet…). Wagtail vous permet de créer un formulaire personnalisé directement depuis l’interface d’administration, sans écrire de code : il suffit d’aller dans l’onglet “Form fields” / “Champs du formulaire” et d’ajouter les champs souhaités.

📌 7. Modifier l’apparence du site (HTML & CSS)
Vous pouvez personnaliser :

couleurs
polices
tailles
mise en page
sections à afficher/cacher
Cela se fait dans les fichiers HTML du dossier templates.

⚠️ IMPORTANT Ne supprimez pas les :

{{ page.champ }}
Car ce sont les champs connectés au CMS. Vous pouvez par contre les déplacer, styliser, mettre dans des colonnes, etc.

📌 8. Enlever les textes d’exemple dans les templates
Dans les templates, vous verrez parfois :

{{ page.hero_title|default:"Titre d’exemple" }}
Cela permet de voir un site fonctionnel même si l’admin est vide.

Si vous voulez utiliser uniquement votre contenu, remplacez par :

{{ page.hero_title }}
Faites-le aussi pour :

sous-titres
textes d’intro
adresse, email
titres de section
contenu par défaut
📌 9. Adapter ce modèle à votre projet
Ce template est fait pour être personnalisé facilement. Vous pouvez :

✔ Adapter l’identité visuelle
changer les couleurs
remplacer les images
modifier les polices
mettre votre logo dans base.html
✔ Modifier le contenu
changer tous les textes depuis l’admin
ajouter vos services
écrire votre histoire, vos valeurs
✔ Ajouter vos propres pages
Vous pouvez dupliquer un modèle dans models.py pour ajouter :

une page Blog
une page Témoignages
une page FAQ
une page Équipe
📌 10. Aller plus loin
Idées d’améliorations possibles :

Configurer l’envoi d’emails pour le formulaire de contact (voir section 11)
Ajouter une galerie photo
Ajouter une page Blog avec StreamField
Ajouter un thème couleur personnalisable
Ajouter des animations CSS
Voici une section toute prête que tu peux copier-coller dans ton README 👇

📌 11. Configurer l’envoi d’emails (formulaire de contact)
La page Contact peut être configurée pour envoyer un email via Gmail lorsque quelqu’un soumet le formulaire. Pour cela, on va utiliser :

un compte Gmail
un mot de passe d’application Gmail
un fichier .env pour stocker les identifiants en sécurité
la librairie python-dotenv pour charger le .env dans Django.
11.1. Créer un mot de passe d’application Gmail
Connectez-vous à votre compte Google (celui qui enverra les emails).

Allez dans Gestion du compte Google → Sécurité.

Activez la validation en deux étapes (2FA) si ce n’est pas déjà fait.

Ensuite, allez dans Mots de passe d’application.

Créez un nouveau mot de passe :

Application : Mail
Appareil : Autre (Django) par exemple
Google vous donne un mot de passe du type :

abcd efgh ijkl mnop
➜ Gardez-le précieusement : c’est ce que nous utiliserons dans le projet (⚠️ sans les espaces dans le .env).

11.2. Créer le fichier .env à la racine du projet
À la racine du projet (là où se trouve manage.py), créez un fichier .env :

EMAIL_HOST_USER=ton_email@gmail.com
EMAIL_HOST_PASSWORD=TONMOTDEPASSEAPPLICATION
⚠️ Important :

Pas de guillemets
Pas d’espaces autour du =
Remplacez TONMOTDEPASSEAPPLICATION par le mot de passe d’application Gmail sans espaces.
Pensez à ajouter .env dans votre .gitignore pour ne pas le pousser sur GitHub :

.env
11.3. Charger le .env dans les settings (dev.py)
Dans le fichier de configuration settings/dev.py (ou le fichier de settings que vous utilisez en local), ajoutez en haut :

from dotenv import load_dotenv
import os

load_dotenv()  # charge automatiquement le fichier .env à la racine du projet
Puis, plus bas dans le fichier, ajoutez ou adaptez la configuration email :

EMAIL_BACKEND = "django.core.mail.backends.smtp.EmailBackend"
EMAIL_HOST = "smtp.gmail.com"
EMAIL_PORT = 587
EMAIL_USE_TLS = True

EMAIL_HOST_USER = os.environ.get("EMAIL_HOST_USER")
EMAIL_HOST_PASSWORD = os.environ.get("EMAIL_HOST_PASSWORD")
💡 En production, vous pourrez utiliser le même principe, mais avec un fichier de settings production.py ou des variables d’environnement directement sur le serveur.

11.4. Vérifier que la configuration est bien prise en compte
Dans un terminal :

python manage.py shell
Puis dans le shell Python :

from django.conf import settings
print(settings.EMAIL_HOST_USER)
print(settings.EMAIL_HOST_PASSWORD is not None)
Vous devez voir :

ton_email@gmail.com
True
Si EMAIL_HOST_USER est None ou que False s’affiche, cela signifie que le .env n’est pas lu correctement.

11.5. Expéditeur de l’email (From)
Pour éviter les erreurs d’authentification côté Gmail, l’adresse d’expéditeur doit être cohérente avec le compte configuré.

Dans votre code d’envoi d’email (formulaire Django ou Wagtail), utilisez de préférence :

from django.conf import settings

from_email = settings.EMAIL_HOST_USER
Ainsi, les emails seront envoyés depuis la même adresse Gmail que celle configurée dans le .env.



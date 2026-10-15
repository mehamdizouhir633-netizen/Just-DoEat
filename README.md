# Just Do Eat — "Your Food, Your Mood"

Application de commande de repas pour un établissement OFPPT. Prototype front-end : **PWA** installable sur Android, avec un projet **Capacitor** prêt pour fabriquer un **APK**.

## Ce qui fonctionne
- Accueil (logo, slogan, bannière promo, recherche, catégories), menu, fiche produit avec suppléments et quantité, prix recalculé en direct.
- Panier (quantités, suppression, sous-total, code promo `OFPPT10` = -10 %), commande avec nom, créneau de retrait (créneaux complets désactivés) et paiement espèces/carte **au retrait**.
- Confirmation avec numéro de commande unique et code de retrait à 4 chiffres.
- Suivi : Commande reçue → En préparation → Prête à récupérer → Récupérée, historique, fidélité « 10 commandes = la suivante offerte ».
- Admin (`#/admin`, code **admin123**) : commandes du jour et changement de statut, produits (nom, description, prix, disponibilité, photo, suppléments, ajout/suppression), créneaux et capacités, ventes, historique.

## Limites (honnêtes)
Pas de serveur ni de synchronisation : tout est enregistré dans le `localStorage` **de l'appareil**. Le client et l'admin ne partagent leurs données que sur le **même appareil/navigateur**. Pas de vrai paiement ni d'e-mail. Pour un usage réel avec plusieurs téléphones, il faudra ajouter un backend.

## Tester en local
```
python3 -m http.server 8080     # puis ouvrir http://localhost:8080
```

## Photos
Les images sont dans `img/` et nommées par identifiant produit (`am.jpg`, `fassi.jpg`, `atlas.jpg`, `bowl.jpg`, `club.jpg`, `thon.jpg`, `pates.jpg`, `fm-thon.jpg`, `fm-bowl.jpg`). Sans photo, l'app affiche un visuel illustré. L'admin peut aussi changer la photo d'un produit depuis son téléphone.

## Obtenir l'APK (3 façons)

### A. GitHub Actions (le plus simple, sans Android Studio)
1. Créez un dépôt GitHub et envoyez-y tout ce dossier.
2. Onglet **Actions** → **Build APK** → **Run workflow**.
3. Après quelques minutes, téléchargez `JustDoEat-apk` (contient `app-debug.apk`) et installez-le sur le téléphone (autoriser les sources inconnues).

### B. Android Studio
```
npm install
npm run prepare:www
npx cap add android
npx cap sync android
npx cap open android      # puis Build > Build APK(s)
```

### C. PWA (sans APK)
Hébergez le dossier sur un site HTTPS (GitHub Pages, Netlify…), ouvrez-le dans Chrome Android → menu → **Installer l'application**. Vous pouvez aussi générer un APK/AAB depuis cette URL avec pwabuilder.com.

L'APK debug est signé avec une clé de debug : parfait pour l'installer, pas pour le Play Store (il faudra une clé de release).

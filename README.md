# rekit. — Student Starter Kits

Site web de ReKit (« Rent. Reuse. Repeat. »), bilingue FR/EN et pensé pour le mobile d'abord.
C'est une maquette fonctionnelle en HTML, CSS et JavaScript (modules ES), sans étape de build.

## Lancer en local
```bash
cd rekit
python3 -m http.server 4173   # ou : npx serve .
```
Ouvrir http://localhost:4173

## Déployer sur Vercel
Importer le dossier dans Vercel (framework : « Other », pas de commande de build, dossier de sortie : `.`).
Le routage utilise des hash (`#/boxes`) : aucune configuration serveur n'est nécessaire.

## Structure
```
index.html              Coquille (header, main, footer)
assets/css/tokens.css   Charte : couleurs, typos, rayons, ombres
assets/css/styles.css   Composants et mises en page
assets/js/app.js        Header, footer, routes, événements globaux
assets/js/router.js     Routeur par hash
assets/js/i18n.js       FR/EN : tr('fr', 'en'), formats de prix et de dates
assets/js/data.js       Box, kits, prix, sources  ← À MODIFIER pour changer l'offre
assets/js/store.js      Panier et commandes (localStorage, à remplacer par une API)
assets/js/ui.js         Composants : icône, photo, badge, modale, toast, champs
assets/js/icons.js      Sous-ensemble d'icônes Lucide (SVG inline)
assets/js/pages/*.js    Une page = render() + mount()
assets/vendor/qrcode.js Génération du QR code de retour (MIT)
```

## Charte graphique (2026), comment elle est appliquée
- **Logo** : fichiers officiels dans `assets/brand/` (couleur, négatif blanc, bleu nuit), jamais redessinés ni modifiés, 112 px minimum à l'écran (la charte demande au moins 100 px).
- **Favicon « r. »** : uniquement dans l'onglet du navigateur (`favicon.ico` 16/32/48, PNG 180, 192 et 512).
- **Couleurs** : `assets/css/tokens.css`, palette stricte, pas de dégradé, environ 60 % blanc, 30 % bleu, 10 % orange. Sur le bleu ou l'orange, le texte est toujours en bleu nuit.
- **Typographies** : titres en Fredoka SemiBold/Bold et en bleu, accroches courtes en orange. Textes en TT Commons Pro si elle est installée. Sinon le site utilise Figtree, une police gratuite qui la remplace en attendant la licence (voir le commentaire dans `tokens.css` pour l'auto-héberger).

## Règles de contenu
- Les prix viennent de la proposition du pitch (nov. 2026) et restent **à valider**. Le tarif annuel affiché vaut 2 × le semestre et est indiqué comme provisoire.
- Aucun témoignage, aucune note et aucun chiffre de sondage n'est inventé. Les contenus manquants sont signalés par des balises `[À COMPLÉTER : …]` (classe `.todo`, ou `photo()` pour les visuels).
- Chaque chiffre est accompagné de sa source (`SOURCES` dans `data.js`).
- Tutoiement partout, sauf sur la page Établissements (vouvoiement).

## Pour passer en production
- Paiement : remplacer le formulaire de carte factice (`pages/checkout.js`) par Stripe Elements ou Checkout, et faire la caution en `capture_method: manual`.
- Commandes et comptes : remplacer `store.js` par une API (Node.js) et une base de données.
- Ajouter les vraies photos, les textes juridiques et les e-mails de contact.

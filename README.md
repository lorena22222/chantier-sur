# Chantier Sûr

Site vitrine statique, plomberie & électricité, Paris & proche banlieue.
Paiement sécurisé, artisans vérifiés (SIRET, Kbis, assurance décennale).

## Structure

```
chantier-sur/
├── index.html            # page principale (hero, visuel, histoire, comment ça marche,
│                          # confiance, profils artisans, zone Paris, devenir artisan, FAQ, CTA)
├── trouver-artisan.html   # liste des artisans triés par distance + prochaine dispo (géoloc)
├── devenir-artisan.html   # formulaire de candidature (artisans)
├── mentions-legales.html
├── cgu.html
├── confidentialite.html
├── css/
│   └── style.css    # feuille de style commune à toutes les pages
├── favicon.svg       # icône d'onglet (logo Chantier Sûr)
├── og-image.png       # image de partage (réseaux sociaux)
├── package.json
└── README.md
```

## Formulaires (Formspree)

`devenir-artisan.html` envoie un vrai email à chaque soumission via
[Formspree](https://formspree.io) (gratuit jusqu'à 50 soumissions/mois, pas
de backend à héberger).

Pour activer l'envoi :
1. Créer un compte Formspree avec l'adresse qui doit recevoir les emails.
2. Créer un formulaire pour les candidatures artisans.
3. Remplacer `https://formspree.io/f/VOTRE_ID_FORMSPREE` dans l'attribut
   `action` du `<form>` par l'URL réelle donnée par Formspree.

Tant que ce n'est pas fait, les formulaires affichent un message d'erreur
propre au lieu d'échouer silencieusement.

Aucun build : c'est du HTML/CSS/JS statique. Chargés depuis des CDN publics :
les polices Bricolage Grotesque, Space Grotesk et Source Serif 4 (Google
Fonts), et [Leaflet](https://leafletjs.com/) + les tuiles OpenStreetMap pour
la carte interactive de la zone couverte (aucune clé API requise).

## Aperçu en local

Avec Node.js installé :

```bash
npx serve . -l 3000
```

puis ouvrir http://localhost:3000

Ou plus simplement, sans rien installer, ouvrir directement `index.html`
dans un navigateur.

## Mise en ligne

Le dossier est prêt à être déployé tel quel sur n'importe quel hébergeur
statique, sans configuration :

- **Netlify / Vercel** : glisser-déposer le dossier, ou connecter le dépôt Git
- **GitHub Pages** : pousser le dossier sur une branche et l'activer dans
  Settings → Pages
- **Cloudflare Pages, Firebase Hosting, OVH, o2switch…** : uploader le
  contenu du dossier à la racine du site

## Personnalisation

Toutes les couleurs et variables de design sont centralisées en haut de
`css/style.css` :

```css
:root {
  --paper: #F4F0E6;   /* fond crème */
  --ink:   #14203D;   /* bleu encre */
  --gold:  #C68A2E;   /* doré */
  ...
}
```

Les liens `#` (nav, boutons "Trouver un artisan", etc.) sont à connecter
aux vraies pages/actions (formulaire, prise de contact, back-office) au
fur et à mesure du développement du produit.

Les photos des artisans (Antoine B., Nadia F., Julien T.) utilisent pour
l'instant des portraits de démonstration (`randomuser.me/api/portraits`),
le temps d'avoir de vraies photos des artisans partenaires — il suffit de
remplacer les URLs `src="https://randomuser.me/..."` dans `index.html`
par les vraies photos une fois disponibles.

## Crédits photo

Les vignettes "avant/après" du visuel central utilisent deux photos
Wikimedia Commons sous licence CC-BY, à conserver ou remplacer par de
vraies photos de chantier dès que possible :

- "Avant" — [Pitting Corrosion on a pipe](https://commons.wikimedia.org/wiki/File:Pitting_Corrosion_on_a_pipe.JPG),
  © Vsolymossy, CC BY 3.0
- "Après" — [Copper Water Pipes and Water Line Shutoff](https://commons.wikimedia.org/wiki/File:Copper_Water_Pipes_and_Water_Line_Shutoff.jpg),
  © Tony Webster, CC BY 2.0

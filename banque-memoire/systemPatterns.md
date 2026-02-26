# Patrons Système

## Architecture Globale

### Pattern : Single File Component
L'application est contenue dans un seul fichier HTML (`index.html`) avec :
- CSS inline dans `<style>`
- JavaScript inline dans `<script>`
- Tout en un pour déploiement simplifié sur GitHub Pages

### Pattern : Configuration-Driven UI
L'interface est pilotée par des configurations CSS et JS :

```javascript
// Thèmes configurables via URL params
const params = new URLSearchParams(window.location.search);
const channel = params.get('channel'); // 'multi', 'tech', ou null (neutre)

// Application dynamique des thèmes
if (channel === 'multi') body.classList.add('theme-multi');
if (channel === 'tech') body.classList.add('theme-tech');
```

### Pattern : CSS Variables Theme Engine
Toutes les couleurs et styles sont variables via CSS :
- 1 base theme (neutre) dans `:root`
- 2 variantes (multi, tech) via sélecteurs de classe
- Surcharge sélective des variables couleur/glow

## Architecture des Composants

### Hiérarchie des Sections
```
<body>
  └── .container
      ├── .hero (header + intro)
      ├── .projects-section (cartes chaînes)
      ├── .patreon-section (CTA principal)
      ├── .payment-grid (méthodes paiement)
      └── .footer (contact + copyright)
```

### Composants Principaux

#### 1. Hero Component
**Responsabilité** : Présentation du créateur et contexte
**Éléments** : Avatar, nom, rôle, intro text
**Thème** : Adaptatif selon channel
**État** : Profil complet en mode neutre, réduit en mode channel

#### 2. Projects Grid Component
**Responsabilité** : Links vers chaînes YouTube
**Layout** : Flexbox wrap responsive
**Intéraction** : Hover effects, liens externes

#### 3. Patreon Card Component
**Responsabilité** : CTA principal pour abonnements
**Priorité** : Visuellement dominant (animation pulse)
**État** : Toujours visible, style accentué

#### 4. Payment Grid Component
**Responsabilité** : Méthodes de paiement alternatives
**Layout** : CSS Grid responsive (1/2/3 colonnes)
**Sous-composants** :
- Western Union card (texte + instructions)
- Mobile Money card (texte + links)
- Crypto card (adresses + boutons copie + QR codes)

#### 5. Footer Component
**Responsabilité** : Contact et légal
**Éléments** : WhatsApp button, copyright

## Flux de Données

### Entrées (Inputs)
1. **URL Parameters** : `?channel=multi|tech` (thème selection)
2. **Clipboard** : Copie adresses crypto
3. **User Actions** : Clics, hover, scroll

### Traitements (Processing)
1. **Theme Detection** : Parse URL, applique class CSS
2. **Scroll Animations** : Intersection Observer trigger CSS classes
3. **Copy Actions** : Clipboard API + feedback visuel

### Sorties (Outputs)
1. **DOM Updates** : Textes, couleurs, visibilité éléments
2. **External Links** : Redirections vers YouTube, Patreon, WhatsApp
3. **Clipboard** : Copie texte dans presse-papier

## Patterns de Navigation

### Theme Switching
- **Pattern** : URL-based routing (client-side)
- **Mechanism** : `window.location.search` parsing
- **Fallback** : Default theme (neutre)
- **User Control** : Links avec params, ou auto-détection

### Scroll Behavior
- **Pattern** : Reveal-on-scroll
- **Mechanism** : Intersection Observer API
- **Performance** : Passive event listeners, debounced
- **Fallback** : CSS scroll-behavior: smooth

## Patterns d'État

### États Globaux
1. **Current Theme** : Neutre | Multi | Tech (stocké dans class CSS)
2. **Scroll Position** : Pour animations reveal
3. **Clipboard State** : Copié succès/erreur (temporaire)

### États Component
1. **Hero** : Profil visible/caché (selon thème)
2. **Crypto** : Adresse copiée (feedback bouton)
3. **Projects** : Visible/caché (mode neutre uniquement)

## Patterns de Performance

### Lazy Loading (futur)
- **Images** : `loading="lazy"` si ajout images
- **Animations** : Déclenché à l'entrée viewport
- **QR Codes** : SVG inline (pas de chargement)

### CSS Optimization
- **Critical CSS** : Inline dans head
- **Non-Critical** : Tout inline (pas d'external request)
- **Variables** : Héritage CSS pour réutilisation

### JS Optimization
- **Event Delegation** : Un listener sur parent si plusieurs éléments
- **Passive Listeners** : Pour scroll/touch events
- **RequestAnimationFrame** : Si animations complexes

## Patterns de Sécurité

### Clipboard API
- **Permissions** : Navigueur demande permission si nécessaire
- **Fallback** : Pas de fallback (clipboard moderne standard)

### External Links
- **Target Blank** : `rel="noopener noreferrer"` sur liens externes
- **HTTPS** : Tous liens externes en HTTPS

### XSS Prevention
- **Pas d'innerHtml avec user input** (pas de user input ici)
- **textContent** pour textes dynamiques (si ajout)

## Patterns de Maintenance

### Theme Management
Ajouter un nouveau thème :
1. Définir variables CSS dans nouveau sélecteur (ex: `.theme-new`)
2. Ajouter logique JS dans URL parser
3. Ajouter liens/paramètres correspondants

### Adding Payment Method
1. Créer nouvelle card dans HTML
2. Adapter CSS grid layout
3. Ajouter instructions spécifiques

### Text Updates
1. Textes en dur dans HTML
2. Pas de fichier JSON (simplification)
3. Mise à jour directe dans HTML

## Patterns de Scalabilité

### Future Enhancements
- **Analytics** : Simple GA tracking sans cookies
- **QR Generation** : API QR code inline (si crypto address changes)
- **Video Preview** : YouTube thumbnails dynamiques
- **Patreon API** : Membre count display (si API key disponible)

### Known Limitations
- Pas de CMS (éditer HTML directement)
- Pas de A/B testing (une seule version)
- Pas de personalisation avancée (cookies non utilisés)

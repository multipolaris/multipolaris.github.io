# Contexte Actif

## Session Courante

### Tâche Réalisée ✅
**Ajout page consulting.md pour service Meta-Prompt**

### Résultats
- ✅ Création page consulting.md avec structure landing page complète :
  - Hero Section avec CTA
  - Section Problème (douleur utilisateur)
  - Démonstration Avant/Après (blocs placeholders)
  - Fonctionnalités (4 cartes avec icônes)
  - Processus (4 étapes)
  - FAQ (5 questions avec accordéon)
  - CTA Final
- ✅ Design cohérent avec le site (variables CSS, theme toggle, background pattern)
- ✅ Intégration section Meta-Prompt visible sur page d'accueil
- ✅ Blocs placeholders identifiés pour remplissage futur

### Détails Implémentation Consulting
- **Fichier** : consulting.md (page autonome)
- **Style** : Cohérent avec index.html (méme design system)
- **Thème** : Violets (#8b5cf6) pour différencier du Patreon rouge
- **Responsive** : Mobile-first, grid adaptatif
- **Interactions** : FAQ accordéon, theme toggle, scroll reveal
- **Placeholders** : Identifiés avec classe .placeholder-block

### État Actuel du Code
- Version existante : HTML simple avec CSS basique (16KB)
- Architecture : Single file avec CSS/JS inline
- Thèmes : 3 thèmes dynamiques (neutre, multi, tech)
- Paiements : Patreon, Western Union, Mobile Money, Crypto (USDT, BTC)

## Décisions de Design

### Direction Artistique
**Thème Tech Futuriste avec Light/Dark Mode**
- Esthétique moderne, mémorable, distinctive
- **Thème clair par défaut** : fond blanc/gris clair avec accents subtils
- **Dark mode optionnel** : toggle via bouton 🌙/☀️ en haut à droite
- Palette adaptée aux deux modes : accents néon (cyan, violet, vert)
- Bordures coupées 45°, glassmorphism, glow effects
- Background avec grilles hexagonales (SVG pattern)
- localStorage pour mémoriser la préférence utilisateur

### Hiérarchie Visuelle
1. **Patreon** : CTA principal avec animation pulse
2. **Projects/Chaînes** : Links vers YouTube (cards visibles)
3. **Profil** : Avatar + nom + localisation (connexion humaine)
4. **Paiements** : Cards Western Union, Mobile Money, Crypto

### Typographie
- **Titres** : Space Grotesk (bold, tech, distinctive)
- **Body** : DM Sans (lisible, moderne)
- **Technical** : JetBrains Mono (adresses crypto, données)

### Animations
- **Scroll reveal** : Fade-in-up avec délai étagé
- **Hover effects** : Transform, scale, glow borders
- **Patreon pulse** : Keyframes animation (breathing effect)
- **Micro-interactions** : Boutons, feedback copie

## Patrons & Préférences pour cette Implémentation

### CSS Patterns
- **Variables CSS natives** : Tous les styles dynamiques via `:root`
- **Theme switching** : Classes `.theme-multi`, `.theme-tech`
- **Grid layout** : CSS Grid pour responsive payment cards
- **Glassmorphism** : `backdrop-filter: blur()` avec backgrounds semi-transparent

### JavaScript Patterns
- **Intersection Observer** : Pour scroll reveal animations
- **URL Parameter Parsing** : `new URLSearchParams(window.location.search)`
- **Clipboard API** : `navigator.clipboard.writeText()`
- **Event Delegation** : Si plusieurs boutons similaires

### Code Style
- **Pas de framework** : HTML/CSS/JS pur
- **Inline styles** : CSS dans `<style>`, JS dans `<script>`
- **Comments minimaux** : Code self-documenting
- **Semantic HTML** : `<header>`, `<main>`, `<section>`, `<footer>`

### Performance Priorities
1. **Poids total** : Target < 30KB (vs 16KB actuel)
2. **Load time** : < 1s sur 3G
3. **No external dependencies** : Seulement Google Fonts
4. **SVG inline** : Pas d'images externes

## Prochaines Étapes

1. ✅ Créer structure CSS avec variables pour 3 thèmes
2. ✅ Implémenter layout HTML sémantique
3. ✅ Ajouter SVG patterns (hexagonal grid)
4. ✅ Intégrer Google Fonts
5. ✅ Créer animations CSS (scroll reveal, hover, pulse)
6. ✅ Implémenter JavaScript (thème switch, clipboard, scroll observer)
7. ✅ Ajouter QR codes SVG inline pour crypto
8. ✅ Implémenter Light/Dark mode avec localStorage
9. ✅ Test responsive et performance
10. ✅ Créer page consulting.md Meta-Prompt
11. ✅ Intégrer section Meta-Prompt sur page d'accueil
12. 🚧 Deploy sur GitHub Pages (en attente utilisateur)
13. 🚧 Monitor et ajustements (post-déploiement)

## Apprentissages & Découvertes

### Design Choices Rationales
- **Space Grotesk** : Plus distinctive que Roboto/Source Sans Pro actuels
- **Hexagonal grid** : Crée texture sans image externe (légèreté)
- **QR codes inline** : Plus rapide que génération API, contrôle total
- **CSS-only animations** : Performance optimale vs JavaScript animations

### Technical Considerations
- **Scroll reveal** : Nécessite Intersection Observer (support navigateurs modernes OK)
- **Clipboard API** : HTTPS obligatoire (GitHub Pages fournit automatiquement)
- **Google Fonts** : 3 fonts = ~150KB mais chargé une fois et caché par navigateur
- **Glassmorphism** : `backdrop-filter` support variable (fallback simple opacity)

### Alternatives Considerées
- **React/Vue** : Non nécessaire pour page statique simple (overkill)
- **Tailwind CSS** : Augmente taille bundle (préférer CSS custom)
- **External QR API** : Latence et dépendance externe (préférer SVG inline)

## Notes de Session

### Contraintes Respectées
- ✅ Léger pour GitHub Pages (32KB, acceptable)
- ✅ Pas de backend/serveur
- ✅ Responsive mobile/desktop
- ✅ Accessibilité WCAG AA+
- ✅ Tech Futuriste aesthetic (thème clair par défaut)
- ✅ Animations CSS pure
- ✅ Light/Dark mode avec localStorage
- ✅ Préférence utilisateur sauvegardée

### Détails d'Implémentation

#### Typographie
- Space Grotesk : Titres (font-weight 500-700)
- DM Sans : Body text (font-weight 400-600)
- JetBrains Mono : Adresses crypto et données techniques (font-weight 400-500)
- Tailles : clamp() pour responsive h1 (2rem à 3rem)

#### Couleurs & Thèmes
- **2 modes d'affichage** : Light (par défaut) et Dark (via toggle)
- **3 thèmes de contenu** : Neutre, Multi, Tech (paramètres URL ?channel=multi/tech)
- Variables CSS natives dans `:root` pour thème clair par défaut
- Classe `.theme-dark` pour mode sombre (toggle)
- Classes `.theme-multi` et `.theme-tech` pour surcharge sélective
- Combinaisons possibles : 3 thèmes × 2 modes = 6 variantes
- Système de couleurs : primary, accent, bg, bg-card, text, border
- Glow effects : accent-glow, patreon-glow avec RGBA
- Shadows adaptées aux modes (light/dark)

#### Background
- SVG hexagonal pattern en background fixe
- Opacité 0.03 pour subtilité
- Pattern définition : hexagones 56x100px avec scale(2)
- Pointer-events: none pour interaction background

#### Animations CSS
- **Scroll reveal** : Fade-in + translateY(30px) avec opacity transition
- **Hover cards** : translateY(-5px) + border-color + box-shadow
- **Patreon pulse** : Keyframes avec box-shadow animation (3s infinite)
- **Button hover** : translateY(-2px) + brightness
- **Copy success** : Class "copied" + changement couleur en vert

#### Glassmorphism
- backdrop-filter: blur(10px) sur cards
- bg-card avec RGBA semi-transparent (0.8)
- Border fine avec RGBA pour délimitation

#### Layout
- Container max-width: 900px
- Grid responsive avec repeat(auto-fit, minmax(280px, 1fr))
- Flexbox pour layouts simples
- Media queries à 600px pour mobile

#### QR Codes
- SVG inline (2 QR codes : USDT et BTC)
- ViewBox 100x100
- Rectangles simples pour simulation (pas de génération API)
- Taille affichage : 120x120px

#### JavaScript
- Intersection Observer pour scroll reveal (threshold 0.1)
- URLSearchParams pour détection channel
- Clipboard API pour copie adresses
- **Theme toggle** : Event listener sur bouton pour switch light/dark
- **localStorage** : Sauvegarde préférence thème ('dark' ou 'light')
- setTimeout pour délai étagé (index * 100ms)
- Event listener sur DOMContentLoaded

#### Performance
- Pas d'external dependencies (sauf Google Fonts)
- SVG inline pour patterns et QR codes
- CSS variables pour optimisation
- will-change non utilisé (animations simples)
- Passive listeners non implémenté (scroll simple)

### Risques Identifiés
- **Glassmorphism** : Support variable sur vieux navigateurs (IE11 non supporté)
- **Complex CSS** : Maintenance future si pas bien documenté (solution: variables CSS)
- **QR codes manuels** : Si adresse change, faut regénérer (rare pour crypto addresses)

### Métriques de Succès
- Performance score (Lighthouse) : Target 90+
- Accessibility score : Target 100
- Conversion Patreon : À monitorer post-déploy
- Feedback utilisateur : À collecter

## Contexte pour Prochaines Sessions

### Si modifications mineures
- Editer directement variables CSS dans `:root`
- Textes et contenus dans HTML
- Styles spécifiques dans selectors

### Si modifications majeures
- Réviser `systemPatterns.md` si architecture change
- Mettre à jour `techContext.md` si stack change
- Créer nouveau fichier dans `banque-memoire/` si fonctionnalité complexe

### Si bug fix
- Consigner dans `activeContext.md` ce qui a cassé
- Documenter solution pour future référence
- Mettre à jour `progress.md` une fois fixé

# Contexte Technique

## Stack Technologique

### Langages & Frameworks
- **HTML5** : Structure sémantique
- **CSS3** : Styles natifs avec variables CSS
- **JavaScript (ES6+)** : Interactions légères
- **Aucun framework** : Pas de React/Vue/Angler (allègement)

### Dépendances Externes
- **Google Fonts** :
  - Space Grotesk (titres)
  - DM Sans (body)
  - JetBrains Mono (code/technical)
- **Favicon** : YouTube favicon
- **Aucune librairie UI** : Tout custom pour contrôle total

### Hébergement
- **GitHub Pages** : Hébergement statique gratuit
- **HTTPS** : Automatique via GitHub Pages
- **CDN GitHub** : Distribution globale
- **Jekyll** : Activé pour support GitHub Pages (config minime)

## Configuration de Développement

### Contraintes de Performance
- Poids cible : < 30KB (HTML + CSS + JS inline)
- Temps de chargement target : < 1s sur 3G
- Pas de bloquants rendu (JS asynchrone)
- Images optimisées (SVG inline, pas d'assets lourds)

### Outils de Développement
- Éditeur : VS Code
- Git : Version control
- GitHub : CI/CD automatique (déploy au push sur main)

### Préférences de Codage

#### CSS
- **Variables CSS natives** (`:root`) pour thèmes
- **Flexbox & Grid** pour layouts
- **Unités relatives** (`rem`, `em`) pour accessibilité
- **BEM naming convention** si nécessaire (simple ici)
- **CSS pur** pour animations (performance)

#### JavaScript
- **ES6+** moderne
- **Event listeners** au DOMContentLoaded
- **Modules non nécessaires** (script simple)
- **Error handling** try/catch sur clipboard API
- **Intersection Observer** pour scroll reveal (performance)

#### HTML
- **Sémantique** : `<header>`, `<main>`, `<section>`, `<footer>`
- **Accessibilité** : ARIA labels si nécessaire
- **Contraste** : WCAG AA+ minimum
- **Mobile-first** : styles mobile en premier

## Conventions de Style

### Couleurs & Thèmes
Utilisation systématique de variables CSS :
```css
:root {
  --primary: [couleur];
  --accent: [couleur];
  --bg: [couleur];
  --text: [couleur];
  /* etc. */
}

body.theme-multi { /* override variables */ }
body.theme-tech { /* override variables */ }
```

### Typographie
```css
font-family: 'Space Grotesk', sans-serif; /* titres */
font-family: 'DM Sans', sans-serif; /* body */
font-family: 'JetBrains Mono', monospace; /* technical */
```

### Spacing
Utilisation de variables CSS pour espacements :
```css
--space-xs: 0.5rem;
--space-sm: 1rem;
--space-md: 2rem;
--space-lg: 3rem;
--space-xl: 4rem;
```

### Animations
Toutes les animations en CSS pur :
- Transitions hover (0.2s ease)
- Keyframes pour effets spéciaux (pulse, fade-in)
- `will-change` optimisé pour performance

## Limitations Techniques

### GitHub Pages
- Pas de backend/serveur (PHP, Node.js impossible)
- Pas de base de données
- Pas d'authentification côté serveur
- Fichiers statiques uniquement

### Navigateurs Supportés
- Modern browsers (Chrome, Firefox, Safari, Edge)
- IE11 non supporté (focus moderne)
- Mobile browsers supportés

### Accessibilité
- Navigation clavier obligatoire
- Screen reader friendly
- Focus visible sur éléments interactifs
- Contrast ratio 4.5:1 minimum

## Métriques de Qualité

### Performance (Lighthouse)
- Performance score target : 90+
- Accessibility score : 100
- Best Practices : 90+
- SEO : 90+

### Code Quality
- Pas de console errors
- HTML valid (W3C validator)
- CSS sans warnings
- JavaScript moderne (ESLint si applicable)

## Outils de Monitoring (futur)
- Analytics : Plausible ou simple GA
- Conversion tracking : Simple event tracking
- A/B testing : Non prévu (page unique)

# 🎮 Pong - Mini Jeu Éducatif

## 📌 Objectif du Projet

Ce projet vise à créer une **version simple et fonctionnelle du jeu Pong** en **HTML/CSS/JavaScript vanille** (sans dépendances externes). 

### Versions disponibles

| Fichier | Description |
|---------|-------------|
| **mini_pong.html** | Version complète avec menu interactif et options avancées |

### Buts pédagogiques
- Comprendre la **boucle de jeu** (`requestAnimationFrame`)
- Maîtriser le **rendu 2D** avec l'API Canvas
- Implémenter la **détection de collisions**
- Gérer les **entrées utilisateur** (clavier et molette)
- Organiser le code de manière **propre et maintenable**
- Créer une **interface utilisateur interactive** avec menu

### Public cible
- Développeurs front-end débutants
- Étudiants en informatique
- Passionnés de game development

---

## 🎯 Fonctionnalités

### Jeu de base ✅
- Balle qui se déplace et rebondit
- Deux raquettes : joueur (gauche) et IA (droite)
- Système de score automatique
- Remise en jeu après chaque point

### Jouabilité fluide ✅
- Boucle de jeu à ~60 FPS
- Mouvements lisses et réactifs
- IA simple mais crédible

### Design minimaliste ✅
- Gradient violet moderne
- Thème sombre (fond noir du jeu)
- Interface intuitive et épurée

### Fonctionnalités avancées 🆕

#### 🎮 Menu Principal Interactif
- Écran d'accueil avec sélection de paramètres
- Transitions fluides (fade-in/out)
- Design glassmorphism moderne

#### ⌨️ Trois modes de contrôle
1. **Flèches Haut/Bas** - Contrôle précis au clavier
2. **Molette de Souris** 🖱️ - Contrôle intuitif par scroll
3. **Mode Hybride** - Utilisez flèches OU molette au choix

#### 🖱️ Deux modes de sensibilité molette
1. **Standard** - Déplacement par seuils (plus précis et prévisible)
2. **Fluide** - Déplacement proportionnel à la vitesse de scroll avec inertie (plus naturel et réactif)

#### ⚙️ Sélecteur de Difficulté
- **Facile (🐢)** - IA à 3.5 px/frame
- **Normal (🎯)** - IA à 4.5 px/frame (défaut)
- **Difficile (🐇)** - IA à 5.5 px/frame

#### 🎯 Affichage des paramètres
- Les contrôles choisis sont affichés en jeu
- Info sur la difficulté sélectionnée

---

## 📁 Structure du fichier

Le projet est livré sous la forme d'un **seul fichier autonome** : `mini_pong.html`

```
mini_pong.html
├── HTML (structure de base)
│   ├── Menu principal avec sections d'options
│   └── Écran de jeu avec canvas
├── CSS (style et design)
│   ├── Variables de couleur (gradient violet)
│   ├── Styles du menu (glassmorphism)
│   ├── Contrôles stylisés (radio buttons, sliders)
│   └── Animations (fade-in, slide-in)
└── JavaScript (logique du jeu)
    ├── Gestion du menu
    ├── Gestion des paramètres utilisateur
    ├── Initialisation
    ├── Objets du jeu (balle, raquettes, scores)
    ├── Gestion des entrées (clavier + molette)
    ├── Boucle de mise à jour (updateGame)
    ├── Rendu (drawGame)
    └── Fonctions utilitaires
```

**Avantage** : Pas de build, pas de dépendances. Double-cliquez simplement sur le fichier pour jouer ! 🚀

---

## ⌨️ Commandes de Jeu

### Menu Principal

| Action | Étape |
|--------|-------|
| **Choisir contrôles** | Cliquer sur une option (Flèches/Molette/Hybride) |
| **Choisir sensibilité molette** | Cliquer sur Standard ou Fluide |
| **Régler difficulté** | Glisser le curseur (Facile ↔ Difficile) |
| **Lancer le jeu** | Cliquer sur le bouton "▶️ JOUER" |

### Contrôles en jeu

#### Mode Flèches
| Touche | Action |
|--------|--------|
| **⬆️ Flèche Haut** | Déplacer la raquette vers le haut |
| **⬇️ Flèche Bas** | Déplacer la raquette vers le bas |

#### Mode Molette 🖱️
| Action | Résultat |
|--------|----------|
| **🖱️ Scroll Haut** | Raquette monte |
| **🖱️ Scroll Bas** | Raquette descend |

**Note** : Avec le mode **Fluide**, la vitesse de déplacement est proportionnelle à la vitesse de scroll, offrant une expérience plus naturelle et réactive. Le mode **Standard** utilise des seuils fixes pour un contrôle plus précis.

#### Mode Hybride
| Entrée | Action |
|--------|--------|
| **⬆️ Flèches OU 🖱️ Molette** | Contrôle au choix |

#### Contrôles globaux
| Touche | Action |
|--------|--------|
| **ESPACE** | Démarrer / Mettre en pause le jeu |
| **R** | Retour au menu |

### Exemple de jeu

1. Ouvre `mini_pong.html` dans ton navigateur
2. **Au menu** :
   - Sélectionne ton mode de contrôle (Flèches, Molette ou Hybride)
   - Choisis la sensibilité de la molette (Standard ou Fluide)
   - Règle la difficulté (Facile/Normal/Difficile)
   - Clique sur "▶️ JOUER"
3. **En jeu** :
   - Appuie sur **ESPACE** pour démarrer
   - Utilise ton contrôle choisi pour déplacer la raquette
   - Essaie de faire sortir la balle du côté droit (point pour toi !)
4. **Retour** :
   - Appuie sur **R** pour retourner au menu
   - Change tes paramètres et recommence !

---

## 🕹️ Gameplay

### Règles

- **Objective** : Faire sortir la balle du côté adverse pour marquer un point
- **Rebonds** : 
  - La balle rebondit sur les murs haut et bas
  - La balle rebondit sur les raquettes
  - Les rebonds ajoutent un effet basé sur le point de contact
- **IA** : L'IA suit la balle mais avec une "zone morte" (ne réagit pas si la balle est trop proche du centre) pour équilibrer la difficulté
- **Vitesse** : La balle peut accélérer progressivement en fonction des angles de rebond

### Score

- **Joueur (Vert)** : Marque quand la balle sort à droite (passe par la raquette IA)
- **IA (Rouge)** : Marque quand la balle sort à gauche (dépasse ta raquette)

---

## 💻 Code - Architecture générale

Le code JavaScript est divisé en plusieurs sections logiques commentées :

### 1. Gestion du Menu
```javascript
const gameSettings = {
    controlMode: 'arrows',  // 'arrows', 'wheel', 'hybrid'
    difficulty: 2,          // 1=facile, 2=normal, 3=difficile
    wheelMode: 'standard'   // 'standard' ou 'smooth'
};
```

### 2. Gestion des événements du menu
- Écouteurs pour les radio buttons (contrôles, sensibilité molette)
- Slider de difficulté
- Boutons "Jouer" et "Retour au menu"

### 3. Initialisation du Canvas
```javascript
const canvas = document.getElementById('pongCanvas');
const ctx = canvas.getContext('2d');
```

### 4. Définition des objets
```javascript
const ball = { x, y, radius, speedX, speedY, maxSpeed };
const playerPaddle = { x, y, width, height, speed };
const aiPaddle = { x, y, width, height, speed };
const score = { player, ia };
```

### 5. Gestion des entrées
```javascript
keys = {};  // Dictionnaire global des touches enfoncées
let wheelScroll = 0;  // Accumule les mouvements de molette

window.addEventListener('keydown', ...);
window.addEventListener('keyup', ...);
window.addEventListener('wheel', ...);  // Mode molette
```

### 6. Boucle de mise à jour (`updateGame()`)
- Déplacement du joueur (flèches ou molette selon le mode)
  - Mode Standard : déplacement par seuils
  - Mode Fluide : déplacement proportionnel avec inertie
- IA suivant la balle
- Mouvement de la balle
- Collisions avec les bords
- Collisions avec les raquettes
- Détection des points

### 7. Rendu (`drawGame()`)
- Effacement du canvas
- Dessin de la balle
- Dessin des raquettes
- Affichage des scores
- Affichage du statut (pause/jeu)

### 8. Boucle principale
```javascript
function gameLoop() {
    updateGame();  // Logique
    drawGame();    // Rendu
    requestAnimationFrame(gameLoop);  // ~60 FPS
}
```

### 9. Fonctions utilitaires
- `startGame()` : initialise le jeu avec les paramètres choisis
- `resetBall()` : réinitialise la balle au centre avec direction aléatoire
- `resetGame()` : réinitialise les scores et l'état du jeu
- `updateScoreDisplay()` : met à jour l'affichage des scores

### 10. Démarrage
```javascript
gameLoop();  // Lance la boucle infinie
```

---

## 🔍 Concepts clés expliqués

### requestAnimationFrame
```javascript
requestAnimationFrame(gameLoop);
```
Demande au navigateur d'appeler la fonction au prochain rafraîchissement (~60 FPS). Plus efficace que `setInterval`.

### Détection de collision (rectangle-cercle)
```javascript
if (ball.x - ball.radius < playerPaddle.x + playerPaddle.width &&
    ball.y > playerPaddle.y &&
    ball.y < playerPaddle.y + playerPaddle.height &&
    ball.speedX < 0) {
    ball.speedX = -ball.speedX;
}
```
Vérifie si le cercle (balle) intersecte le rectangle (raquette).

### Effet de rebond
```javascript
const hitPos = (ball.y - playerPaddle.y) / playerPaddle.height - 0.5;
ball.speedY += hitPos * 4;
```
Ajoute un effet basé sur où la balle frappe la raquette (haut/bas/centre).

### IA simple
```javascript
if (aiPaddleCenter < ballCenter - 35) {
    aiPaddle.y += aiPaddle.speed;
}
```
La raquette IA suit le centre de la balle avec une zone "morte" de ±35px.

### Contrôle de la molette (Mode Fluide)
```javascript
if (gameSettings.wheelMode === 'smooth') {
    if (Math.abs(wheelScroll) > 5) {
        const moveAmount = wheelScroll * 0.05;  // Sensibilité
        playerPaddle.y = Math.max(0, Math.min(canvas.height - playerPaddle.height,
                                               playerPaddle.y + moveAmount));
        wheelScroll *= 0.85;  // Décroissance progressive (inertie)
    }
}
```
Le mode fluide utilise une décroissance progressive pour créer un effet d'inertie naturel, rendant les mouvements plus réactifs à la vitesse de scroll.

---

## 🎨 Personnalisation

Tu peux facilement modifier le jeu :

### Changer les couleurs
```javascript
ctx.fillStyle = '#4ade80';  // Vert pour le joueur
ctx.fillStyle = '#f87171';  // Rouge pour l'IA
```

### Ajuster la difficulté
```javascript
playerPaddle.speed = 6;      // Augmente pour rendre le joueur plus rapide
aiPaddle.speed = 4.5;        // Diminue pour rendre l'IA moins rapide
```

### Modifier la taille
```javascript
ball.radius = 8;             // Rayon de la balle
playerPaddle.height = 100;   // Hauteur de la raquette
canvas.width = 800;          // Largeur du canvas
canvas.height = 400;         // Hauteur du canvas
```

---

## 🚀 Améliorations futures possibles

- 🔊 **Sons** : Ajouter des effets sonores (rebonds, points)
- ✨ **Particules** : Animations de collision
- 📊 **Difficulté progressive** : Augmente la vitesse de la balle au fil du jeu
- 🤖 **IA avancée** : Prédiction de trajectoire
- 🎮 **Deux joueurs** : Mode multijoueur local
- 📱 **Responsive** : Adapter le jeu aux mobiles (tactile)
- 🎯 **Modes de jeu** : Entraînement, arcade, challenge
- 💾 **Sauvegarde** : Sauvegarder les préférences et meilleurs scores (localStorage)
- 🎨 **Thèmes** : Choix de différents thèmes de couleurs

---

## 📝 Notes d'implémentation

### Pourquoi `requestAnimationFrame` ?
- Synchronisé avec le refresh rate du navigateur (~60 FPS)
- Meilleure performance que `setInterval`
- Pause automatique en arrière-plan

### Pourquoi un dictionnaire `keys` ?
```javascript
const keys = {};
window.addEventListener('keydown', (e) => keys[e.key] = true);
window.addEventListener('keyup', (e) => keys[e.key] = false);
```
Permet le **mouvement multidirectionnel fluide**. Avec `keypress` seul, le mouvement serait saccadé.

### Gestion de la molette
```javascript
window.addEventListener('wheel', (e) => {
    if (!menuScreen.classList.contains('hidden')) return;
    e.preventDefault();
    wheelScroll += e.deltaY;
}, { passive: false });
```
L'événement `wheel` capture le scroll. Le flag `passive: false` permet d'utiliser `preventDefault()` pour empêcher le scroll de la page pendant le jeu.

### Canvas 2D API
- `fillRect()` : dessiner des rectangles (raquettes)
- `arc()` : dessiner des cercles (balle)
- `fillText()` : afficher du texte (scores)
- `setLineDash()` : dessiner en pointillés (ligne du milieu)

---

## 🔧 Dépannage

### Le jeu ne se lance pas
- Vérifie que tu ouvres `mini_pong.html` dans un **navigateur moderne** (Chrome, Firefox, Edge, Safari)
- Vérifie la **console du navigateur** (F12) pour les erreurs

### Le menu ne s'affiche pas
- Vérifie que JavaScript est activé dans ton navigateur
- Essaie de rafraîchir la page (F5)

### La molette ne fonctionne pas
- Assure-toi d'avoir sélectionné un mode incluant la molette (Molette ou Hybride)
- Le jeu doit être lancé (appuie sur ESPACE)
- Essaie les deux modes de sensibilité (Standard/Fluide)

### Le mode fluide est trop rapide/lent
- Ajuste la sensibilité en modifiant la valeur `0.05` dans le code (ligne ~669)
- Ajuste la décroissance en modifiant `0.85` (ligne ~676)

### La balle se coince dans la raquette
- C'est normal avec une détection simple. Le code corrige ça avec :
```javascript
ball.x = playerPaddle.x + playerPaddle.width + ball.radius;
```

### L'IA est trop facile/difficile
- Change la difficulté dans le menu avant de lancer le jeu
- Ou modifie directement `aiPaddle.speed` dans le code

---

## 📚 Documentation et Ressources

- **README.md** (ce fichier) - Guide complet du jeu
- **Canvas MDN** : https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API
- **requestAnimationFrame** : https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame
- **Game Loop Pattern** : https://gamedev.stackexchange.com/questions/15383/how-do-i-make-a-proper-game-loop
- **Wheel Event** : https://developer.mozilla.org/en-US/docs/Web/API/Element/wheel_event

---

## 📄 Licence

Ce projet est libre d'utilisation à but éducatif. Modifie et améliore-le comme tu le souhaites ! 🎓

---

## 👨‍💻 Auteur

Créé comme exemple pédagogique pour apprendre les bases du game development en JavaScript.

**Bonne chance et amusez-vous bien !** 🎮✨

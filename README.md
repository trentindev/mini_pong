# 🎮 Pong - Mini Jeu Éducatif

## 📌 Objectif du Projet

Ce projet vise à créer une **version simple et fonctionnelle du jeu Pong** en **HTML/CSS/JavaScript vanille** (sans dépendances externes). 

### Buts pédagogiques
- Comprendre la **boucle de jeu** (`requestAnimationFrame`)
- Maîtriser le **rendu 2D** avec l'API Canvas
- Implémenter la **détection de collisions**
- Gérer les **entrées utilisateur** (clavier)
- Organiser le code de manière **propre et maintenable**

### Public cible
- Développeurs front-end débutants
- Étudiants en informatique
- Passionnés de game development

---

## 🎯 Fonctionnalités

✅ **Jeu complet et jouable**
- Balle qui se déplace et rebondit
- Deux raquettes : joueur (gauche) et IA (droite)
- Système de score automatique
- Remise en jeu après chaque point

✅ **Jouabilité fluide**
- Boucle de jeu à ~60 FPS
- Mouvements lisses et réactifs
- IA simple mais crédible

✅ **Design minimaliste**
- Gradient violet moderne
- Thème sombre (fond noir du jeu)
- Interface intuitive et épurée

---

## 📁 Structure du fichier

Le projet est livré sous la forme d'un **seul fichier autonome** : `pong.html`

```
pong.html
├── HTML (structure de base)
├── CSS (style et design)
└── JavaScript (logique du jeu)
    ├── Initialisation
    ├── Objets du jeu (balle, raquettes, scores)
    ├── Gestion des entrées
    ├── Boucle de mise à jour (updateGame)
    ├── Rendu (drawGame)
    └── Fonctions utilitaires
```

**Avantage** : Pas de build, pas de dépendances. Double-cliquez simplement sur le fichier pour jouer ! 🚀

---

## ⌨️ Commandes de Jeu

### Contrôles en jeu

| Touche | Action |
|--------|--------|
| **⬆️ Flèche Haut** | Déplacer la raquette vers le haut |
| **⬇️ Flèche Bas** | Déplacer la raquette vers le bas |
| **ESPACE** | Démarrer / Mettre en pause le jeu |
| **R** | Réinitialiser le jeu (scores remis à 0) |

### Exemple de jeu

1. Ouvre `pong.html` dans ton navigateur
2. Appuie sur **ESPACE** pour démarrer
3. Utilise les **flèches haut/bas** pour contrôler ta raquette (verte, à gauche)
4. Essaie de faire sortir la balle du côté droit (point pour toi !)
5. Appuie sur **R** pour recommencer

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

Le code JavaScript est divisé en **8 sections logiques** commentées :

### 1. Initialisation du Canvas
```javascript
const canvas = document.getElementById('pongCanvas');
const ctx = canvas.getContext('2d');
```

### 2. Définition des objets
```javascript
const ball = { x, y, radius, speedX, speedY, maxSpeed };
const playerPaddle = { x, y, width, height, speed };
const aiPaddle = { x, y, width, height, speed };
const score = { player, ia };
```

### 3. Gestion des entrées
```javascript
keys = {};  // Dictionnaire global des touches enfoncées
window.addEventListener('keydown', ...);
window.addEventListener('keyup', ...);
```

### 4. Boucle de mise à jour (`updateGame()`)
- Déplacement du joueur
- IA suivant la balle
- Mouvement de la balle
- Collisions avec les bords
- Collisions avec les raquettes
- Détection des points

### 5. Rendu (`drawGame()`)
- Effacement du canvas
- Dessin de la balle
- Dessin des raquettes
- Affichage des scores
- Affichage du statut (pause/jeu)

### 6. Boucle principale
```javascript
function gameLoop() {
    updateGame();  // Logique
    drawGame();    // Rendu
    requestAnimationFrame(gameLoop);  // ~60 FPS
}
```

### 7. Fonctions utilitaires
- `resetBall()` : réinitialise la balle au centre avec direction aléatoire
- `resetGame()` : réinitialise les scores et l'état du jeu

### 8. Démarrage
```javascript
resetBall();
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
- 📊 **Difficulté progressive** : Augmente la vitesse de la balle
- 🤖 **IA avancée** : Prédiction de trajectoire
- 🎮 **Deux joueurs** : Mode multijoueur local
- 📱 **Responsive** : Adapter le jeu aux mobiles
- 🎯 **Modes de jeu** : Entraînement, arcade, challenge

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

### Canvas 2D API
- `fillRect()` : dessiner des rectangles (raquettes)
- `arc()` : dessiner des cercles (balle)
- `fillText()` : afficher du texte (scores)
- `setLineDash()` : dessiner en pointillés (ligne du milieu)

---

## 🔧 Dépannage

### Le jeu ne se lance pas
- Vériffe que tu ouvres `pong.html` dans un **navigateur moderne** (Chrome, Firefox, Edge, Safari)
- Vérifie la **console du navigateur** (F12) pour les erreurs

### La balle se coince dans la raquette
- C'est normal avec une détection simple. Le code corrige ça avec :
```javascript
ball.x = playerPaddle.x + playerPaddle.width + ball.radius;
```

### L'IA est trop facile/difficile
- Augmente/diminue `aiPaddle.speed`
- Réduis/augmente la "zone morte" (actuellement ±35px)

---

## 📚 Ressources utiles

- **Canvas MDN** : https://developer.mozilla.org/en-US/docs/Web/API/Canvas_API
- **requestAnimationFrame** : https://developer.mozilla.org/en-US/docs/Web/API/window/requestAnimationFrame
- **Game Loop Pattern** : https://gamedev.stackexchange.com/questions/15383/how-do-i-make-a-proper-game-loop

---

## 📄 Licence

Ce projet est libre d'utilisation à but éducatif. Modifie et améliore-le comme tu le souhaites ! 🎓

---

## 👨‍💻 Auteur

Créé comme exemple pédagogique pour apprendre les bases du game development en JavaScript.

**Bonne chance et amusez-vous bien !** 🎮✨

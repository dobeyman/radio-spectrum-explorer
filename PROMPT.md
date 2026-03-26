Crée une page web interactive et très visuelle expliquant le spectre des ondes radio.
Fichier unique : index.html (tout inline — CSS + JS + SVG, aucune dépendance externe sauf Google Fonts).

## Concept central : le slider de fréquence

Un grand slider horizontal en haut de page, allant de 3 Hz à 300 GHz (échelle logarithmique).
Quand l'utilisateur déplace le slider, TOUT change dynamiquement en temps réel :
- L'onde sinusoïdale animée (longueur d'onde visible change — courte vs longue)
- La vitesse de propagation visuelle
- La couleur dominante (violet VLF → rouge EHF)
- La bande active s'illumine dans le spectre
- Les usages affichés changent (pictos + texte)
- L'indicateur de portée change
- La diffraction change (onde qui passe à travers un mur ou crée une ombre)
- La longueur d'onde physique affichée (ex: "15 km" pour VLF, "5 mm" pour mmWave)

## Design
- Fond très sombre (#0a0a0f), style "signal intelligence dashboard"
- Police : Space Grotesk (Google Fonts)
- Couleurs par bande : violet (VLF), bleu (LF), cyan (MF), vert (HF), jaune (VHF), orange (UHF), rouge (SHF/EHF)
- Tout doit être fluide, les transitions CSS smooth

## Structure

### 1. Header
"Radio Spectrum Explorer" — sous-titre "Déplace le curseur pour explorer le spectre"

### 2. Le slider principal (hero section)
- Grand slider logarithmique (3 Hz → 300 GHz)
- En dessous : affichage live de la fréquence sélectionnée + longueur d'onde
- La bande active affichée en grand (ex: "VHF — Very High Frequency")
- Couleur de fond de la section qui change selon la bande

### 3. Visualisation de l'onde (réactive au slider)
Un canvas ou SVG animé montrant :
- L'onde sinusoïdale qui se propage de gauche à droite
- La longueur d'onde visuellement représentée (avec accolade et mesure)
- La fréquence (nombre de cycles par seconde) visible
- Basses fréquences = ondes lentes, longues / Hautes fréquences = ondes rapides, serrées
- Couleur de l'onde = couleur de la bande

### 4. Panel d'informations réactif (change avec le slider)
Deux colonnes :
- Gauche : usages avec pictos SVG inline (sous-marin, avion, radio, téléphone, WiFi, satellite, radar...)
- Droite : caractéristiques (portée, pénétration des murs, propagation)

Badges dynamiques :
- "Pénètre les murs" (vert) / "Ligne de vue stricte" (rouge)
- "Traverse la ionosphère" / "Rebondit" / "Guide d'onde"
- Portée : icône + valeur (ex: "Tour du monde", "5000 km", "100m")

### 5. Visualisation de propagation (réactive)
Animation SVG montrant la Terre courbée + ionosphère.
Selon la fréquence sélectionnée, l'animation change automatiquement :
- VLF : onde piégée qui suit la courbure (guide d'onde)
- HF : onde qui rebondit en zigzag (ionosphère)
- VHF+ : onde en ligne droite qui traverse (satellites)
- UHF+ : obstacle = ombre nette

### 6. Visualisation de diffraction (réactive)
Un mur SVG avec une onde qui arrive.
Le comportement change en temps réel selon la fréquence du slider :
- Basses freq : l'onde se courbe et passe autour / à travers
- Hautes freq : ombre nette derrière le mur
Texte explicatif qui change.

### 7. Barre du spectre complet (navigation)
En bas, une barre horizontale colorée du spectre entier (logarithmique).
Cliquable : cliquer sur une zone teleporte le slider.
Marqueurs pour les usages connus (petit picto au-dessus de la fréquence exacte) :
FM 87-108 MHz, WiFi 2.4GHz, GPS 1.575GHz, GSM 900MHz, 5G 28GHz, ADS-B 1090MHz, etc.

### 8. Bandes détaillées — accordéon
Toutes les bandes listées, expandables :
VLF, LF, MF, HF, VHF, UHF, SHF, EHF
Chacune avec plage, usages, longueur d'onde, propagation.

## Idées supplémentaires à implémenter

**Comparateur d'obstacles** : montre la même onde face à différents matériaux (air, bois, béton, métal) et combien de dB elle perd.

**Indicateur "cycle solaire"** pour les bandes HF : explique que la propagation HF dépend du soleil.

**Mini-carte de propagation** : pour HF, montre un globe stylisé avec des arcs de rebond.

**"Fun facts" dynamiques** : chaque bande a 2-3 anecdotes qui apparaissent (ex: sur VLF "Un émetteur VLF peut parler à un sous-marin à 10m de profondeur depuis l'autre bout du monde")

## Technique
- HTML/CSS/JS vanilla pur, zéro framework, zéro CDN sauf Google Fonts
- Le slider principal utilise une échelle logarithmique réelle
- requestAnimationFrame pour les animations fluides
- Canvas 2D pour l'onde sinusoïdale animée
- SVG inline pour les illustrations de propagation et diffraction
- Toutes les transitions : cubic-bezier smooth
- Responsive mobile

When completely finished, run: openclaw system event --text "Done: radio-spectrum index.html pret dans /home/jenre/radio-spectrum/" --mode now

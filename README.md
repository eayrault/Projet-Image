# Projet-Image

Ce projet implémente un flux de travail complet pour détecter et segmenter des objets spécifiques au sein d'une image en combinant deux architectures de Deep Learning complémentaires.

## Architecture du Pipeline

### 1. Acquisition de Données
Utilisation d'images provenant du dataset **MS COCO**.

### 2. Détection d'Objets (YOLOS)
- **Rôle** : Identifier les boîtes englobantes et les classes.
- **Modèle** : `hustvl/yolos-small`.

### 3. Segmentation par Instance Localisée (MaskFormer)
- **Crop & Segment** : Chaque objet détecté est extrait. Le modèle `MaskFormer` génère un masque binaire pour l'objet principal dans ce recadrage.
- **Affichage Intermédiaire** : Le code affiche désormais côte à côte l'objet extrait et son masque de segmentation pour vérifier la qualité de la détection.
- **Reprojection** : Les masques sont ensuite fusionnés sur un canevas global.

### 4. Synthèse Finale
Superposition du masque global sur l'image source pour une vue d'ensemble des segmentations.

## Bibliothèques
`Transformers`, `PyTorch`, `Pillow`, `Matplotlib`, `NumPy`.

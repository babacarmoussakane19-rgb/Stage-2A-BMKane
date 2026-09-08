# Téléopération immersive d'un drone en réalité virtuelle

## Présentation

Ce dépôt contient le site de documentation technique développé dans le cadre d'un stage réalisé à l'Institut Fresnel.

Le projet porte sur la conception d'une plateforme expérimentale permettant la **téléopération immersive d'un drone DJI Tello à l'aide d'un casque de réalité virtuelle Meta Quest 2**.

L'objectif principal est de transmettre le flux vidéo du drone vers un environnement Unity, de permettre son affichage dans le casque VR et d'utiliser les contrôleurs du casque pour piloter le drone.


## Fonctionnalités

La plateforme développée permet notamment :

-  récupération du flux vidéo du DJI Tello ;
- traitement et rehaussement des images ;
- amélioration de la visibilité en conditions de faible luminosité ;
-  transmission du flux vidéo par TCP ;
-  affichage immersif dans Unity avec Meta Quest 2 ;
-  récupération des commandes des joysticks VR ;
-  transmission des commandes de pilotage vers le drone ;
-  architecture modulaire Python / Unity.


## Architecture

L'architecture générale du système est organisée de la manière suivante :
```text
                    DJI TELLO
                       │
                       │ Wi-Fi
                       ▼
                ┌───────────────┐
                │    Python     │
                │               │
                │ Acquisition   │
                │ vidéo         │
                │       │       │
                │       ▼       │
                │ Traitement    │
                │ d'image       │
                │       │       │
                │       ▼       │
                │ Compression   │
                │ JPEG          │
                └───────┬───────┘
                        │
                        │ TCP
                        ▼
                ┌───────────────┐
                │     Unity     │
                │               │
                │ Réception     │
                │ vidéo         │
                │       │       │
                │       ▼       │
                │ Affichage VR  │
                └───────┬───────┘
                        │
                        ▼
                 META QUEST 2
                        │
                     Joysticks
                        │
                        ▼
                     Unity
                        │
                        │ TCP
                        ▼
                     Python
                        │
                        ▼
                   DJI TELLO

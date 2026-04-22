# Où est mon tram ?

> Application de mobilités pour les transports de Grenoble et du territoire du SMMAG

---

## Présentation

**Où est mon tram ?** est une web app, indépendante et non officielle, qui utilise les données de l'API publique Mobilités M pour fournir des informations sur les transports en commun du réseau de Grenoble. L'application est faite pour une utilisation sur mobile mais fonctionne aussi sur PC. Pour obtenir l'application sur votre téléphone, ouvrez le lien ci dessous sur votre appareil et ajoutez la page sur l'écran d'accueil.

**[Ouvrir l'application](https://lechomeurdudimanche.github.io/ouestmontram/)**

---

## Fonctionnalités

### Horaires (`index.html`)
- Sélection par **ligne** ou par **recherche d'arrêt**
- Affichage des **prochains passages** (jusqu'à 4) avec distinction temps réel / horaires théoriques
- Indicateur de **position du tram** lorsque cela est possible. La **position du bus** est également disponible sur certaines lignes.
- Affichage du nombre de **perturbations sur la ligne** et possibilité d'obtenir le détail des perturbations
- Téléchargement de la **fiche horaire** pour chaque ligne.
- Système d'**arrêts favoris** avec accès rapide
- Copie du tripId pour les trams
<div align="center">
  <img src="screenshots/horaires.jpg" width="200"/>
  <img src="screenshots/horaires2.jpg" width="200"/>
  <img src="screenshots/horaires3.jpg" width="200"/>
  <img src="screenshots/horaires4.jpg" width="200"/>
</div>

### Suivi tram (`suivi.html`)
- Suivi d'un voyage en tram précis via son **identifiant de voyage** (ou tripId)
- Affichage de la **ponctualité** du tram en temps réel (à l'heure / en retard / en avance)
- Affichage en temps réel de la **position du tram** sur la ligne
- Affichage du temps restant avant l’arrivée à un arrêt futur du trajet, ainsi que de l’heure de passage et les prochaines correspondances de l'arrêt.
<div align="center">
  <img src="screenshots/suivi.jpg" width="200"/>
</div>

### Itinéraire (`itineraire.html`)
- Carte interactive
- Calcul d'itinéraire en transports en commun, à pied et à vélo via OpenTripPlanner (API Mobilités M)
- Possibilité de définir des lieux favoris comme un lieu de travail pour faciliter la recherche d'itinéraire
- Historique des recherches récentes sauvegardé en local
<div align="center">
  <img src="screenshots/itinéraire.jpg" width="200"/>
  <img src="screenshots/itinéraire2.jpg" width="200"/>
  <img src="screenshots/itinéraire3.jpg" width="200"/>
</div>

### Infotrafic (`infotrafic.html`)
- Liste de toutes les **perturbations en cours et à venir** sur le réseau tram et sur une bonne partie du réseau bus
- Filtrage possible par type de ligne (trams, bus chronos, bus chronos périurbains, bus proximo, bus flexo)
- Liste des perturbations d'une ligne spécifique disponible en cliquant sur l'icone de la ligne
- Affichage détaillé des retards en temps réel de l'ensemble du réseau de tramway
<div align="center">
  <img src="screenshots/infotrafic.jpg" width="200"/>
  <img src="screenshots/infotrafic2.jpg" width="200"/>
  <img src="screenshots/infotrafic3.jpg" width="200"/>
</div>

---

## Architecture

L'application est entièrement **statique**. Aucun backend, aucune base de données. Elle tient en quelques fichiers HTML/CSS/JS autonomes.

```
ouestmontram/
├── index.html        # Horaires & favoris
├── suivi.html        # Suivi d'un voyage
├── itineraire.html   # Calcul d'itinéraire
├── infotrafic.html   # Perturbations réseau
├── mentions.html     # Mentions légales
├── manifest.json     # Manifeste PWA
├── sw.js             # Service Worker
└── logo.png          # Icône de l'application
```

### Progressive Web App (PWA)

L'application est installable sur iOS et Android via le navigateur. Le `manifest.json` déclare le nom, les couleurs et l'icône, et le `sw.js` enregistre un service worker.

---

## Sources de données

| Source | Usage |
|---|---|
| [Mobilités M](https://data.mobilites-m.fr/) (SMMAG) | Horaires, temps réel, topologies, perturbations, itinéraires |
| [OpenTripPlanner](https://www.opentripplanner.org/) | Moteur de calcul d'itinéraire (via Mobilités M) |
| [CARTO](https://carto.com/) | Tuiles cartographiques |
| [OpenStreetMap](https://www.openstreetmap.org/) | Données géographiques |
| [Base Adresse Nationale](https://adresse.data.gouv.fr/) | Géocodage d'adresses françaises |
| [Photon (Komoot)](https://photon.komoot.io/) | Géocodage complémentaire (OSM) |

### Bibliothèques front-end

| Bibliothèque | Usage |
|---|---|
| [Leaflet](https://leafletjs.com/) | Cartographie interactive |
| [QRCode.js](https://github.com/davidshimjs/qrcodejs) | Génération du QR code de partage |
| [Google Fonts](https://fonts.google.com/) | Typographie |

---

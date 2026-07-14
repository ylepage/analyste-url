# Proofpoint URL Decoder + Shortener Resolver

Outil d'analyse d'URLs en HTML/JS pur (zéro dépendance) qui :

- **Décodage Proofpoint** v1/v2/v3 — 100% local (regex + URL decode + base64url v3)
- **Résolution de raccourcisseurs** — tente HEAD puis GET, lit `response.url` (best effort, sujet à CORS)
- **Évaluation heuristique du risque** — HTTP non chiffré, IP directe, extensions exécutables, caractères cyrilliques, sous-domaines anormaux
- **Vérification VirusTotal** — intégration API avec modal de saisie de clé API (stockée localement) + fallback CORS pour `file://`
- **Liens vers Google Safe Browsing** — ouvert dans un nouvel onglet
- **Bilingue** — toggle FR/EN, préférence sauvegardée en `localStorage`
- **Export** — copie des résultats structurés dans le presse-papiers

## Utilisation

Ouvrez `index.html` dans votre navigateur — aucune dépendance, aucun serveur requis. Pour la vérification VirusTotal, lancez un serveur local :

```bash
python -m http.server 8080
# puis ouvrez http://localhost:8080
```

## Raccourcis

- **Ctrl+Entrée** : lancer l'analyse
- **FR/EN** : changer la langue (persistance localStorage)

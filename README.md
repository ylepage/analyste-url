# Proofpoint URL Decoder + Shortener Resolver

On remet parfois le poids de vérifier la validité des URL dans les courriels dans les mains des utilisateurs. La majorité des outils de sécurité de courriels réécrivent les URL et les rendent plus difficiles à lire. Cette preuve de concept permet à l'utilisateur de vérifier les URL qui seraient récrits par Proofpoint, puis de pousser plus loin la vérification si nécessaire avec les outils VirusTotal et Google.

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
Vous aurez besoin d'une clé API personnelle pour utiliser la vérification VirusTotal https://www.virustotal.com/gui/sign-in

## Raccourcis

- **Ctrl+Entrée** : lancer l'analyse
- **FR/EN** : changer la langue (persistance localStorage)

## Prochaines étapes
 Support Checkpoint (SandBlast URL)
 Support Egress (URL rewriting)
 Intégration additionelle d'autres threat intel feeds

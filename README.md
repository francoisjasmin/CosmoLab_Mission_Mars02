# 🚀 CosmoLab — Mission Mars 2.0

## Démarrage (enseignant et étudiant)

1. Décompresser le ZIP dans un dossier.
2. Double-cliquer `index.html` dans **Chrome** ou **Edge**.
3. Entrer le nom de l'étudiant et le groupe.
4. Terminer les cinq missions de l'histoire ARES-7.
5. À la fin, cliquer sur **Imprimer / Enregistrer en PDF**.

L'application fonctionne **sans serveur, connexion Internet ou installation**. Les deux missions IA nécessitent seulement un accès à un assistant IA externe, dans un autre onglet ; le jeu lui-même n'appelle jamais ce service. En l'absence d'IA, le joueur peut utiliser les jeux de secours avec des points réduits.

## Contenu

- `index.html` : interface, navigation, panneau d'aide.
- `style.css` : design futuriste martien, animations, responsive, impression.
- `script.js` : missions et moteur de validation JSON, progression, score, sauvegarde.

## Missions, durée indicative et pointage

| Mission | Durée | Barème |
|---|---:|---:|
| 1. Diagnostic martien | 4 min | 5 × 4 = 20 |
| 2. Archives stellaires | 5 min | 6 × 3 + 1 × 2 = 20 |
| 3. Chrono-Sol | 5 min | Tri (12) + questions (4 + 4) = 20 |
| 4. Forge de données IA | 9 min | Prompt (4) + génération JSON (10) + critique JSON (6) = 20 |
| 5. Sabotage des données | 7 min | 5 × 4 = 20 |

**Total : 100 points, environ 30 minutes, sans chronomètre ni limite de temps.** La mention « Mission complétée » apparaît seulement après les cinq missions, indépendamment du score.

## Gestion des erreurs

- Questions classiques : premier essai = totalité, deuxième essai = environ la moitié, troisième réponse ou solution dévoilée = 0 point.
- Génération IA : 10 points au premier JSON conforme, puis 7, 5, 3 ; exemple de secours = 2.
- Correction IA : 6 points au premier JSON conforme, puis 4, 2, 1 ; exemple de secours = 0.
- Le bouton de secours exige confirmation ; il permet de poursuivre sans IA externe.
- Les classements sont possibles en drag & drop **et** par boutons, pour garantir l'accessibilité.

## Règles de CosmoLab

- Température : -70 °C ≤ T ≤ 20 °C (bornes inclusives).
- Oxygène : O₂ ≥ 18 %.
- Radiation : R ≤ 5 mSv.
- Batterie : B ≥ 20 %.
- Une mesure hors seuil entraîne `ALERTE`.
- Une valeur absente, nulle, textuelle ou non numérique est `INVALIDE`, pas `STABLE`.

Les données IA attendent un objet JSON racine :

```json
{
  "mission": {"name":"ARES-7","description":"Données fictives"},
  "crew": [{"id":"C01","name":"Maya","role":"Ingénieure"}],
  "readings": [
    {"id":"G01","sol":501,"date":"2042-09-01","temperature":-30,"oxygen":21,"radiation":2,"battery":80}
  ]
}
```

La validation de la Forge IA vérifie la structure, les types, les dates, les Sols, l'unicité, la couverture d'alertes et de valeurs frontières. La mission Critique impose huit identifiants Q01 à Q08, des Sols 601 à 608 et une séquence chronologique cohérente.

## Rapport final

Le rapport contient nom, groupe, date, identifiant de session, durée, score, XP, rang, badges, détail par mission et maîtrise par concept. L'identifiant de session est local : **ce n'est pas une attestation cryptographique**. Le rapport est conçu pour tenir sur une page Lettre et peut être enregistré en PDF par le navigateur.

## Sauvegarde, confidentialité et remise

- Sauvegarde via `localStorage` de ce navigateur, pour ce dossier et cette origine ; la disponibilité varie selon les réglages des navigateurs, notamment en mode `file://` et navigation privée.
- Pour préserver l'avancement, rouvrir le même `index.html` dans le même navigateur, sans effacer ses données.
- Aucun renseignement n'est transmis automatiquement vers Internet.
- Ne pas envoyer de données réelles ou de secrets dans un outil IA externe non autorisé.
- La réinitialisation efface les résultats enregistrés localement et démarre une nouvelle session.
- La seule remise demandée est le **rapport final imprimé ou enregistré en PDF**.

## Conseils de test rapide pour l'enseignant

1. Tester une valeur exactement sur un seuil et juste au-delà.
2. Tester la Mission Archives avec la souris, puis au clavier (sélection + bouton de secteur).
3. Tester le réordonnancement des Sols avec les flèches et avec drag & drop.
4. Coller dans la Forge un JSON invalide (`{oops}`), puis vérifier les explications.
5. Corriger des IDs en doublon, une valeur textuelle, une date incorrecte.
6. Utiliser les exemples de secours pour atteindre le rapport et vérifier l'impression.
7. Relancer la page pour vérifier la reprise de session.

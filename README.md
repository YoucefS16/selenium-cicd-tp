![alt text](<Testsreussis.png>)

1) Avantages observés

Automatisation des tests : une fois les tests écrits, tu peux vérifier automatiquement que les fonctionnalités clés (chargement de page, addition, division par zéro, etc.) marchent toujours après chaque modification. Ça évite les vérifications manuelles répétitives et ça réduit les oublis.

CI/CD et qualité : un pipeline CI/CD exécute les tests à chaque push/PR, donc il détecte tôt les régressions. Ça force aussi à garder un projet “exécutable” (dépendances, structure, scripts) et ça rend les erreurs visibles avant fusion sur main.

2) Défis rencontrés

Selenium/WebDriver : la mise en place du driver est une source fréquente de problèmes (versions Chrome/ChromeDriver, compatibilité OS, cache webdriver-manager). Exemple typique : erreur de lancement du driver (WinError 193) qui bloque tous les tests avant même d’exécuter les assertions.

Stabilité des tests : les tests UI peuvent devenir flakey (timing, chargement, éléments pas prêts). Pour améliorer la stabilité :

privilégier WebDriverWait plutôt que sleep

isoler les tests (recharger la page, éviter que l’état précédent influence le suivant)

rendre les sélecteurs robustes (IDs stables)

éviter les assertions fragiles sur des détails d’affichage qui varient selon OS/navigateur.

3) Métriques

Taux de réussite des tests (pass/fail) : métrique de base, suivie à chaque run CI.

Durée des tests/pipeline : important pour garder un feedback rapide (si ça devient trop long, les devs le contournent).

Couverture de code (via pytest-cov) : donne une idée des zones du code réellement exercées par les tests, à compléter par une logique “qualitative” (tester les cas critiques).

Performance simple : temps de chargement (ton test “< 3s”) est un exemple de métrique non-fonctionnelle utile.

Rapports : rapports HTML pytest + artefacts CI (trace des résultats) permettent de mesurer l’évolution et de diagnostiquer les échecs.
# Préparation à la certification AWS Certified Machine Learning Engineer – Associate (MLA-C02, bêta)

**Changement de cible (28 août) : MLA-C02, pas MLA-C01.** Ce document visait initialement MLA-C01 avant sa retraite du 28 septembre. Nouvelle cible : la version bêta de **MLA-C02**, orientée IA générative/agentique.

Ce que ça change concrètement :

- Inscription à la bêta ouverte à partir du **1er septembre 2026** — c'est aussi la date où AWS publie le guide d'examen détaillé (task statements précis). Avant cette date, on travaille sur la base du guide MLA-C01 (les 4 domaines et leurs poids ne changent pas), en sachant que le contenu génératif/agentique sera précisé au dernier moment.
- Passage possible **à partir du 29 septembre 2026** (le lendemain de la fermeture de MLA-C01), 85 questions au lieu de 65, 170 minutes, 75 $, uniquement en anglais, via Pearson VUE.
- **Les résultats d'un examen bêta mettent jusqu'à 90 jours à sortir** (contre 5 jours ouvrés pour un examen standard) — le temps qu'AWS analyse les réponses de tous les candidats bêta avant de fixer le score de passage définitif. Concrètement : pas de confirmation immédiate le jour de l'examen, à garder en tête si une date de certification précise compte pour toi (candidature, exigence employeur...).
- La version standard (non bêta) de MLA-C02 n'arrive qu'**début 2027**.

Aujourd'hui : le 28 août. Fenêtre avant le premier créneau possible (29 sept) : environ 4,5 semaines, dont les 4 premiers jours sur le contenu MLA-C01 (encore valable, les domaines ne changent pas) puis ajustement dès la sortie du guide le 1er septembre.

Méthode : Feynman, comme dans [`../Cahier-Vacances-2026-Documentation/`](../Cahier-Vacances-2026-Documentation/METHODE-FEYNMAN.md) — expliquer simplement, repérer les trous, combler avec des analogies et des exemples concrets. La différence ici : les trous ne sont presque jamais des trous de compréhension ML (les projets du cahier ont déjà construit cette base), ce sont des trous de **vocabulaire et d'outillage AWS** sur des concepts déjà acquis — plus, pour MLA-C02, du contenu réellement nouveau (IA générative, modèles de fondation, workflows agentiques) qui n'a pas d'équivalent direct dans le cahier.

## L'examen, factuellement

- **Structure inchangée par rapport à MLA-C01** : mêmes 4 domaines, mêmes poids (AWS l'a confirmé — les task statements existants sont mis à jour pour refléter les pratiques actuelles, mais aucun domaine n'est ajouté ou retiré).
- Version bêta : 85 questions, 170 minutes, 75 $. (La version MLA-C01 avait 65 questions dont 50 notées ; le détail scoré/non-scoré de la bêta MLA-C02 n'est pas encore publié.)
- Score sur 100–1000, seuil de passage à confirmer pour la bêta (720 pour MLA-C01).
- Modèle de notation compensatoire : pas besoin de réussir chaque domaine, seulement le total.
- Types de questions : QCM classique, choix multiples, mise en ordre, appariement, étude de cas (plusieurs questions sur un même scénario).
- Contenu ajouté par rapport à MLA-C01, selon AWS : solutions d'IA générative, modèles de fondation et LLM, workflows agentiques, mise à l'échelle ("operationalization") de l'IA en production.
- Quatre domaines, chacun avec 2-3 "task statements" officiels (poids et intitulés ci-dessous encore ceux de MLA-C01 — à recaler le 1er septembre) :

| # | Domaine | Poids | Task statements |
|---|---|---|---|
| 1 | Préparation des données pour le ML | **28 %** | 1.1 Ingérer et stocker les données · 1.2 Transformer et faire du feature engineering · 1.3 Garantir l'intégrité des données |
| 2 | Développement de modèle | **26 %** | 2.1 Choisir une approche de modélisation · 2.2 Entraîner et affiner les modèles · 2.3 Analyser la performance du modèle |
| 3 | Déploiement et orchestration | **22 %** | 3.1 Choisir l'infrastructure de déploiement · 3.2 Scripter l'infrastructure (IaC) · 3.3 Mettre en place des pipelines CI/CD |
| 4 | Monitoring, maintenance et sécurité | **24 %** | 4.1 Monitorer l'inférence · 4.2 Monitorer et optimiser l'infra/les coûts · 4.3 Sécuriser les ressources AWS |

L'écrasante majorité des questions portent sur **Amazon SageMaker**. Sont explicitement hors périmètre : concevoir une architecture ML de bout en bout, définir une stratégie ML d'entreprise, la NLP/vision en profondeur, la quantification de modèles.

## Ce que le cahier de vacances a déjà construit — et ce qui manque

Le tableau suivant est le cœur de la méthode : pour chaque task statement, à quel projet déjà fait ça ressemble (le point d'ancrage Feynman), et ce qui est entièrement nouveau (le vocabulaire AWS à apprendre par-dessus).

| Task statement | Déjà acquis (cahier) | Entièrement nouveau (AWS) |
|---|---|---|
| 1.1 Ingérer/stocker | Projet_01 (SQL relationnel) | S3, EFS, FSx, Kinesis/Flink/Kafka, formats Parquet/ORC/Avro/RecordIO, SageMaker Data Wrangler |
| 1.2 Transformer/feature engineering | Projet_02 (`build_training_table`), Projet_07/08 (parsing PDF → DataFrame) | AWS Glue, Glue DataBrew, SageMaker Feature Store, SageMaker Ground Truth |
| 1.3 Intégrité des données | Projet_08 (le bug `total_amount` trouvé et corrigé) | SageMaker Clarify (biais), chiffrement, PII/PHI, conformité |
| 2.1 Choisir une approche | Projet_02 (classification), Projet_03 (clustering), Projet_04/07 (RAG vs fine-tuning) | Amazon Bedrock, SageMaker JumpStart, algorithmes intégrés SageMaker |
| 2.2 Entraîner/affiner | Projet_02 (train/test split, RandomForest), Projet_05 (fine-tuning), Projet_06 (ARMA) | SageMaker script mode, Automatic Model Tuning, Model Registry |
| 2.3 Analyser la performance | Projet_02/06 (métriques, MAE, Ljung-Box) | SageMaker Clarify, Model Debugger, variante shadow vs production |
| 3.1 Infrastructure de déploiement | Projet_07/08 (API sans état, Docker) | Endpoints SageMaker (temps réel/serverless/asynchrone/batch), SageMaker Neo |
| 3.2 Infrastructure as code | *rien* | CloudFormation, CDK, auto scaling, ECR/ECS/EKS, VPC |
| 3.3 CI/CD | *rien* (identifié comme manque dans `BILAN-ENTREPRISE.md`) | CodePipeline, CodeBuild, CodeDeploy, EventBridge, blue/green/canary |
| 4.1 Monitorer l'inférence | Le logging ajouté récemment à Projet_08 (même intention, pas le même outil) | SageMaker Model Monitor, dérive de données, A/B testing |
| 4.2 Infra/coûts | *rien* | CloudWatch, X-Ray, CloudTrail, Cost Explorer, Trusted Advisor, types d'instances |
| 4.3 Sécuriser | Identifié comme manque dans `BILAN-ENTREPRISE.md` ("aucun contrôle d'accès") | IAM (rôles/policies), VPC/security groups, KMS, Secrets Manager |

Constat honnête : les domaines 1 et 2 (54 % de l'examen) s'appuient sur une vraie base déjà là. Les domaines 3 et 4 (46 %) demandent d'apprendre l'outillage AWS presque en partant de zéro — c'est là qu'il faut mettre le plus de temps.

## Projet de portage : predict-student-dropout → AWS

En plus du cahier de vacances, un second projet sert de terrain de pratique principal : [`predict-student-dropout`](C:\Users\Tchoupo\PyCharmMiscProject\predict-student-dropout), un système de classification (décrochage scolaire) avec un pipeline déjà proche d'un usage réel — préparation des données, rééquilibrage SMOTE, validation de schéma (TFDV), comparaison de 3 modèles (Decision Tree, Random Forest, Gradient Boosting) avec recherche d'hyperparamètres, service via Flask + `joblib`, conteneurisé avec Docker.

Sa propre documentation (`Chapitre6.md`, section "Limites actuelles") liste déjà, dans ses mots : pas d'orchestration avancée, pas de monitoring de dérive, pas de CI/CD, pas de tests de charge, pas de service de model serving spécialisé — une table des matières presque exacte des Domaines 3 et 4 de l'examen. L'idée : porter ce projet vers AWS, domaine par domaine, plutôt que faire des exercices isolés sans lien entre eux.

| Fichier du projet | Ce qu'il fait déjà en local | Portage AWS visé |
|---|---|---|
| `training/PreValModels/data_preparation.py`, `data_validation.py` | Nettoyage, encodage, split stratifié, rééquilibrage SMOTE | S3 + Glue/DataBrew pour la préparation ; SageMaker Clarify pour mesurer le déséquilibre de classes avant/après (1.1, 1.2, 1.3) |
| `training/PreValModels/model_selection.py` | 3 modèles comparés via `HalvingRandomSearchCV`, F1 pondéré, validation croisée | SageMaker Training Job (script mode) + Automatic Model Tuning à la place de la recherche locale (2.1, 2.2, 2.3) |
| `app.py`, `src/presentation/`, `training/PreValModels/models/best_model.joblib` | Service Flask qui charge le modèle sérialisé, API `POST /predict` | Endpoint SageMaker temps réel, puis serverless, comparaison latence/coût avec le Flask actuel (3.1) |
| `Dockerfile`, déploiement manuel | Conteneur reproductible, déploiement local ou Vercel à la main | CodePipeline/CodeBuild déclenché sur le dépôt Git, pour remplacer le déploiement manuel (3.3) |
| *Limite listée : "absence de monitoring de dérive"* | Rien en place | SageMaker Model Monitor sur l'endpoint déployé (4.1) |
| *Limite listée : accès non détaillé* | Pas de rôle applicatif dédié | Rôle IAM à privilège minimal pour le service, à la place d'un accès local non contraint (4.3) |

## Programme jusqu'au premier créneau bêta (29 septembre)

**28–31 août — Domaine 1, sur la base MLA-C01.** Une fiche Feynman par task statement (1.1, 1.2, 1.3). Le contenu "préparation des données" est le moins susceptible de changer avec le virage gen-AI, donc le moins risqué à démarrer avant la sortie du guide définitif. Pratique : charger le dataset de `predict-student-dropout` dans S3, reproduire le nettoyage/encodage de `data_preparation.py` via un job Glue DataBrew, puis comparer le SMOTE local (`data_validation.py`) à une mesure de class imbalance via SageMaker Clarify.

**1er septembre — Point de bascule.** Le guide d'examen MLA-C02 sort. Lire les task statements mis à jour, en particulier ceux du Domaine 2 (modélisation) et du Domaine 3 (déploiement), les plus susceptibles d'intégrer explicitement Bedrock, les modèles de fondation et les workflows agentiques. Ajuster le reste du programme si besoin (une nouvelle version de ce README, pas une réécriture depuis zéro — la structure en 4 domaines reste valable).

**2–8 sept — Domaine 2.** Fiches 2.1, 2.2, 2.3, mises à jour avec le contenu gen-AI confirmé. Pratique : reprendre `model_selection.py` (Decision Tree/Random Forest/Gradient Boosting) et relancer la comparaison via un SageMaker Estimator en script mode, avec Automatic Model Tuning à la place de `HalvingRandomSearchCV` — comparer le F1 pondéré obtenu ; tester ensuite un modèle de fondation via Bedrock sur le même problème pour illustrer l'opposition explicite entre les deux approches (2.1).

**9–15 sept — Domaine 3.** Fiches 3.1, 3.2, 3.3 — déjà le domaine le plus neuf sur MLA-C01, probablement encore plus chargé en nouveauté ici (orchestration de workflows agentiques). Pratique : remplacer le service Flask + `joblib` (`app.py`) par un endpoint SageMaker temps réel, puis un endpoint serverless, comparer latence et coût avec le Flask actuel.

**16–22 sept — Domaine 4.** Fiches 4.1, 4.2, 4.3. Pratique : combler les deux limites listées dans `Chapitre6.md` — ajouter SageMaker Model Monitor sur l'endpoint déployé en semaine précédente, et un rôle IAM à privilège minimal pour y accéder, à la place d'un accès local non contraint.

**23–28 sept — Intégration et inscription.** S'inscrire à la bêta dès que possible après le 1er septembre (les places sont limitées sur ce type d'examen). Un ou deux examens blancs si un fournisseur en propose déjà sur MLA-C02 (sinon, se rabattre sur les blancs MLA-C01 pour les domaines 1-2, moins susceptibles d'avoir changé). Revoir le tableau de mapping ci-dessus et le tableau de portage.

**À partir du 29 sept — Passage de l'examen**, en sachant que le résultat peut mettre jusqu'à 90 jours à arriver.

## Le gabarit Feynman pour chaque fiche

Même structure que les fiches `FEYNMAN.md` du cahier, adaptée à un service/concept AWS :

1. **En une phrase** — ce que fait ce service, sans jargon.
2. **Analogie** — le rapprocher d'un projet déjà fait (voir le tableau ci-dessus).
3. **Vocabulaire** — les termes AWS, en tableau, avec leur équivalent déjà connu.
4. **Comment ça marche en détail** — la mécanique du service, ce qui est configurable.
5. **Un exemple annoté** — console, CLI ou `boto3`, jamais du code non testé.
6. **Pièges classiques** — les questions d'examen AWS opposent souvent 3-4 services plausibles (ex. endpoint temps réel vs serverless vs asynchrone vs batch) ; cette section liste ces oppositions explicitement.
7. **Test de Feynman** — 3-5 questions, dans l'esprit des questions d'examen (scénario + "quel service choisir ?").

## Avancement

- [x] Domaine 1 — Préparation des données (sur la base du guide MLA-C01, texte exact des task statements 1.1/1.2/1.3) : [`Domaine-1-Preparation-des-donnees/`](./Domaine-1-Preparation-des-donnees/)
- [ ] Domaine 2 — Développement de modèle
- [ ] Domaine 3 — Déploiement et orchestration
- [ ] Domaine 4 — Monitoring, maintenance, sécurité

## Prochaine étape

Le 1er septembre : relire ces 3 fiches à la lumière du vrai guide MLA-C02 et ajuster si le contenu gen-AI y touche (probable surtout pour 1.2, feature engineering — potentiel ajout autour des embeddings/modèles de fondation). En attendant, enchaîner sur le Domaine 2.

## Sources

- [AWS Certified Machine Learning Engineer – Associate — page officielle](https://aws.amazon.com/certification/certified-machine-learning-engineer-associate/)
- [Guide d'examen officiel MLA-C01 (PDF)](https://d1.awsstatic.com/training-and-certification/docs-machine-learning-engineer-associate/AWS-Certified-Machine-Learning-Engineer-Associate_Exam-Guide.pdf)
- [Updates to AWS Certified Machine Learning Engineer – Associate (MLA-C02) — AWS Training and Certification Blog](https://aws.amazon.com/blogs/training-and-certification/updates-to-aws-certified-machine-learning-engineer-associate-mla-c02/)
- [What's New with MLA-C02 in 2026 — Tutorials Dojo](https://tutorialsdojo.com/whats-new-with-the-aws-certified-machine-learning-engineer-associate-mla-c02-in-2026/)
- [AWS Certification policies — after testing (délai des résultats)](https://aws.amazon.com/certification/policies/after-testing)

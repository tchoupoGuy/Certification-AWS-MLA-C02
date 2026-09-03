# Préparation à la certification AWS Certified Machine Learning Engineer – Associate (MLA-C02, bêta)

**Mise à jour du 3 septembre : le vrai guide d'examen MLA-C02 est publié.** Les inscriptions à la bêta ont ouvert le 1er septembre comme prévu, et AWS a mis en ligne le guide d'examen détaillé le même jour. Tout ce document (poids des domaines, task statements, sources) est désormais basé sur ce guide officiel — plus une hypothèse construite sur MLA-C01 en attendant.

- [Guide d'examen officiel MLA-C02](https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/machine-learning-engineer-associate-02.html)
- [Comparaison officielle MLA-C01 → MLA-C02](https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/mla-02-comparison.html) (ajouts/retraits/recatégorisations, skill par skill)
- Inscription possible **à partir du 29 septembre 2026** (le lendemain de la fermeture de MLA-C01), 85 questions, 170 minutes, 75 $, uniquement en anglais, via Pearson VUE.
- **Les résultats d'un examen bêta mettent jusqu'à 90 jours à sortir** (contre 5 jours ouvrés pour un examen standard), et la désignation réussite/échec elle-même ne s'applique officiellement pas à la version bêta — le temps qu'AWS calibre le seuil de passage définitif à partir des réponses de tous les candidats bêta. Concrètement : pas de confirmation immédiate le jour de l'examen.
- La version standard (non bêta) de MLA-C02 n'arrive qu'**début 2027**.

Méthode : Feynman, comme dans [`../Cahier-Vacances-2026-Documentation/`](../Cahier-Vacances-2026-Documentation/METHODE-FEYNMAN.md) — expliquer simplement, repérer les trous, combler avec des analogies et des exemples concrets. La différence ici : les trous ne sont presque jamais des trous de compréhension ML (les projets du cahier ont déjà construit cette base), ce sont des trous de **vocabulaire et d'outillage AWS** sur des concepts déjà acquis — plus, pour MLA-C02, du contenu réellement nouveau (IA générative, modèles de fondation, workflows agentiques) qui n'a pas d'équivalent direct dans le cahier.

## L'examen, factuellement (confirmé par le guide officiel)

| Détail | MLA-C02 (bêta) | MLA-C01 (actuel) |
|---|---|---|
| Code examen | ME1-C02 | MLA-C01 |
| Durée | 170 minutes | 130 minutes |
| Format | 85 questions (dont des items expérimentaux non notés propres à la bêta) | 65 questions |
| Coût | 75 $ (tarif bêta) | 150 $ |
| Questions notées / non notées (cible standard) | 50 notées + 15 non notées = 65 | — |
| Score | 100–1000, seuil de passage 720 pour la version standard — **ne s'applique pas formellement à la bêta** | 720/1000 |
| Types de question | Choix multiple (1 bonne réponse, 3 distracteurs), réponses multiples (2+ bonnes réponses parmi 5+) — **rien d'officiellement confirmé sur d'autres formats** (mise en ordre, appariement...) | — |
| Modèle de notation | Compensatoire : pas besoin de réussir chaque domaine, seulement le total | Idem |
| Langue | Anglais uniquement pendant la bêta | Anglais + japonais, coréen, chinois simplifié |

Structure inchangée par rapport à MLA-C01 : **4 domaines, aucun ajouté ni retiré**, mais les poids ont bougé et les intitulés intègrent désormais explicitement les modèles de fondation (FM) :

| # | Domaine (MLA-C02) | Poids MLA-C02 | Poids MLA-C01 |
|---|---|---|---|
| 1 | Data Preparation for ML and AI | **28 %** | 28 % (inchangé) |
| 2 | ML Model and Foundation Model (FM) Development | **24 %** | 26 % |
| 3 | Deployment and Orchestration of ML and AI Workflows | **24 %** | 22 % |
| 4 | Operating, Monitoring, and Securing ML and AI Solutions | **24 %** | 24 % (inchangé) |

Chaque domaine garde 3 task statements officiels (mêmes intitulés généraux, task statements recatégorisés 1:1 avec MLA-C01, voir tableau complet ci-dessous). Contenu explicitement ajouté par rapport à MLA-C01, selon la comparaison officielle : bases de données vectorielles, ingestion multimodale, embeddings et chunking pour RAG, préparation de données de fine-tuning de FM (Domaine 1) ; sélection/évaluation de FM via Bedrock, RAG, prompt engineering, métriques NLP (BLEU/ROUGE/BERTScore), LLM-as-a-judge (Domaine 2) ; déploiement de FM et d'agents, Knowledge Bases Bedrock, CI/CD pour prompts et agents (Domaine 3) ; observabilité et coûts spécifiques aux FM/agents, Bedrock Guardrails (Domaine 4). Rien n'a de contenu portant sur la NLP/vision "from scratch" en profondeur ni sur la quantification de modèles — hors périmètre.

## Ce que le cahier de vacances a déjà construit — et ce qui manque

| Task statement (MLA-C02) | Déjà acquis (cahier) | Entièrement nouveau (AWS) |
|---|---|---|
| 1.1 Collecter et stocker | Projet_01 (SQL relationnel) | S3, EFS, FSx, Kinesis/Flink/Kafka, formats Parquet/ORC/Avro/RecordIO, bases vectorielles (OpenSearch, pgvector) |
| 1.2 Transformer, feature engineering, pré-traitement | Projet_02 (`build_training_table`), Projet_07/08 (parsing PDF → DataFrame, embeddings) | AWS Glue, Glue DataBrew, SageMaker Feature Store, chunking RAG, préparation de données de fine-tuning |
| 1.3 Valider la qualité des données et gérer le biais | Projet_08 (le bug `total_amount` trouvé et corrigé), predict-student-dropout (`handle_outliers`) | SageMaker Clarify (biais), chiffrement, PII/PHI, conformité, validation de données d'entraînement IA |
| 2.1 Choisir une approche de modélisation | predict-student-dropout (3 modèles comparés), Projet_03 (clustering), Projet_04/07 (RAG) | Amazon Bedrock, SageMaker JumpStart, AWS AI services (Textract, Rekognition, Comprehend) |
| 2.2 Entraîner, affiner, personnaliser | predict-student-dropout (`HalvingRandomSearchCV`), Projet_05 (fine-tuning) | SageMaker script mode, Automatic Model Tuning, personnalisation de FM (prompt engineering, fine-tuning) |
| 2.3 Analyser et évaluer la performance | predict-student-dropout (F1, matrice de confusion), Projet_06 (MAE, Ljung-Box) | SageMaker Clarify, MLflow, BLEU/ROUGE/BERTScore, LLM-as-a-judge, shadow variants |
| 3.1 Gérer l'infrastructure de déploiement | predict-student-dropout (Flask + Gunicorn + Docker) | Endpoints SageMaker (temps réel/serverless/asynchrone/batch), déploiement d'agents et de FM |
| 3.2 Provisionner et configurer les ressources | Projet_08 (`docker-compose.yml`, orchestration locale) | CloudFormation, CDK, VPC, auto scaling, GPU scaling, Bedrock Knowledge Bases |
| 3.3 CI/CD et orchestration automatisée | predict-student-dropout (`.github/workflows/ci.yml`, tests auto) | CodePipeline, CodeBuild, CodeDeploy, blue/green/canary, SageMaker Model Registry, Bedrock Prompt Management |
| 4.1 Monitorer l'inférence | Le logging ajouté à predict-student-dropout (même intention, pas le même outil) | SageMaker Model Monitor, dérive de données, A/B testing, monitoring d'agents |
| 4.2 Optimiser coûts/infra | *rien* | CloudWatch, X-Ray, Cost Explorer, types d'instances, coûts spécifiques FM (tokens, embeddings) |
| 4.3 Sécuriser les charges de travail | Identifié comme manque dans `BILAN-ENTREPRISE.md` ("aucun contrôle d'accès") | IAM (rôles/policies), VPC/security groups, KMS, Secrets Manager, Bedrock Guardrails |

Constat honnête : les domaines 1 et 2 (52 % de l'examen) s'appuient sur une vraie base déjà là, y compris désormais côté FM (RAG déjà pratiqué via Projet_04/07/08). Les domaines 3 et 4 (48 %) demandent d'apprendre l'outillage AWS presque en partant de zéro pour tout ce qui touche à l'infrastructure cloud elle-même (provisioning, réseau, coûts, IAM) — predict-student-dropout comble une bonne partie du volet déploiement applicatif (3.1, 3.3), mais rien dans le cahier ne touche au provisioning d'infrastructure ni à la sécurité IAM.

## Projet de portage : predict-student-dropout → AWS

En plus du cahier de vacances, un second projet sert de terrain de pratique principal : [`predict-student-dropout`](C:\Users\Tchoupo\PyCharmMiscProject\predict-student-dropout), un système de classification (décrochage scolaire) avec un pipeline proche d'un usage réel — préparation des données, rééquilibrage SMOTE, validation de schéma (TFDV), comparaison de 3 modèles avec recherche d'hyperparamètres, service via Flask + Gunicorn + `joblib`, conteneurisé avec Docker, testé (31+14 tests) et avec une CI GitHub Actions.

Sa propre documentation (`BILAN-ENTREPRISE.md`, section "Ce qui manque encore") liste déjà, dans ses mots : pas de monitoring de dérive, pas de tests de charge, pas de service de model serving spécialisé, pas de déploiement automatisé (CD) — une table des matières presque exacte des Domaines 3 et 4 de l'examen.

| Fichier du projet | Ce qu'il fait déjà en local | Portage AWS visé |
|---|---|---|
| `training/PreValModels/infrastructure/data_preparation.py`, `data_validation.py` | Nettoyage, encodage, split stratifié, rééquilibrage SMOTE | S3 + Glue/DataBrew ; SageMaker Clarify pour mesurer le déséquilibre de classes (1.1, 1.2, 1.3) |
| `training/PreValModels/infrastructure/model_selection.py` | 3 modèles comparés via `HalvingRandomSearchCV`, F1 pondéré | SageMaker Training Job (script mode) + Automatic Model Tuning (2.1, 2.2, 2.3) |
| `app.py`, `src/presentation/`, `Dockerfile` (Gunicorn) | Service Flask+Gunicorn, API `POST /predict`, conteneurisé | Endpoint SageMaker temps réel, puis serverless, comparaison latence/coût (3.1) |
| `.github/workflows/ci.yml` | CI : tests automatiques à chaque push (2 jobs uv) | CodePipeline/CodeBuild pour aller jusqu'au déploiement automatique — CD, pas seulement CI (3.3) |
| *Limite listée : "pas de monitoring de dérive"* | Rien en place | SageMaker Model Monitor sur l'endpoint déployé (4.1) |
| *Limite listée : accès non détaillé* | Pas de rôle applicatif dédié | Rôle IAM à privilège minimal pour le service (4.3) |

## Le gabarit Feynman pour chaque fiche

1. **En une phrase** — ce que fait ce service, sans jargon.
2. **Analogie** — le rapprocher d'un projet déjà fait.
3. **Vocabulaire** — les termes AWS, en tableau, avec leur équivalent déjà connu.
4. **Comment ça marche en détail** — la mécanique du service, ce qui est configurable.
5. **Un exemple annoté** — console, CLI, boto3 ou code déjà existant, jamais du code non testé.
6. **Ancrage** — le lien concret avec un fichier réel du cahier ou de predict-student-dropout.
7. **Pièges classiques** — les oppositions que l'examen aime poser entre 2-4 services plausibles.
8. **Test de Feynman** — 3-6 questions dans l'esprit des questions d'examen.

## Avancement

- [x] Domaine 1 — Data Preparation for ML and AI : [`Domaine-1-Preparation-des-donnees/`](./Domaine-1-Preparation-des-donnees/) — 3 fiches (1.1, 1.2, 1.3), relues et complétées avec le vrai guide MLA-C02 (sections "Nouveauté MLA-C02" ajoutées)
- [x] Domaine 2 — ML Model and Foundation Model (FM) Development : [`Domaine-2-Developpement-modele-FM/`](./Domaine-2-Developpement-modele-FM/) — 3 fiches (2.1, 2.2, 2.3)
- [x] Domaine 3 — Deployment and Orchestration of ML and AI Workflows : [`Domaine-3-Deploiement-orchestration/`](./Domaine-3-Deploiement-orchestration/) — 3 fiches (3.1, 3.2, 3.3)
- [x] Domaine 4 — Operating, Monitoring, and Securing ML and AI Solutions : [`Domaine-4-Operation-monitoring-securite/`](./Domaine-4-Operation-monitoring-securite/) — 3 fiches (4.1, 4.2, 4.3)

## Prochaine étape

Les 12 fiches (4 domaines complets) sont écrites. Reste à consolider par la pratique : reprendre le tableau de portage ci-dessus et implémenter concrètement au moins un morceau par domaine sur un vrai compte AWS (Free Tier — voir échanges précédents sur SageMaker Studio), plutôt que de rester purement théorique. S'inscrire à la bêta dès que possible (places limitées). Un ou deux examens blancs si un fournisseur en propose déjà sur MLA-C02.

## Sources

- [AWS Certified Machine Learning Engineer – Associate — page officielle](https://aws.amazon.com/certification/certified-machine-learning-engineer-associate/)
- [Guide d'examen officiel MLA-C02](https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/machine-learning-engineer-associate-02.html) (introduction, contenu, 4 domaines détaillés)
- [Comparaison officielle MLA-C01 → MLA-C02](https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/mla-02-comparison.html) (ajouts/retraits/recatégorisations, skill par skill)
- [Services et fonctionnalités hors périmètre MLA-C02](https://docs.aws.amazon.com/aws-certification/latest/machine-learning-engineer-associate-02/mla-02-out-of-scope-services.html)
- [AWS Certification policies — after testing (délai des résultats)](https://aws.amazon.com/certification/policies/after-testing)

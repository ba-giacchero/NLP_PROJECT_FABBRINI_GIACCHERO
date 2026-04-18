# NLP Project - Passation et reprise

## Objet du projet
Ce projet réalise une classification binaire de registres poétiques:
- romantique
- tragique

Le notebook principal est:
- final_project_nlp.ipynb

Notebook complémentaire:
- Final_Project_Sujet.ipynb

Dataset utilisé:
- PoetryFoundationData.csv

## Important: fichiers absents du dépôt
Le dépôt ignore volontairement les artefacts lourds de training (via .gitignore), en particulier:
- bert_poetry_outputs/
- .ipynb_checkpoints/
- *.pt
- *.bin
- *.safetensors
- *.pth

Conséquence:
- Les checkpoints du Transformer ne sont pas fournis.
- Ce n'est pas bloquant: ils se régénèrent automatiquement en relançant l'entraînement.

## Pré-requis pour relancer le projet
- Python 3.10+ (idéalement 3.11)
- Jupyter (ou VS Code Notebook)

Packages Python requis:
- numpy
- pandas
- scikit-learn
- spacy
- matplotlib
- seaborn
- datasets
- transformers
- torch
- accelerate

Exemple d'installation:
- pip install numpy pandas scikit-learn spacy matplotlib seaborn datasets transformers torch accelerate

Modèle spaCy (si nécessaire):
- python -m spacy download fr_core_news_sm

## Ordre d'exécution recommandé
Exécuter les cellules dans l'ordre, du haut vers le bas.

1. Chargement des dépendances et du dataset (Étape 2)
2. Split train/dev/test
3. Prétraitement comparatif
4. Analyse linguistique (Étape 3)
5. Baseline TF-IDF + Logistic Regression (Étape 4.1)
6. Transformer (Étape 4.2)

## Paramètre Transformer
Dans la cellule Transformer:
- RUN_TRANSFORMER = True lance le fine-tuning (plus long)
- RUN_TRANSFORMER = False saute l'entraînement lourd

## Résultats de référence attendus
Ces ordres de grandeur permettent de vérifier que l'exécution est correcte:

Baseline (TF-IDF + LogReg):
- Test Accuracy ≈ 0.746
- Test F1 weighted ≈ 0.742

Transformer:
- Test Accuracy ≈ 0.798
- Test F1 weighted ≈ 0.794

Interprétation:
- Gain d'environ +5 points (Accuracy et F1 weighted)
- Réduction relative de l'erreur d'environ 20%

## Warnings courants (normaux)
- warning pin_memory sans GPU: non bloquant sur CPU
- warning LF/CRLF sous Windows: non bloquant
- fallback dev metrics (callback bug Trainer/evaluate): déjà géré dans le notebook

## Ce qui doit être versionné
À garder dans Git:
- final_project_nlp.ipynb
- Final_Project_Sujet.ipynb
- PoetryFoundationData.csv (si politique de partage autorisée)
- README.md

À ne pas versionner:
- checkpoints et artefacts de training lourds
- dossiers de cache notebook

## Recommandation pour la poursuite
Pour poursuivre proprement:
1. Relancer le notebook dans l'ordre
2. Vérifier les métriques baseline
3. Lancer (ou relancer) le Transformer si besoin de reproduction complète
4. Mettre à jour l'interprétation finale avec les scores obtenus

# Spam Detection NLP

![Python](https://img.shields.io/badge/python-3.10-blue)
![TensorFlow](https://img.shields.io/badge/tensorflow-2.x-orange)
![Transformers](https://img.shields.io/badge/transformers-BERT-lightgrey)


## Description

Ce projet implémente un système de détection de spam pour emails utilisant **NLP (Natural Language Processing)**.  
Il compare plusieurs approches de modélisation :  

1. **RNN (Recurrent Neural Network)**
2. **LSTM avec mécanisme d’attention**
3. **Transformers (BERT)**

Le pipeline complet comprend :

- Chargement et inspection des données
- Prétraitement et nettoyage des messages
- Tokenization et encodage
- Modélisation avec différentes architectures
- Évaluation et comparaison des modèles

---

## Dataset

Le dataset utilisé est un CSV d’emails contenant :

- `label` : `ham` ou `spam`  
- `message` : contenu du message  

Après nettoyage, seules les colonnes `clean_text` et `label` sont conservées.

**Shape initiale :** `(5572, 2)`  
**Shape après suppression des doublons :** `(5172, 2)`

---

## Prétraitement

- Suppression des doublons
- Nettoyage du texte (minuscules, suppression des caractères spéciaux, tokenization, lemmatisation)
- Suppression des stopwords
- Encodage des labels (`ham` → 0, `spam` → 1)
- Transformation en séquences pour RNN/LSTM avec padding pour uniformiser les longueurs

---

## Modélisation

### 1. RNN
- **Architecture :**
  - Embedding Layer
  - SimpleRNN (64 unités)
  - Dropout (0.5)
  - Dense (sigmoid)
- **Résultats :**
  - Accuracy : 96 %
  - Précision Ham : 0.98
  - Rappel Ham : 0.97
  - Précision Spam : 0.84
  - Rappel Spam : 0.88

### 2. LSTM + Attention
- **Architecture :**
  - Embedding Layer
  - LSTM (64 unités, return_sequences=True)
  - Attention
  - Flatten → Dropout (0.5)
  - Dense (sigmoid)
- **Résultats :**
  - Accuracy : 98 %
  - Précision Ham : 0.99
  - Rappel Ham : 0.99
  - Précision Spam : 0.94
  - Rappel Spam : 0.92

### 3. Transformers (BERT)
- **Architecture :**
  - `bert-base-uncased` pour la classification
  - Tokenizer BERT
  - Fine-tuning sur le dataset
- **Résultats :**
  - Accuracy : 99 %
  - Précision Ham : 0.99
  - Rappel Ham : 1.00
  - Précision Spam : 0.98
  - Rappel Spam : 0.93

**Conclusion :** BERT offre la meilleure performance globale et une excellente détection des spams tout en conservant une haute précision pour les emails légitimes.

---

## Installation

```bash
# Cloner le dépôt
git clone https://github.com/votre-utilisateur/spam-detection-nlp.git
cd spam-detection-nlp

# Créer un environnement
python -m venv venv
source venv/bin/activate  # Linux/macOS
venv\Scripts\activate     # Windows

# Installer les dépendances
pip install -r requirements.txt
```
## Usage

**1.** Placer le fichier spam.csv dans le dossier du projet

**2.** Lancer le notebook ou script Python

**3.** Le pipeline effectuera :

    - Prétraitement

    - Entraînement du modèle (RNN, LSTM ou BERT)

    - Évaluation et visualisation des résultats

## Visualisations

 - Matrice de confusion annotée pour chaque modèle

 - Scores d’attention pour LSTM + Attention

 - Comparaison des métriques RNN vs LSTM vs BERT
## 🧑‍💻 Author

**Salima Qritel**

* GitHub: [@salima-qritel](https://github.com/salima-qritel)

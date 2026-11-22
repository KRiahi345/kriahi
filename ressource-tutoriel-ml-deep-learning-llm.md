---
layout: page
title: "Tutoriel Machine Learning, Deep Learning et LLM"
permalink: /ressources/tutoriel-ml-deep-learning-llm/
render_with_liquid: false
---

<p class="eyebrow">MACHINE LEARNING · DOCUMENT DE RÉFÉRENCE</p>
<p>Cette page reprend le contenu du document de référence, dans son ordre d’origine. Les exemples fournis dans le document sont conservés avec les explications correspondantes.</p>
<p class="source-filename">Source : Tutoriel_complet_Machine_Learning_Deep_Learning_LLM.docx</p>
<div class="source-document">
<h2>Tutoriel complet : Machine Learning, Deep Learning, ANN et LLM</h2>
<p>Classification des algorithmes, fonctionnement, fonctions mathématiques, exemples et cas d’utilisation.</p>
<h2>1. Cartographie générale de l’intelligence artificielle</h2>
<p>Intelligence artificielle (AI) → Machine Learning (ML) → Deep Learning (DL) → réseaux de neurones profonds → Transformers et LLM. Les réseaux de neurones artificiels (ANN) sont une famille de modèles ; les réseaux profonds relèvent du Deep Learning.</p>
<h2>2. Les trois grandes catégories du Machine Learning</h2>
<div class="table-scroll"><table><tr><td><p>Approche</p></td><td><p>Principe</p></td><td><p>Exemple</p></td></tr><tr><td><p>Supervisé</p></td><td><p>Données avec labels</p></td><td><p>Prédire le churn</p></td></tr><tr><td><p>Non supervisé</p></td><td><p>Données sans labels</p></td><td><p>Segmenter les clients</p></td></tr><tr><td><p>Renforcement</p></td><td><p>Apprentissage par récompenses</p></td><td><p>Robot autonome</p></td></tr></table></div>
<h2>2.1 Classification des algorithmes</h2>
<div class="table-scroll"><table><tr><td><p>Famille</p></td><td><p>Algorithmes</p></td><td><p>Objectif</p></td></tr><tr><td><p>Régression</p></td><td><p>Linear, Ridge, Lasso</p></td><td><p>Prédire une valeur</p></td></tr><tr><td><p>Classification</p></td><td><p>Logistic, SVM, KNN, Naive Bayes</p></td><td><p>Prédire une classe</p></td></tr><tr><td><p>Arbres et ensembles</p></td><td><p>Decision Tree, Random Forest, XGBoost</p></td><td><p>Prédire à partir de règles</p></td></tr><tr><td><p>Clustering</p></td><td><p>K-Means, DBSCAN, GMM</p></td><td><p>Identifier des groupes</p></td></tr><tr><td><p>Réduction dimensionnelle</p></td><td><p>PCA, t-SNE, UMAP</p></td><td><p>Réduire les variables</p></td></tr><tr><td><p>Deep Learning</p></td><td><p>ANN, CNN, RNN, LSTM</p></td><td><p>Apprendre des représentations</p></td></tr><tr><td><p>Génératif</p></td><td><p>GAN, VAE, Transformers</p></td><td><p>Générer des données</p></td></tr><tr><td><p>Renforcement</p></td><td><p>Q-Learning, PPO</p></td><td><p>Apprendre une stratégie</p></td></tr></table></div>
<h2>3. Fonctions mathématiques fondamentales</h2>
<h3>3.1 Fonction linéaire</h3>
<p>f(x) = ax + b</p>
<p>Exemple : Prix = 2 000 × Surface + 15 000. Pour 50 m² : 115 000.</p>
<h3>3.2 Fonctions de coût</h3>
<p>MSE = (1/n) Σᵢ (yᵢ − ŷᵢ)²</p>
<p>MAE = (1/n) Σᵢ |yᵢ − ŷᵢ|</p>
<p>Binary Cross-Entropy = −(1/n) Σᵢ [yᵢ ln(pᵢ) + (1−yᵢ) ln(1−pᵢ)]</p>
<p>MSE pénalise fortement les grandes erreurs ; MAE est moins sensible aux valeurs extrêmes ; la cross-entropy évalue les probabilités prédites.</p>
<h3>3.3 Descente de gradient</h3>
<p>θₜ₊₁ = θₜ − α∇J(θₜ)</p>
<p>θ : paramètres ; α : learning rate ; ∇J : gradient. Variantes : Batch, SGD, Mini-batch, Momentum, RMSProp et Adam.</p>
<h3>3.4 Fonctions d’activation</h3>
<div class="table-scroll"><table><tr><td><p>Fonction</p></td><td><p>Formule</p></td><td><p>Usage</p></td></tr><tr><td><p>Sigmoid</p></td><td><p>1/(1+e⁻ˣ)</p></td><td><p>Classification binaire</p></td></tr><tr><td><p>Tanh</p></td><td><p>tanh(x)</p></td><td><p>Réseaux récurrents</p></td></tr><tr><td><p>ReLU</p></td><td><p>max(0,x)</p></td><td><p>Couches cachées</p></td></tr><tr><td><p>Leaky ReLU</p></td><td><p>max(0,01x,x)</p></td><td><p>Éviter neurones inactifs</p></td></tr><tr><td><p>Softmax</p></td><td><p>eᶻⁱ / Σⱼeᶻʲ</p></td><td><p>Multiclasse</p></td></tr><tr><td><p>GELU</p></td><td><p>xΦ(x)</p></td><td><p>Transformers</p></td></tr></table></div>
<h2>4. Machine Learning supervisé</h2>
<h3>4.1 Linear Regression</h3>
<p>Prédit une valeur numérique (prix, consommation, ventes).</p>
<p>ŷ = w₁x₁ + … + wₙxₙ + b</p>
<p>Minimiser J = (1/m)Σ(yᵢ−ŷᵢ)². Ridge : MSE + λΣwⱼ² ; Lasso : MSE + λΣ|wⱼ|. Elastic Net combine L1 et L2.</p>
<h3>4.2 Logistic Regression</h3>
<p>Classification binaire, par exemple spam ou churn.</p>
<p>z = wᵀx+b ; P(y=1|x) = 1/(1+e⁻ᶻ)</p>
<p>Utilise généralement Binary Cross-Entropy et un seuil de décision, par exemple 0,5.</p>
<h3>4.3 Decision Tree</h3>
<p>Arbre de règles successives, pour classification et régression.</p>
<p>Gini = 1 − Σₖpₖ² ; H = −Σₖpₖ log₂(pₖ)</p>
<p>Information Gain = H(parent) − Σⱼ(Nⱼ/N)H(enfantⱼ). En régression, réduction de variance ou MSE.</p>
<h3>4.4 Random Forest</h3>
<p>Agrège des arbres entraînés sur des échantillons bootstrap et des sous-ensembles de variables.</p>
<p>Régression : ŷ = (1/n)Σᵢ Tᵢ(x)</p>
<p>Classification : vote majoritaire. Réduit la variance par rapport à un arbre isolé.</p>
<h3>4.5 Gradient Boosting / XGBoost / LightGBM</h3>
<p>Arbres ajoutés successivement pour corriger les erreurs.</p>
<p>Fₘ(x) = F₀(x) + Σₘ ηhₘ(x)</p>
<p>XGBoost exploite gradient, Hessienne et régularisation ; LightGBM favorise la rapidité ; CatBoost gère les catégories.</p>
<h3>4.6 K-Nearest Neighbors (KNN)</h3>
<p>Classe une observation selon ses K voisins les plus proches.</p>
<p>d(x,y) = √[Σᵢ(xᵢ−yᵢ)²]</p>
<p>Vote majoritaire pour classification ; moyenne pour régression. Normaliser les variables.</p>
<h3>4.7 Support Vector Machine (SVM)</h3>
<p>Trouve un hyperplan séparateur à marge maximale.</p>
<p>wᵀx+b=0 ; min ½||w||² + CΣξᵢ</p>
<p>Contraintes : yᵢ(wᵀxᵢ+b) ≥ 1−ξᵢ. Noyau RBF : K(x,x′)=exp(−γ||x−x′||²).</p>
<h3>4.8 Naive Bayes</h3>
<p>Classification probabiliste avec indépendance conditionnelle des variables.</p>
<p>P(A|B)=P(B|A)P(A)/P(B)</p>
<p>P(C|X) ∝ P(C)∏ᵢP(xᵢ|C). Variantes Gaussian, Multinomial, Bernoulli.</p>
<h2>5. Machine Learning non supervisé</h2>
<h3>5.1 K-Means</h3>
<p>Choisir K centroïdes ; affecter chaque point au plus proche ; recalculer les centroïdes ; itérer jusqu’à convergence.</p>
<p>J = Σₖ Σₓᵢ∈Cₖ ||xᵢ−μₖ||²</p>
<p>μₖ = (1/|Cₖ|) Σₓᵢ∈Cₖ xᵢ</p>
<p>K se choisit notamment avec la méthode du coude (Elbow). Limites : K fixé, sensibilité aux outliers et aux formes non convexes.</p>
<h3>5.2 DBSCAN</h3>
<p>Clustering fondé sur la densité. Paramètres : ε (rayon) et MinPts (nombre minimum de points). Types : core, border et noise.</p>
<p>Nε(p) = {q ∈ D : d(p,q) ≤ ε} ; point central si |Nε(p)| ≥ MinPts</p>
<p>Détecte des clusters de formes complexes et des points isolés, sans fixer le nombre de groupes.</p>
<h3>5.3 K-Means versus DBSCAN</h3>
<div class="table-scroll"><table><tr><td><p>Critère</p></td><td><p>K-Means</p></td><td><p>DBSCAN</p></td></tr><tr><td><p>Nombre de clusters</p></td><td><p>K imposé</p></td><td><p>Automatique</p></td></tr><tr><td><p>Forme</p></td><td><p>Plutôt convexe</p></td><td><p>Arbitraire</p></td></tr><tr><td><p>Outliers</p></td><td><p>Sensible</p></td><td><p>Bruit identifié</p></td></tr><tr><td><p>Paramètres</p></td><td><p>K</p></td><td><p>ε, MinPts</p></td></tr><tr><td><p>Centroïdes</p></td><td><p>Oui</p></td><td><p>Non</p></td></tr></table></div>
<p>Autres méthodes : Hierarchical Clustering, GMM, Mean Shift, OPTICS, Spectral Clustering.</p>
<h3>5.4 PCA</h3>
<p>Réduit la dimension en conservant autant que possible la variance.</p>
<p>Xc = X − X̄ ; Σ = XcᵀXc/(n−1) ; Σv = λv ; Z = XcW</p>
<p>Étapes : centrer, calculer la covariance, trouver les vecteurs propres, sélectionner les composantes et projeter.</p>
<h2>6. ANN – Réseaux de neurones artificiels</h2>
<p>Architecture : couche d’entrée, couches cachées et couche de sortie. Chaque neurone réalise une combinaison pondérée suivie d’une activation.</p>
<p>z = Σᵢ wᵢxᵢ + b ; a = f(z)</p>
<p>Exemple : x₁=2, x₂=3, w₁=0,5, w₂=0,8, b=0,1 → z=3,5 ; ReLU(z)=3,5.</p>
<h3>6.2 Forward Propagation</h3>
<p>Z⁽ˡ⁾ = W⁽ˡ⁾A⁽ˡ⁻¹⁾ + b⁽ˡ⁾ ; A⁽ˡ⁾ = f(Z⁽ˡ⁾)</p>
<h3>6.3 Backpropagation</h3>
<p>∂L/∂w = (∂L/∂a)(∂a/∂z)(∂z/∂w)</p>
<p>wₜ₊₁ = wₜ − α ∂L/∂w</p>
<p>Calcul des gradients par règle de dérivation en chaîne, puis mise à jour des poids.</p>
<h3>6.4 ANN et Deep Learning</h3>
<p>Un ANN peut être peu profond ; un réseau à plusieurs couches cachées relève généralement du Deep Learning.</p>
<h2>7. Architectures de Deep Learning</h2>
<h3>7.1 CNN</h3>
<p>Réseau convolutif pour images : convolution, activation, pooling, classification.</p>
<p>Y(i,j) = ΣₘΣₙ X(i−m,j−n)K(m,n)</p>
<p>MaxPooling : Y(i,j) = max₍ₘ,ₙ₎∈Rᵢⱼ X(m,n)</p>
<h3>7.2 RNN</h3>
<p>Réseau récurrent pour séquences et séries temporelles. Limites : vanishing et exploding gradients.</p>
<p>hₜ = f(Wₓxₜ + Wₕhₜ₋₁ + b) ; yₜ = g(Wᵧhₜ+bᵧ)</p>
<h3>7.3 LSTM</h3>
<p>Mémoire interne avec Forget Gate, Input Gate et Output Gate.</p>
<p>fₜ = σ(Wf[hₜ₋₁,xₜ]+bf)</p>
<p>iₜ = σ(Wi[hₜ₋₁,xₜ]+bi)</p>
<p>C̃ₜ = tanh(Wc[hₜ₋₁,xₜ]+bc)</p>
<p>Cₜ = fₜ ⊙ Cₜ₋₁ + iₜ ⊙ C̃ₜ</p>
<p>oₜ = σ(Wo[hₜ₋₁,xₜ]+bo) ; hₜ = oₜ ⊙ tanh(Cₜ)</p>
<h3>7.4 GRU</h3>
<p>Réseau récurrent avec deux portes : Update et Reset ; généralement plus simple que LSTM.</p>
<h3>7.5 Autoencoder</h3>
<p>Encoder → représentation latente → Decoder. Utilisé pour réduction de dimension, compression et détection d’anomalies.</p>
<p>z = fθ(x) ; x̂ = gφ(z) ; L = ||x−x̂||²</p>
<h3>7.6 GAN</h3>
<p>Deux réseaux adversariaux : Generator et Discriminator.</p>
<p>minG maxD V(D,G) = Eₓ[log D(x)] + E𝓏[log(1−D(G(z)))].</p>
<h2>8. Transformers</h2>
<p>Architecture fondée sur l’attention, présentée en 2017. Embeddings, information positionnelle, attention, FFN.</p>
<h3>8.1 Embeddings</h3>
<p>Embedding(token) = [e₁,e₂,…,e𝑑]</p>
<h3>8.2 Positional Encoding</h3>
<p>PE(pos,2i) = sin(pos/10000^(2i/d))</p>
<p>PE(pos,2i+1) = cos(pos/10000^(2i/d))</p>
<p>D’autres modèles utilisent des encodages positionnels appris ou relatifs (RoPE).</p>
<h3>8.3 Self-Attention</h3>
<p>Q=XWQ ; K=XWK ; V=XWV</p>
<p>Attention(Q,K,V) = Softmax(QKᵀ/√dₖ)V</p>
<p>Q : Query ; K : Key ; V : Value. Scores → normalisation → Softmax → somme pondérée des Values.</p>
<h3>8.4 Multi-Head Attention</h3>
<p>MultiHead(Q,K,V) = Concat(head₁,…,headₕ)WO</p>
<p>headᵢ = Attention(QWᵢQ, KWᵢK, VWᵢV)</p>
<h3>8.5 Feed Forward Network</h3>
<p>FFN(x) = W₂σ(W₁x+b₁)+b₂</p>
<h3>8.6 Encoder et Decoder</h3>
<div class="table-scroll"><table><tr><td><p>Architecture</p></td><td><p>Rôle</p></td><td><p>Exemples</p></td></tr><tr><td><p>Encoder-only</p></td><td><p>Représenter et comprendre</p></td><td><p>BERT</p></td></tr><tr><td><p>Decoder-only</p></td><td><p>Générer</p></td><td><p>GPT, Llama</p></td></tr><tr><td><p>Encoder-Decoder</p></td><td><p>Transformer des séquences</p></td><td><p>T5</p></td></tr></table></div>
<h2>9. Large Language Models (LLM)</h2>
<p>Chaîne de traitement : Tokenization → Embedding → Position → Transformer → Logits → Softmax → Génération.</p>
<h3>9.1 Next Token Prediction</h3>
<p>P(tokenᵢ) = eᶻⁱ / Σⱼeᶻʲ</p>
<p>L = −Σᵢ log P(xᵢ | x₁,…,xᵢ₋₁)</p>
<h3>9.2 Temperature</h3>
<p>Pᵢ = Softmax(zᵢ/T)</p>
<p>Faible température : prédictions plus concentrées ; forte température : distribution plus diversifiée.</p>
<h3>9.3 Fine-Tuning et LoRA</h3>
<p>Full Fine-Tuning modifie tous les poids. LoRA apprend une correction de faible rang. QLoRA combine LoRA et quantification.</p>
<p>W′ = W + ΔW ; ΔW = BA</p>
<h3>9.4 RAG</h3>
<p>Documents → chunks → embeddings → base vectorielle → question → recherche → contexte → LLM → réponse.</p>
<p>CosineSimilarity(A,B) = (A·B)/(||A|| ||B||)</p>
<div class="table-scroll"><table><tr><td><p>RAG</p></td><td><p>Fine-Tuning</p></td></tr><tr><td><p>Récupère des informations externes</p></td><td><p>Adapte les paramètres</p></td></tr><tr><td><p>Documents actualisables</p></td><td><p>Nécessite un entraînement</p></td></tr><tr><td><p>Sources potentiellement citées</p></td><td><p>Connaissance moins traçable</p></td></tr></table></div>
<h2>10. GNN et GraphRAG</h2>
<p>Les Graph Neural Networks apprennent sur des graphes (nœuds, arêtes, attributs) ; GraphRAG associe recherche et graphe de connaissances.</p>
<p>hᵥ⁽ˡ⁺¹⁾ = σ(W⁽ˡ⁾ AGG{hᵤ⁽ˡ⁾ : u∈N(v)})</p>
<p>Architectures : GCN, GAT, GraphSAGE. Exemple GraphRAG : Référentiel client → API Client → CRM → Facturation → Portail client.</p>
<h2>11. Reinforcement Learning</h2>
<p>Un agent interagit avec un environnement : état, action, récompense et politique.</p>
<h3>11.1 Q-Learning</h3>
<p>Q(s,a) ← Q(s,a) + α[r + γ maxₐ′ Q(s′,a′) − Q(s,a)]</p>
<p>Autres algorithmes : DQN, Policy Gradient, Actor-Critic, PPO.</p>
<h2>12. Tableau récapitulatif des fonctions mathématiques</h2>
<div class="table-scroll"><table><tr><td><p>Fonction</p></td><td><p>Algorithmes</p></td><td><p>Rôle</p></td></tr><tr><td><p>ax+b</p></td><td><p>Régression</p></td><td><p>Relation linéaire</p></td></tr><tr><td><p>Sigmoid</p></td><td><p>Logistic, ANN</p></td><td><p>Probabilité binaire</p></td></tr><tr><td><p>Softmax</p></td><td><p>ANN, LLM</p></td><td><p>Distribution multiclasse</p></td></tr><tr><td><p>MSE / MAE</p></td><td><p>Régression</p></td><td><p>Erreur</p></td></tr><tr><td><p>Cross-Entropy</p></td><td><p>Classification, LLM</p></td><td><p>Erreur probabiliste</p></td></tr><tr><td><p>Gradient Descent</p></td><td><p>ML, DL</p></td><td><p>Optimisation</p></td></tr><tr><td><p>ReLU / GELU</p></td><td><p>ANN, Transformers</p></td><td><p>Non-linéarité</p></td></tr><tr><td><p>Gini / Entropy</p></td><td><p>Arbres</p></td><td><p>Impureté</p></td></tr><tr><td><p>Distance euclidienne</p></td><td><p>KNN, K-Means, DBSCAN</p></td><td><p>Proximité</p></td></tr><tr><td><p>Cosine Similarity</p></td><td><p>RAG</p></td><td><p>Similarité</p></td></tr><tr><td><p>Covariance / valeurs propres</p></td><td><p>PCA</p></td><td><p>Axes principaux</p></td></tr><tr><td><p>Convolution</p></td><td><p>CNN</p></td><td><p>Extraction de motifs</p></td></tr><tr><td><p>Chain Rule</p></td><td><p>ANN</p></td><td><p>Rétropropagation</p></td></tr><tr><td><p>Attention</p></td><td><p>Transformers</p></td><td><p>Pondération des tokens</p></td></tr><tr><td><p>Bayes</p></td><td><p>Naive Bayes</p></td><td><p>Probabilités</p></td></tr><tr><td><p>Q-Learning</p></td><td><p>RL</p></td><td><p>Décisions</p></td></tr></table></div>
<h2>13. Quel algorithme utiliser ?</h2>
<div class="table-scroll"><table><tr><td><p>Besoin</p></td><td><p>Algorithmes</p></td></tr><tr><td><p>Prédire un prix</p></td><td><p>Linear Regression</p></td></tr><tr><td><p>Churn</p></td><td><p>Logistic Regression, XGBoost</p></td></tr><tr><td><p>Fraude</p></td><td><p>Random Forest, XGBoost, GNN</p></td></tr><tr><td><p>Segmentation</p></td><td><p>K-Means, DBSCAN</p></td></tr><tr><td><p>Anomalies</p></td><td><p>DBSCAN, Isolation Forest, Autoencoder</p></td></tr><tr><td><p>Images</p></td><td><p>CNN, Vision Transformers</p></td></tr><tr><td><p>Séries temporelles</p></td><td><p>XGBoost, LSTM, Transformers</p></td></tr><tr><td><p>Texte</p></td><td><p>Naive Bayes, BERT</p></td></tr><tr><td><p>Génération</p></td><td><p>LLM</p></td></tr><tr><td><p>Documents</p></td><td><p>RAG + LLM</p></td></tr><tr><td><p>Relations</p></td><td><p>GNN, GraphRAG</p></td></tr><tr><td><p>Décisions</p></td><td><p>Reinforcement Learning</p></td></tr></table></div>
<h2>14. Étapes d’un projet Machine Learning</h2>
<div class="table-scroll"><table><tr><td><p>Étape</p></td><td><p>Description</p></td></tr><tr><td><p>1</p></td><td><p>Business Understanding</p></td></tr><tr><td><p>2</p></td><td><p>Data Collection</p></td></tr><tr><td><p>3</p></td><td><p>Data Preparation</p></td></tr><tr><td><p>4</p></td><td><p>Feature Engineering</p></td></tr><tr><td><p>5</p></td><td><p>Model Selection</p></td></tr><tr><td><p>6</p></td><td><p>Training</p></td></tr><tr><td><p>7</p></td><td><p>Evaluation</p></td></tr><tr><td><p>8</p></td><td><p>Deployment</p></td></tr><tr><td><p>9</p></td><td><p>Monitoring</p></td></tr></table></div>
<h3>14.1 Métriques d’évaluation</h3>
<p>Accuracy = (TP+TN)/(TP+TN+FP+FN)</p>
<p>Precision = TP/(TP+FP)</p>
<p>Recall = TP/(TP+FN)</p>
<p>F1 = 2×Precision×Recall/(Precision+Recall)</p>
<p>Classification : Accuracy, Precision, Recall, F1, AUC-ROC. Régression : MAE, MSE, RMSE, R². Clustering : Silhouette, Davies-Bouldin, Calinski-Harabasz.</p>
<h2>15. Parcours d’apprentissage recommandé</h2>
<p class="source-list-item">Mathématiques : algèbre linéaire, statistiques, probabilités, gradients</p>
<p class="source-list-item">ML supervisé : régressions, arbres, ensembles, KNN, SVM</p>
<p class="source-list-item">ML non supervisé : K-Means, DBSCAN, PCA, GMM</p>
<p class="source-list-item">ANN : propagation, backpropagation, Adam, activations</p>
<p class="source-list-item">Deep Learning : CNN, RNN, LSTM, GRU, GAN</p>
<p class="source-list-item">GenAI : Transformers, attention, embeddings, RAG, LoRA</p>
<p class="source-list-item">Avancé : GNN, GraphRAG, MLOps, LLMOps</p>
<h2>16. Quiz de révision</h2>
<p>1. Quel algorithme segmente sans connaître K et identifie le bruit ?<br>
Réponse : DBSCAN</p>
<p>2. Quelle fonction transforme le score logistique en probabilité ?<br>
Réponse : Sigmoid</p>
<p>3. Quelle technique calcule les gradients dans un ANN ?<br>
Réponse : Backpropagation</p>
<p>4. Quelle formule est au cœur de la Self-Attention ?<br>
Réponse : Softmax(QKᵀ/√dₖ)V</p>
<p>5. Différence principale entre RAG et Fine-Tuning ?<br>
Réponse : RAG récupère du contexte externe ; Fine-Tuning adapte les poids.</p>
<p>6. Quel algorithme minimise la somme des distances aux centroïdes ?<br>
Réponse : K-Means</p>
<p>Conseil : maîtriser les distances pour le clustering, les probabilités pour la classification, les gradients pour les réseaux de neurones et l’attention pour les Transformers.</p>

<section class="resource-illustrations"><h2>Schémas et illustrations</h2>
<figure class="resource-figure"><img src="/assets/images/resources/llm-finetuning-lora.jpg" alt="Schéma comparant le fine-tuning complet, LoRA et QLoRA." loading="lazy"><figcaption>Schéma comparant le fine-tuning complet, LoRA et QLoRA.</figcaption></figure>
<figure class="resource-figure"><img src="/assets/images/resources/deep-learning-formulas.jpg" alt="Formules de référence en deep learning : neurone, activations, perte, rétropropagation et descente de gradient." loading="lazy"><figcaption>Formules de référence en deep learning : neurone, activations, perte, rétropropagation et descente de gradient.</figcaption></figure>
</section>
</div>

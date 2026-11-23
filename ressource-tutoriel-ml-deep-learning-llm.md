---
layout: page
title: "Deep Learning: ANN et LLM"
permalink: /ressources/tutoriel-ml-deep-learning-llm/
render_with_liquid: false
---

<div class="source-document">
<h2>1. Architectures de Deep Learning</h2>
<h3>1.1 CNN</h3>
<p>Réseau convolutif pour images : convolution, activation, pooling, classification.</p>
<p>Y(i,j) = ΣₘΣₙ X(i−m,j−n)K(m,n)</p>
<p>MaxPooling : Y(i,j) = max₍ₘ,ₙ₎∈Rᵢⱼ X(m,n)</p>
<h3>1.2 RNN</h3>
<p>Réseau récurrent pour séquences et séries temporelles. Limites : vanishing et exploding gradients.</p>
<p>hₜ = f(Wₓxₜ + Wₕhₜ₋₁ + b) ; yₜ = g(Wᵧhₜ+bᵧ)</p>
<h3>1.3 LSTM</h3>
<p>Mémoire interne avec Forget Gate, Input Gate et Output Gate.</p>
<p>fₜ = σ(Wf[hₜ₋₁,xₜ]+bf)</p>
<p>iₜ = σ(Wi[hₜ₋₁,xₜ]+bi)</p>
<p>C̃ₜ = tanh(Wc[hₜ₋₁,xₜ]+bc)</p>
<p>Cₜ = fₜ ⊙ Cₜ₋₁ + iₜ ⊙ C̃ₜ</p>
<p>oₜ = σ(Wo[hₜ₋₁,xₜ]+bo) ; hₜ = oₜ ⊙ tanh(Cₜ)</p>
<h3>1.4 GRU</h3>
<p>Réseau récurrent avec deux portes : Update et Reset ; généralement plus simple que LSTM.</p>
<h3>1.5 Autoencoder</h3>
<p>Encoder → représentation latente → Decoder. Utilisé pour réduction de dimension, compression et détection d’anomalies.</p>
<p>z = fθ(x) ; x̂ = gφ(z) ; L = ||x−x̂||²</p>
<h3>1.6 GAN</h3>
<p>Deux réseaux adversariaux : Generator et Discriminator.</p>
<p>minG maxD V(D,G) = Eₓ[log D(x)] + E𝓏[log(1−D(G(z)))].</p>
<h2>2. Transformers</h2>
<p>Architecture fondée sur l’attention, présentée en 2017. Embeddings, information positionnelle, attention, FFN.</p>
<h3>2.1 Embeddings</h3>
<p>Embedding(token) = [e₁,e₂,…,e𝑑]</p>
<h3>2.2 Positional Encoding</h3>
<p>PE(pos,2i) = sin(pos/10000^(2i/d))</p>
<p>PE(pos,2i+1) = cos(pos/10000^(2i/d))</p>
<p>D’autres modèles utilisent des encodages positionnels appris ou relatifs (RoPE).</p>
<h3>2.3 Self-Attention</h3>
<p>Q=XWQ ; K=XWK ; V=XWV</p>
<p>Attention(Q,K,V) = Softmax(QKᵀ/√dₖ)V</p>
<p>Q : Query ; K : Key ; V : Value. Scores → normalisation → Softmax → somme pondérée des Values.</p>
<h3>2.4 Multi-Head Attention</h3>
<p>MultiHead(Q,K,V) = Concat(head₁,…,headₕ)WO</p>
<p>headᵢ = Attention(QWᵢQ, KWᵢK, VWᵢV)</p>
<h3>2.5 Feed Forward Network</h3>
<p>FFN(x) = W₂σ(W₁x+b₁)+b₂</p>
<h3>2.6 Encoder et Decoder</h3>
<div class="table-scroll"><table><tr><td><p>Architecture</p></td><td><p>Rôle</p></td><td><p>Exemples</p></td></tr><tr><td><p>Encoder-only</p></td><td><p>Représenter et comprendre</p></td><td><p>BERT</p></td></tr><tr><td><p>Decoder-only</p></td><td><p>Générer</p></td><td><p>GPT, Llama</p></td></tr><tr><td><p>Encoder-Decoder</p></td><td><p>Transformer des séquences</p></td><td><p>T5</p></td></tr></table></div>
<h2>3. Large Language Models (LLM)</h2>
<p>Chaîne de traitement : Tokenization → Embedding → Position → Transformer → Logits → Softmax → Génération.</p>
<h3>3.1 Next Token Prediction</h3>
<p>P(tokenᵢ) = eᶻⁱ / Σⱼeᶻʲ</p>
<p>L = −Σᵢ log P(xᵢ | x₁,…,xᵢ₋₁)</p>
<h3>3.2 Temperature</h3>
<p>Pᵢ = Softmax(zᵢ/T)</p>
<p>Faible température : prédictions plus concentrées ; forte température : distribution plus diversifiée.</p>
<h3>3.3 Fine-Tuning et LoRA</h3>
<p>Full Fine-Tuning modifie tous les poids. LoRA apprend une correction de faible rang. QLoRA combine LoRA et quantification.</p>
<p>W′ = W + ΔW ; ΔW = BA</p>
<h3>3.4 RAG</h3>
<p>Documents → chunks → embeddings → base vectorielle → question → recherche → contexte → LLM → réponse.</p>
<p>CosineSimilarity(A,B) = (A·B)/(||A|| ||B||)</p>
<div class="table-scroll"><table><tr><td><p>RAG</p></td><td><p>Fine-Tuning</p></td></tr><tr><td><p>Récupère des informations externes</p></td><td><p>Adapte les paramètres</p></td></tr><tr><td><p>Documents actualisables</p></td><td><p>Nécessite un entraînement</p></td></tr><tr><td><p>Sources potentiellement citées</p></td><td><p>Connaissance moins traçable</p></td></tr></table></div>
<h2>4. GNN et GraphRAG</h2>
<p>Les Graph Neural Networks apprennent sur des graphes (nœuds, arêtes, attributs) ; GraphRAG associe recherche et graphe de connaissances.</p>
<p>hᵥ⁽ˡ⁺¹⁾ = σ(W⁽ˡ⁾ AGG{hᵤ⁽ˡ⁾ : u∈N(v)})</p>
<p>Architectures : GCN, GAT, GraphSAGE. Exemple GraphRAG : Référentiel client → API Client → CRM → Facturation → Portail client.</p>
<h2>5. Reinforcement Learning</h2>
<p>Un agent interagit avec un environnement : état, action, récompense et politique.</p>
<h3>5.1 Q-Learning</h3>
<p>Q(s,a) ← Q(s,a) + α[r + γ maxₐ′ Q(s′,a′) − Q(s,a)]</p>
<p>Autres algorithmes : DQN, Policy Gradient, Actor-Critic, PPO.</p>
<h2>6. Tableau récapitulatif des fonctions mathématiques</h2>
<div class="table-scroll"><table><tr><td><p>Fonction</p></td><td><p>Algorithmes</p></td><td><p>Rôle</p></td></tr><tr><td><p>ax+b</p></td><td><p>Régression</p></td><td><p>Relation linéaire</p></td></tr><tr><td><p>Sigmoid</p></td><td><p>Logistic, ANN</p></td><td><p>Probabilité binaire</p></td></tr><tr><td><p>Softmax</p></td><td><p>ANN, LLM</p></td><td><p>Distribution multiclasse</p></td></tr><tr><td><p>MSE / MAE</p></td><td><p>Régression</p></td><td><p>Erreur</p></td></tr><tr><td><p>Cross-Entropy</p></td><td><p>Classification, LLM</p></td><td><p>Erreur probabiliste</p></td></tr><tr><td><p>Gradient Descent</p></td><td><p>ML, DL</p></td><td><p>Optimisation</p></td></tr><tr><td><p>ReLU / GELU</p></td><td><p>ANN, Transformers</p></td><td><p>Non-linéarité</p></td></tr><tr><td><p>Gini / Entropy</p></td><td><p>Arbres</p></td><td><p>Impureté</p></td></tr><tr><td><p>Distance euclidienne</p></td><td><p>KNN, K-Means, DBSCAN</p></td><td><p>Proximité</p></td></tr><tr><td><p>Cosine Similarity</p></td><td><p>RAG</p></td><td><p>Similarité</p></td></tr><tr><td><p>Covariance / valeurs propres</p></td><td><p>PCA</p></td><td><p>Axes principaux</p></td></tr><tr><td><p>Convolution</p></td><td><p>CNN</p></td><td><p>Extraction de motifs</p></td></tr><tr><td><p>Chain Rule</p></td><td><p>ANN</p></td><td><p>Rétropropagation</p></td></tr><tr><td><p>Attention</p></td><td><p>Transformers</p></td><td><p>Pondération des tokens</p></td></tr><tr><td><p>Bayes</p></td><td><p>Naive Bayes</p></td><td><p>Probabilités</p></td></tr><tr><td><p>Q-Learning</p></td><td><p>RL</p></td><td><p>Décisions</p></td></tr></table></div>
<h2>7. Quel algorithme utiliser ?</h2>
<div class="table-scroll"><table><tr><td><p>Besoin</p></td><td><p>Algorithmes</p></td></tr><tr><td><p>Prédire un prix</p></td><td><p>Linear Regression</p></td></tr><tr><td><p>Churn</p></td><td><p>Logistic Regression, XGBoost</p></td></tr><tr><td><p>Fraude</p></td><td><p>Random Forest, XGBoost, GNN</p></td></tr><tr><td><p>Segmentation</p></td><td><p>K-Means, DBSCAN</p></td></tr><tr><td><p>Anomalies</p></td><td><p>DBSCAN, Isolation Forest, Autoencoder</p></td></tr><tr><td><p>Images</p></td><td><p>CNN, Vision Transformers</p></td></tr><tr><td><p>Séries temporelles</p></td><td><p>XGBoost, LSTM, Transformers</p></td></tr><tr><td><p>Texte</p></td><td><p>Naive Bayes, BERT</p></td></tr><tr><td><p>Génération</p></td><td><p>LLM</p></td></tr><tr><td><p>Documents</p></td><td><p>RAG + LLM</p></td></tr><tr><td><p>Relations</p></td><td><p>GNN, GraphRAG</p></td></tr><tr><td><p>Décisions</p></td><td><p>Reinforcement Learning</p></td></tr></table></div>
<h2>8. Étapes d’un projet Machine Learning</h2>
<div class="table-scroll"><table><tr><td><p>Étape</p></td><td><p>Description</p></td></tr><tr><td><p>1</p></td><td><p>Business Understanding</p></td></tr><tr><td><p>2</p></td><td><p>Data Collection</p></td></tr><tr><td><p>3</p></td><td><p>Data Preparation</p></td></tr><tr><td><p>4</p></td><td><p>Feature Engineering</p></td></tr><tr><td><p>5</p></td><td><p>Model Selection</p></td></tr><tr><td><p>6</p></td><td><p>Training</p></td></tr><tr><td><p>7</p></td><td><p>Evaluation</p></td></tr><tr><td><p>8</p></td><td><p>Deployment</p></td></tr><tr><td><p>9</p></td><td><p>Monitoring</p></td></tr></table></div>
<h3>8.1 Métriques d’évaluation</h3>
<p>Accuracy = (TP+TN)/(TP+TN+FP+FN)</p>
<p>Precision = TP/(TP+FP)</p>
<p>Recall = TP/(TP+FN)</p>
<p>F1 = 2×Precision×Recall/(Precision+Recall)</p>
<p>Classification : Accuracy, Precision, Recall, F1, AUC-ROC. Régression : MAE, MSE, RMSE, R². Clustering : Silhouette, Davies-Bouldin, Calinski-Harabasz.</p>
</div>

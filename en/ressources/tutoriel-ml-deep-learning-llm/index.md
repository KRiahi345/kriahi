---
layout: page
title: "Deep Learning: ANN and LLM"
permalink: /en/ressources/tutoriel-ml-deep-learning-llm/
render_with_liquid: false
compact_title: true
lang: en
french_url: /ressources/tutoriel-ml-deep-learning-llm/
---
<div class="source-document">
<h2>1. Neural network models</h2>
<figure class="resource-figure"><img src="/assets/images/resources/deep-learning-ann-llm-overview.png" alt="Overview of Deep Learning, from ANN neural networks and Transformers to LLMs, with architectures, functions, use cases and metrics." loading="lazy"><figcaption>Overview of neural network architectures, Transformers and LLM.</figcaption></figure>
<h3>1.1 CNN</h3>
<p>Convolutional network for images: convolution, activation, pooling, classification.</p>
<p>Y(i,j) = ΣₘΣₙ X(i−m,j−n)K(m,n)</p>
<p>MaxPooling: Y(i,j) = max₍ₘ,ₙ₎∈Rᵢⱼ</p>
<h3>1.2 RNN</h3>
<p>Recurrent network for sequences and time series. Limits: vanishing and exploding gradients.</p>
<p>hₜ = f(Wₓxₜ + Wₕhₜ₋₁ + b); yₜ = g(Wᵧhₜ+bᵧ)</p>
<h3>1.3 LSTM</h3>
<p>Internal memory with Forget Gate, Input Gate and Output Gate.</p>
<p>fₜ = σ(Wf[hₜ₋₁,xₜ]+bf)</p>
<p>iₜ = σ(Wi[hₜ₋₁,xₜ]+bi)</p>
<p>C̃ₜ = tanh(Wc[hₜ₋₁,xₜ]+bc)</p>
<p>Cₜ = fₜ ⊙ Cₜ₋₁ + iₜ ⊙ C̃ₜ</p>
<p>oₜ = σ(Wo[hₜ₋₁,xₜ]+bo); hₜ = oₜ ⊙ tanh(Cₜ)</p>
<h3>1.4 GRU</h3>
<p>Recurrent network with two gates: Update and Reset; generally simpler than LSTM.</p>
<h3>1.5 Autoencoder</h3>
<p>Encode → latent representation → Decoder. Used for dimension reduction, compression and anomaly detection.</p>
<p>z = fθ(x); x̂ = gφ(z); L = ||x−x̂||²</p>
<h3>1.6 GAN</h3>
<p>Two adversarial networks: Generator and Discriminator.</p>
<p>minG maxD V(D,G) = Eₓ[log D(x)] + E𝓏[log(1−D(G(z)))].</p>
<h2>2. Transformers</h2>
<p>Attention-based architecture, presented in 2017. Embeddings, positional information, attention, FFN.</p>
<h3>2.1 Embeddings</h3>
<p>Embedding(token) = [e₁,e₂,…,e𝑑]</p>
<h3>2.2 Positional Encoding</h3>
<p>PE(pos,2i) = sin(pos/10000^(2i/d))</p>
<p>PE(pos,2i+1) = cos(pos/10000^(2i/d))</p>
<p>Other models use learned or relative positional encodings (RoPE).</p>
<h3>2.3 Self-Attention</h3>
<p>Q=XWQ ; K=XWK; V=XWV</p>
<p>Attention(Q,K,V) = Softmax(QKᵀ/√dₖ)V</p>
<p>Q: Query; K:Key; V: Value. Scores → normalization → Softmax → weighted sum of Values.</p>
<h3>2.4 Multi-Head Caution</h3>
<p>MultiHead(Q,K,V) = Concat(head₁,…,headₕ)WO</p>
<p>headᵢ = Attention(QWᵢQ, KWᵢK, VWᵢV)</p>
<h3>2.5 Feed Forward Network</h3>
<p>FFN(x) = W₂σ(W₁x+b₁)+b₂</p>
<h3>2.6 Encode and Decode</h3>
<div class="table-scroll"><table><tr><td><p>Architecture</p></td><td><p>Role</p></td><td><p>Examples</p></td></tr><tr><td><p>Encoder-only</p></td><td><p>Represent and understand</p></td><td><p>BERT</p></td></tr><tr><td><p>Decoder-only</p></td><td><p>Generate</p></td><td><p>GPT, Llama</p></td></tr><tr><td><p>Encoder-Decoder</p></td><td><p>Transform sequences</p></td><td><p>T5</p></td></tr></table></div>
<h2>3. Large Language Models (LLM)</h2>
<p>Processing chain: Tokenization → Embedding → Position → Transform → Logits → Softmax → Generation.</p>
<h3>3.1 Next Token Prediction</h3>
<p>P(tokenᵢ) = eᶻⁱ / Σⱼeᶻʲ</p>
<p>L = −Σᵢ log P(xᵢ | x₁,…,xᵢ₋₁)</p>
<h3>3.2 Temperature</h3>
<p>Pᵢ = Softmax(zᵢ/T)</p>
<p>Low temperature: more concentrated predictions; high temperature: more diversified distribution.</p>
<h3>3.3 Fine-Tuning and LoRA</h3>
<p>Full Fine-Tuning modifies all weights. LoRA learns low-rank correction. QLoRA combines LoRA and quantification.</p>
<p>W′ = W + ΔW; ΔW = BA</p>
<h3>3.4 RAG</h3>
<p>Documents → chunks → embeddings → vector base → question → search → context → LLM → answer.</p>
<p>CosineSimilarity(A,B) = (A·B)/(||A|| ||B||)</p>
<div class="table-scroll"><table><tr><td><p>RAG</p></td><td><p>Fine-Tuning</p></td></tr><tr><td><p>Retrieves external information</p></td><td><p>Adapt the settings</p></td></tr><tr><td><p>Updatable documents</p></td><td><p>Requires training</p></td></tr><tr><td><p>Potentially cited sources</p></td><td><p>Less traceable knowledge</p></td></tr></table></div>
<h2>4. GNN and GraphRAG</h2>
<p>Graph Neural Networks learn on graphs (nodes, edges, attributes); GraphRAG combines search and knowledge graph.</p>
<p>hᵥ⁽ˡ⁺¹⁾ = σ(W⁽ˡ⁾ AGG{hᵤ⁽ˡ⁾ : u∈N(v)})</p>
<p>Architectures: GCN, GAT, GraphSAGE. GraphRAG example: Customer repository → Customer API → CRM → Billing → Customer portal.</p>
<h2>5. Reinforcement Learning</h2>
<p>An agent interacts with an environment: state, action, reward and policy.</p>
<h3>5.1 Q-Learning</h3>
<p>Q(s,a) ← Q(s,a) + α[r + γ maxₐ′ Q(s′,a′) − Q(s,a)]</p>
<p>Other algorithms: DQN, Policy Gradient, Actor-Critic, PPO.</p>
<h2>6. Summary table of mathematical functions</h2>
<div class="table-scroll"><table><tr><td><p>Function</p></td><td><p>Algorithms</p></td><td><p>Role</p></td></tr><tr><td><p>ax+b</p></td><td><p>Regression</p></td><td><p>Linear relationship</p></td></tr><tr><td><p>Sigmoid</p></td><td><p>Logistics, ANN</p></td><td><p>Binary probability</p></td></tr><tr><td><p>Softmax</p></td><td><p>ANN, LLM</p></td><td><p>Multiclass distribution</p></td></tr><tr><td><p>MSE / MAE</p></td><td><p>Regression</p></td><td><p>Error</p></td></tr><tr><td><p>Cross-Entropy</p></td><td><p>Classification, LLM</p></td><td><p>Probabilistic error</p></td></tr><tr><td><p>Gradient Descent</p></td><td><p>ML, DL</p></td><td><p>Optimization</p></td></tr><tr><td><p>ReLU / GELU</p></td><td><p>ANN, Transformers</p></td><td><p>Nonlinearity</p></td></tr><tr><td><p>Gini / Entropy</p></td><td><p>Trees</p></td><td><p>Impurity</p></td></tr><tr><td><p>Euclidean distance</p></td><td><p>KNN, K-Means, DBSCAN</p></td><td><p>Proximity</p></td></tr><tr><td><p>Cosine Similarity</p></td><td><p>RAG</p></td><td><p>Similarity</p></td></tr><tr><td><p>Covariance / eigenvalues</p></td><td><p>PCA</p></td><td><p>Main axes</p></td></tr><tr><td><p>Convolution</p></td><td><p>CNN</p></td><td><p>Pattern extraction</p></td></tr><tr><td><p>Chain Rule</p></td><td><p>ANN</p></td><td><p>Backpropagation</p></td></tr><tr><td><p>Attention</p></td><td><p>Transformers</p></td><td><p>Token weighting</p></td></tr><tr><td><p>Bayes</p></td><td><p>Naive Bayes</p></td><td><p>Probabilities</p></td></tr><tr><td><p>Q-Learning</p></td><td><p>R.L.</p></td><td><p>Decisions</p></td></tr></table></div>
<h2>7. Which algorithm to use?</h2>
<div class="table-scroll"><table><tr><td><p>Need</p></td><td><p>Algorithms</p></td></tr><tr><td><p>Predict a price</p></td><td><p>Linear Regression</p></td></tr><tr><td><p>Churn</p></td><td><p>Logistic Regression, XGBoost</p></td></tr><tr><td><p>Fraud</p></td><td><p>Random Forest, XGBoost, GNN</p></td></tr><tr><td><p>Segmentation</p></td><td><p>K-Means, DBSCAN</p></td></tr><tr><td><p>Anomalies</p></td><td><p>DBSCAN, Forest Isolation, Autoencoder</p></td></tr><tr><td><p>Pictures</p></td><td><p>CNN, Vision Transformers</p></td></tr><tr><td><p>Time series</p></td><td><p>XGBoost, LSTM, Transformers</p></td></tr><tr><td><p>Text</p></td><td><p>Naive Bayes, BERT</p></td></tr><tr><td><p>Generation</p></td><td><p>LLM</p></td></tr><tr><td><p>Documents</p></td><td><p>RAG + LLM</p></td></tr><tr><td><p>Relationships</p></td><td><p>GNN, GraphRAG</p></td></tr><tr><td><p>Decisions</p></td><td><p>Reinforcement Learning</p></td></tr></table></div>
<h2>8. Stages of a Machine Learning project</h2>
<div class="table-scroll"><table><tr><td><p>Stage</p></td><td><p>Description</p></td></tr><tr><td><p>1</p></td><td><p>Business Understanding</p></td></tr><tr><td><p>2</p></td><td><p>Data Collection</p></td></tr><tr><td><p>3</p></td><td><p>Data Preparation</p></td></tr><tr><td><p>4</p></td><td><p>Feature Engineering</p></td></tr><tr><td><p>5</p></td><td><p>Model Selection</p></td></tr><tr><td><p>6</p></td><td><p>Training</p></td></tr><tr><td><p>7</p></td><td><p>Assessment</p></td></tr><tr><td><p>8</p></td><td><p>deployment</p></td></tr><tr><td><p>9</p></td><td><p>Monitoring</p></td></tr></table></div>
<h3>8.1 Evaluation Metrics</h3>
<p>Accuracy = (TP+TN)/(TP+TN+FP+FN)</p>
<p>Precision = TP/(TP+FP)</p>
<p>Recall = TP/(TP+FN)</p>
<p>F1 = 2×Precision×Recall/(Precision+Recall)</p>
<p>Classification: Accuracy, Precision, Recall, F1, AUC-ROC. Regression: MAE, MSE, RMSE, R². Clustering: Silhouette, Davies-Bouldin, Calinski-Harabasz.</p>
</div>

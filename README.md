# Rethinking Fairness in LLM-Based Recommender Systems: A Survey

<!-- TODO: replace XXXX.XXXXX with the real arXiv id, and OWNER/REPO with the GitHub repo once available. -->
[![Static Badge](https://img.shields.io/badge/arXiv-XXXX.XXXXX-b31b1b?logo=arXiv)](https://arxiv.org/abs/XXXX.XXXXX)
![GitHub Repo stars](https://img.shields.io/github/stars/OWNER/REPO?style=flat&logo=GitHub)
![GitHub last commit](https://img.shields.io/github/last-commit/OWNER/REPO?path=README.md&style=flat&logo=GitHub)

- This is the official repository of the paper **Rethinking Fairness in LLM-Based Recommender Systems: A Survey**.

- Authors: Song-Duo Ma, Chu-Yun Chen, Bang-An Li, Pin-Yu Chen, Shau-Yung Hsu, Yun-Nung Chen (National Taiwan University).

<!-- Reference: https://github.com/jonschlinkert/markdown-toc -->
## :sun_with_face: Paper Overview
### :sparkles: Table of content

<!-- toc -->

- [:eyes: Overview](#eyes-overview)
- [:gear: The Roles of LLMs in Recommendation](#gear-the-roles-of-llms-in-recommendation)
- [:balance_scale: A Taxonomy of Fairness in LLM4Rec](#balance_scale-a-taxonomy-of-fairness-in-llm4rec)
  * [:white_check_mark: Bias Mechanisms](#white_check_mark-bias-mechanisms)
    + [Social and Attribute Bias](#social-and-attribute-bias)
    + [Linguistic and Knowledge Bias](#linguistic-and-knowledge-bias)
    + [Data and Propensity Bias](#data-and-propensity-bias)
    + [System and Optimization Bias](#system-and-optimization-bias)
  * [:white_check_mark: Fairness Targets](#white_check_mark-fairness-targets)
- [:bar_chart: Evaluation Resources and Protocols](#bar_chart-evaluation-resources-and-protocols)
  * [:white_check_mark: Datasets and Data Sources](#white_check_mark-datasets-and-data-sources)
  * [:white_check_mark: Fairness Evaluation Protocols](#white_check_mark-fairness-evaluation-protocols)
- [:wrench: Fairness Mitigation in LLM4Rec](#wrench-fairness-mitigation-in-llm4rec)
  * [:white_check_mark: Input-Level Mitigation](#white_check_mark-input-level-mitigation)
  * [:white_check_mark: Data-Level Mitigation](#white_check_mark-data-level-mitigation)
  * [:white_check_mark: Model-Level Mitigation](#white_check_mark-model-level-mitigation)
  * [:white_check_mark: Re-Ranking Mitigation](#white_check_mark-re-ranking-mitigation)
- [:shield: Cross-Cutting Trustworthy Issues](#shield-cross-cutting-trustworthy-issues)
  * [:white_check_mark: Fairness and Explainability](#white_check_mark-fairness-and-explainability)
  * [:white_check_mark: Fairness and Privacy](#white_check_mark-fairness-and-privacy)
  * [:white_check_mark: Fairness and Robustness](#white_check_mark-fairness-and-robustness)
  * [:white_check_mark: Fairness and Controllability](#white_check_mark-fairness-and-controllability)
- [:sushi: Open Challenges and Future Directions](#sushi-open-challenges-and-future-directions)

<!-- tocstop -->

### :eyes: Overview

Large Language Models (LLMs) are reshaping recommender systems (RecSys), moving them beyond
traditional collaborative filtering and user/item IDs toward pipelines enhanced by semantic
understanding, natural language generation, and reasoning. This shift, however, also introduces
**new fairness challenges**: bias may arise not only from interaction data and exposure distributions,
but also from pretrained knowledge, prompt design, generated explanations, decoding strategies,
and feedback loops.

This survey organizes fairness in LLM-based recommender systems (**LLM4Rec**) through a
**two-dimensional view**: *bias mechanisms* (where unfairness emerges) and *fairness targets*
(which stakeholders are affected). It further connects fairness with broader trustworthy concerns —
explainability, privacy, robustness, and controllability — and consolidates the evaluation landscape
and mitigation strategies. To the best of our knowledge, this is the first survey specifically focused
on fairness in LLM4Rec.

<p align="center">
    <img src="img/taxonomy.png" width="700">
</p>

### :gear: The Roles of LLMs in Recommendation

Depending on their position in the pipeline, LLMs can support different stages of recommendation.
Fairness issues take on different forms across these roles.

| Role | Venue | Paper |
|------|-------|-------|
| User and Item Extractors | WWW'24 | Representation Learning with Large Language Models for Recommendation |
| User and Item Extractors | WSDM'24 | LLMRec: Large Language Models with Graph Augmentation for Recommendation |
| Re-Rankers | ECIR'24 | Large Language Models are Zero-Shot Rankers for Recommender Systems |
| Re-Rankers | COLING'25 | Enhancing Reranking for Recommendation with LLMs through User Preference Retrieval |
| Generators | RecSys'22 | Recommendation as Language Processing (RLP): A Unified Pretrain, Personalized Prompt & Predict Paradigm (P5) |
| Generators | Arxiv'22 | [M6-Rec: Generative Pretrained Language Models are Open-Ended Recommender Systems](https://arxiv.org/abs/2205.08084) |
| Explanation Modules | EMNLP'24 | XRec: Large Language Models for Explainable Recommendation |
| Explanation Modules | UMAP'24 | LLM-Generated Explanations for Recommender Systems |

### :balance_scale: A Taxonomy of Fairness in LLM4Rec

Fairness in LLM4Rec is analyzed along two dimensions. **Bias mechanisms** describe the *sources*
from which unfairness emerges; **fairness targets** describe the *stakeholders* affected by
recommendation outcomes (users, items, and both jointly). In each table below, the `Target` column
indicates whether the work addresses **User-Side**, **Item-Side**, or **Two-Sided** fairness.

#### :white_check_mark: Bias Mechanisms

##### Social and Attribute Bias
Bias arising when recommendations vary across sensitive or socially salient attributes such as gender,
age, nationality, religion, occupation, or race, whether explicitly provided or inferred from names,
occupations, or conversational context. (Item-side social bias is *rarely studied explicitly*.)

| Venue | Target | Paper |
|-------|--------|-------|
| RecSys'23 | User-Side | Is ChatGPT Fair for Recommendation? Evaluating Fairness in Large Language Model Recommendation (FaiRLLM) |
| TIST'25 | User-Side | CFairLLM: Consumer Fairness Evaluation in Large-Language Model Recommender System |
| Arxiv'24 | User-Side | [A Normative Framework for Benchmarking Consumer Fairness in LLM Recommender System](https://arxiv.org/abs/2405.02219) |
| RecSys'24 | User-Side | Fairness Matters: A Look at LLM-Generated Group Recommendations |
| EACL'24 | User-Side | UP5: Unbiased Foundation Model for Fairness-Aware Recommendation |
| Arxiv'25 | User-Side | [FairEval: Evaluating Fairness in LLM-Based Recommendations with Personality Awareness](https://arxiv.org/abs/2504.07801) |
| ICML'25 | User-Side | FACTER: Fairness-Aware Conformal Thresholding and Prompt Engineering for Fair LLM-Based Recommender Systems |
| Arxiv'25 | User-Side | [Improving Recommendation Fairness without Sensitive Attributes using Multi-Persona LLMs](https://arxiv.org/abs/2505.19473) |
| Arxiv'26 | User-Side | [Uncertainty and Fairness Awareness in LLM-Based Recommendation Systems](https://arxiv.org/abs/2602.02582) |
| JECR'25 | User-Side | A Comparative Study of Fairness in AI-Enabled and LLM-Based Recommendation Systems |
| Sci. Rep.'25 | User-Side | Fairness Identification of Large Language Models in Recommendation |
| Arxiv'26 | User-Side | [Lightweight Fairness for LLM-Based Recommendations via Kernelized Projection and Gated Adapters](https://arxiv.org/abs/2603.23780) |
| DASFAA'25 | User-Side | Improving Multi-Attribute Fairness in LLM-Based Recommenders through a Mixture-of-Experts Contrastive Learning Method |
| IJCNLP-AACL'25 | Two-Sided | Where Should I Study? Biased Language Models Decide! Evaluating Fairness in LMs for Academic Recommendations |
| SIGIR'25 | Two-Sided | FairWork: A Generic Framework for Evaluating Fairness in LLM-Based Job Recommender System |

##### Linguistic and Knowledge Bias
Bias originating from language patterns, cultural associations, and world knowledge encoded in LLM
pretraining corpora, biasing recommendations toward mainstream or culturally dominant items even
without explicit demographic signals.

| Venue | Target | Paper |
|-------|--------|-------|
| IPM'23 | User-Side | Towards Understanding and Mitigating Unintended Biases in Language Model-Driven Conversational Recommendation |
| EMNLP'24 | User-Side | A Study of Implicit Ranking Unfairness in Large Language Models |
| Arxiv'26 | User-Side | [Can Fairness Be Prompted? Prompt-Based Debiasing Strategies in High-Stakes Recommendations](https://arxiv.org/abs/2603.12935) |
| Arxiv'25 | User-Side | [Revealing Potential Biases in LLM-Based Recommender Systems in the Cold Start Setting](https://arxiv.org/abs/2508.20401) |
| Arxiv'25 | Item-Side | [BiFair: A Fairness-Aware Training Framework for LLM-Enhanced Recommender Systems via Bi-Level Optimization](https://arxiv.org/abs/2507.04294) |
| RecSys'25 | Item-Side | LLM-RecG: A Semantic Bias-Aware Framework for Zero-Shot Sequential Recommendation |
| WWW'24 | Item-Side | Item-Side Fairness of Large Language Model-Based Recommendation System |
| Arxiv'25 | Two-Sided | [Investigating and Mitigating Stereotype-Aware Unfairness in LLM-Based Recommendations](https://arxiv.org/abs/2504.04199) |

##### Data and Propensity Bias
Bias stemming from popularity skews, selection effects, exposure inequalities, and imbalanced
interaction histories, which LLMs may inherit as rankers, user modelers, item encoders, or generators.

| Venue | Target | Paper |
|-------|--------|-------|
| TOIS'25 | User-Side | Mitigating Propensity Bias of Large Language Models for Recommender Systems |
| SIGIR'25 | User-Side | Can LLMs Enhance Fairness in Recommendation Systems? A Data Augmentation Approach |
| WWW'26 | User-Side | Towards Fair Large Language Model-Based Recommender Systems without Costly Retraining |
| IPM'23 | User-Side | Towards Understanding and Mitigating Unintended Biases in Language Model-Driven Conversational Recommendation |
| WWW'24 | Item-Side | Item-Side Fairness of Large Language Model-Based Recommendation System |
| Arxiv'26 | Two-Sided | [Unveiling and Mitigating Bias in Large Language Model Recommendations: A Path to Fairness](https://arxiv.org/abs/2409.10825) |
| WWW'26 | Two-Sided | Bridging Semantic Understanding and Popularity Bias with LLMs |
| CIKM'25 | Two-Sided | LeadFairRec: LLM-Enhanced Discriminative Counterfactual Debiasing for Two-Sided Fairness in Recommendation |
| Arxiv'26 | Two-Sided | [De-Conflating Preference and Qualification: Constrained Dual-Perspective Reasoning for Job Recommendation with LLMs](https://arxiv.org/abs/2602.03097) |

##### System and Optimization Bias
Bias arising when design and inference choices — prompt formulation, candidate ordering, decoding,
and feedback incorporation — systematically shape recommendation outcomes across the pipeline.

| Venue | Target | Paper |
|-------|--------|-------|
| WWW'26 | User-Side | Does LLM Focus on the Right Words? Mitigating Context Bias in LLM-Based Recommenders |
| ACL'25 | User-Side | iAgent: LLM Agent as a Shield between User and Recommender Systems |
| TORS'25 | Item-Side | Understanding Biases in ChatGPT-Based Recommender Systems: Provider Fairness, Temporal Stability, and Recency |
| RecSys'23 | Item-Side | A Preliminary Study of ChatGPT on News Recommendation: Personalization, Provider Fairness, and Fake News |
| WWW'25 | Item-Side | SPRec: Self-Play to Debias LLM-Based Recommendation |
| SIGIR'25 | Item-Side | Dual Debiasing in LLM-Based Recommendation |
| '26 | Item-Side | SPLit: Popularity-Bias-Aware Online Prompt Optimization for LLM-Based Recommendation |
| Arxiv'25 | Item-Side | [BiFair: A Fairness-Aware Training Framework for LLM-Enhanced Recommender Systems via Bi-Level Optimization](https://arxiv.org/abs/2507.04294) |
| Arxiv'26 | Item-Side | [Is Your LLM-as-a-Recommender Agent Trustable? LLMs' Recommendation is Easily Hacked by Biases](https://arxiv.org/abs/2603.17417) |
| EMNLP'24 | Item-Side | Decoding Matters: Addressing Amplification Bias and Homogeneity Issue in Recommendations for LLMs |
| Arxiv'26 | Item-Side | [CollabRec: An LLM-Based Agentic Framework for Balancing Recommendations in Tourism](https://arxiv.org/abs/2508.15030) |
| '26 | Item-Side | Refining Bias and Reward in LLM Recommender Agents through Meta-Controlled Tool Invocation |
| WebSci'26 | Item-Side | Self-Promotion in LLM Recommendations |
| Arxiv'26 | Two-Sided | [Polarization by Default: Auditing Recommendation Bias in LLM-Based Content Curation](https://arxiv.org/abs/2604.15937) |
| KDD'25-W | Two-Sided | Algorithmic Harms Associated with Generative Model-Augmented Recommendation Systems |
| Arxiv'26 | Two-Sided | [Echoes in the Loop: Diagnosing Risks in LLM-Powered Recommender Systems under Feedback Loops](https://arxiv.org/abs/2602.07442) |

#### :white_check_mark: Fairness Targets

- **User-Side Fairness** — ensures equitable recommendation quality and utility across user groups,
  typically evaluated as *group fairness* (comparable performance across demographic groups) and
  *individual fairness* (similar users receive similar treatment).
- **Item-Side Fairness** — centers on the equitable allocation of visibility among items or content
  providers, addressing popularity bias, exposure disparity, and long-tail suppression.
- **Two-Sided Fairness** — balances user-side utility with item-side exposure equity. It is
  particularly challenging in LLM4Rec because improving personalization may unintentionally amplify
  exposure disparities among items or providers.

### :bar_chart: Evaluation Resources and Protocols

#### :white_check_mark: Datasets and Data Sources

Fairness datasets are grouped into three broad types according to how the evaluation data are
constructed and used.

| Dataset Type | Subcategory | Example Datasets / Sources |
|--------------|-------------|----------------------------|
| Curated Candidate-Pool | Curated Item Catalogs | IMDb, MTV, Spotify, QS World University Rankings |
| Curated Candidate-Pool | Real-World Content Pools | Twitter, BlueSky, Reddit, Review-5k, resume-score-details, Shopping Queries Dataset |
| Behavioral Interaction | Entertainment and Media | MovieLens, LastFM, Steam, Book-Crossing, Goodreads, Goodbooks-10k |
| Behavioral Interaction | E-Commerce Review | Amazon Review Datasets (Books, Movies and TV, Video Games, ...) |
| Behavioral Interaction | Service and Community | Yelp, BeerAdvocate, ZhihuRec, AliEC |
| Behavioral Interaction | High-Stakes Decision Domains | CareerBuilder, Insurance, MIND |
| Constructed Evaluation Scenario | Simulated Environments | CS-Domain Job Recommendation Data, SynthTRIPS, University-Profile Data |
| Constructed Evaluation Scenario | Prompt-Synthesized Data | Prompt-Synthesized Books / Movies / Songs Recommendation Data |

#### :white_check_mark: Fairness Evaluation Protocols

Existing protocols are organized into four families by their primary evaluation focus.

**Sensitive Attribute** — Modify sensitive attributes (e.g., gender, age) in prompts and measure
whether outputs change. Metrics are similarity- or ranking-based (e.g., SNSR, SNSV, Jaccard@K,
SERP\*@K, PRAG\*@K).

| Venue | Paper |
|-------|-------|
| RecSys'23 | Is ChatGPT Fair for Recommendation? (FaiRLLM) |
| Arxiv'25 | [FairEval: Evaluating Fairness in LLM-Based Recommendations with Personality Awareness](https://arxiv.org/abs/2504.07801) |
| Arxiv'26 | [Uncertainty and Fairness Awareness in LLM-Based Recommendation Systems](https://arxiv.org/abs/2602.02582) |
| Arxiv'25 | [Revealing Potential Biases in LLM-Based Recommender Systems in the Cold Start Setting](https://arxiv.org/abs/2508.20401) |
| RecSys'24 | Fairness Matters: A Look at LLM-Generated Group Recommendations |
| IPM'23 | Towards Understanding and Mitigating Unintended Biases in Conversational Recommendation |
| Arxiv'26 | [Unveiling and Mitigating Bias in LLM Recommendations: A Path to Fairness](https://arxiv.org/abs/2409.10825) |
| Sci. Rep.'25 | Fairness Identification of Large Language Models in Recommendation |

**Preference Aligned** — Evaluate whether output differences actually harm user benefit, rather than
merely measuring list similarity. The main metric is benefit deviation (e.g., ∆B).

| Venue | Paper |
|-------|-------|
| TIST'25 | CFairLLM: Consumer Fairness Evaluation in Large-Language Model Recommender System |
| Arxiv'24 | [A Normative Framework for Benchmarking Consumer Fairness in LLM Recommender System](https://arxiv.org/abs/2405.02219) |
| SIGIR'25 | Can LLMs Enhance Fairness in Recommendation Systems? A Data Augmentation Approach |
| Arxiv'25 | [Improving Recommendation Fairness without Sensitive Attributes using Multi-Persona LLMs](https://arxiv.org/abs/2505.19473) |
| JECR'25 | A Comparative Study of Fairness in AI-Enabled and LLM-Based Recommendation Systems |
| CIKM'25 | LeadFairRec: LLM-Enhanced Discriminative Counterfactual Debiasing for Two-Sided Fairness |
| ACL'25 | iAgent: LLM Agent as a Shield between User and Recommender Systems |

**Target Specific** — Domain-specific scenarios (e.g., job, academic recommendation). Fairness is
evaluated through counterfactual testing, group-level parity (SP, EO, PPV_diff), and domain-specific
ranking measures (DRS, GRS, U-NDCG).

| Venue | Paper |
|-------|-------|
| SIGIR'25 | FairWork: A Generic Framework for Evaluating Fairness in LLM-Based Job Recommender System |
| EMNLP'24 | A Study of Implicit Ranking Unfairness in Large Language Models |
| Arxiv'26 | [Can Fairness Be Prompted? Prompt-Based Debiasing Strategies in High-Stakes Recommendations](https://arxiv.org/abs/2603.12935) |
| IJCNLP-AACL'25 | Where Should I Study? Evaluating Fairness in LMs for Academic Recommendations |
| Arxiv'26 | [Polarization by Default: Auditing Recommendation Bias in LLM-Based Content Curation](https://arxiv.org/abs/2604.15937) |
| Arxiv'26 | [Is Your LLM-as-a-Recommender Agent Trustable?](https://arxiv.org/abs/2603.17417) |
| Arxiv'26 | [De-Conflating Preference and Qualification for Job Recommendation (JobRec)](https://arxiv.org/abs/2602.03097) |

**Item Side** — Examine whether exposure is equitably distributed across items, especially popular vs.
long-tail. Metrics include Gini Index, HHI, entropy, MGU/DGU, and long-tail coverage.

| Venue | Paper |
|-------|-------|
| TORS'25 | Understanding Biases in ChatGPT-Based Recommender Systems: Provider Fairness, Temporal Stability, and Recency |
| RecSys'23 | A Preliminary Study of ChatGPT on News Recommendation |
| WebSci'26 | Self-Promotion in LLM Recommendations |
| WWW'26 | Towards Fair Large Language Model-Based Recommender Systems without Costly Retraining |
| SIGIR'25 | Dual Debiasing in LLM-Based Recommendation |
| '26 | SPLit: Popularity-Bias-Aware Online Prompt Optimization for LLM-Based Recommendation |
| WWW'26 | Bridging Semantic Understanding and Popularity Bias with LLMs |
| WWW'24 | Item-Side Fairness of Large Language Model-Based Recommendation System |
| WWW'25 | SPRec: Self-Play to Debias LLM-Based Recommendation |
| EMNLP'24 | Decoding Matters: Addressing Amplification Bias and Homogeneity Issue |

### :wrench: Fairness Mitigation in LLM4Rec

Mitigation interventions are organized into four levels: input, data, model, and re-ranking.

#### :white_check_mark: Input-Level Mitigation
Guides LLMs toward fair outcomes during inference without altering parameters (e.g., online prompt
optimization, conformal thresholding with prompt engineering). Prompting can be brittle.

| Venue | Paper |
|-------|-------|
| '26 | SPLit: Popularity-Bias-Aware Online Prompt Optimization for LLM-Based Recommendation |
| ICML'25 | FACTER: Fairness-Aware Conformal Thresholding and Prompt Engineering |
| Arxiv'26 | [Can Fairness Be Prompted? Prompt-Based Debiasing Strategies in High-Stakes Recommendations](https://arxiv.org/abs/2603.12935) |

#### :white_check_mark: Data-Level Mitigation
Targets historical biases in interaction logs via counterfactual data augmentation, counterfactual
debiasing, and causal intervention.

| Venue | Paper |
|-------|-------|
| SIGIR'25 | Can LLMs Enhance Fairness in Recommendation Systems? A Data Augmentation Approach |
| CIKM'25 | LeadFairRec: LLM-Enhanced Discriminative Counterfactual Debiasing for Two-Sided Fairness |
| TOIS'25 | Mitigating Propensity Bias of Large Language Models for Recommender Systems |

#### :white_check_mark: Model-Level Mitigation
Improves fairness by updating or regularizing parameters while avoiding costly full retraining (PEFT,
gated adapters, fairness regularization, bi-level optimization, MoE + contrastive learning).

| Venue | Paper |
|-------|-------|
| WWW'26 | Towards Fair Large Language Model-Based Recommender Systems without Costly Retraining |
| Arxiv'26 | [Lightweight Fairness for LLM-Based Recommendations via Kernelized Projection and Gated Adapters](https://arxiv.org/abs/2603.23780) |
| EACL'24 | UP5: Unbiased Foundation Model for Fairness-Aware Recommendation |
| Arxiv'25 | [BiFair: Fairness-Aware Training via Bi-Level Optimization](https://arxiv.org/abs/2507.04294) |
| DASFAA'25 | Improving Multi-Attribute Fairness through a Mixture-of-Experts Contrastive Learning Method |

#### :white_check_mark: Re-Ranking Mitigation
Modifies decoding to curtail homogeneity (D3) and applies post-hoc re-ranking as a secondary fairness
filter (explainable re-rankers, IPS-based dual debiasing).

| Venue | Paper |
|-------|-------|
| EMNLP'24 | Decoding Matters: Addressing Amplification Bias and Homogeneity Issue (D3) |
| Arxiv'25 | [LLM as Explainable Re-Ranker for Recommendation System](https://arxiv.org/abs/2512.03439) |
| SIGIR'25 | Dual Debiasing in LLM-Based Recommendation |

### :shield: Cross-Cutting Trustworthy Issues

Fairness in LLM4Rec is increasingly intertwined with other dimensions of trustworthiness and should
be studied as a cross-cutting system property rather than a standalone metric.

#### :white_check_mark: Fairness and Explainability
Natural language rationales can make biased behavior more visible, support popularity debiasing, and
enable explainable re-ranking — but plausible explanations may also obscure biased ranking factors.

| Venue | Paper |
|-------|-------|
| '26 | Leveraging Holistic Explanations to Mitigate Popularity Bias for Recommender Systems |
| Arxiv'25 | [LLM as Explainable Re-Ranker for Recommendation System](https://arxiv.org/abs/2512.03439) |
| RecSys'25 | Mitigating Popularity Bias in Counterfactual Explanations using LLMs |
| Arxiv'25 | [LLM4Rec: Large Language Models for Multimodal Generative Recommendation with Causal Debiasing](https://arxiv.org/abs/2510.01622) |
| IUI'25-W | Mitigating Misleadingness in LLM-Generated Natural Language Explanations |
| EMNLP'24 | XRec: Large Language Models for Explainable Recommendation |
| UMAP'24 | LLM-Generated Explanations for Recommender Systems |

#### :white_check_mark: Fairness and Privacy
Privacy protection can reshape how personalization quality is distributed across users and items, and
LLMs may infer sensitive attributes even when explicit demographics are removed.

| Venue | Paper |
|-------|-------|
| IRJET'25 | Privacy-Preserving Large Language Model-Based Recommendation Systems |
| EMNLP'25 | Reading Between the Prompts: How Stereotypes Shape LLM's Implicit Personalization |
| ICLR'24 | Beyond Memorization: Violating Privacy via Inference with Large Language Models |
| Arxiv'25 | [Privacy-Utility-Bias Trade-offs for Privacy-Preserving Recommender Systems](https://arxiv.org/abs/2511.22515) |

#### :white_check_mark: Fairness and Robustness
Fair behavior should not depend on a specific prompt, profile, or interaction trajectory; minor input
changes, feedback loops, and adversarial manipulation can destabilize fairness outcomes.

| Venue | Paper |
|-------|-------|
| Arxiv'25 | [FairEval: Evaluating Fairness with Personality Awareness](https://arxiv.org/abs/2504.07801) |
| EMNLP'24 | A Study of Implicit Ranking Unfairness in Large Language Models |
| WWW'26 | Does LLM Focus on the Right Words? Mitigating Context Bias in LLM-Based Recommenders |
| Arxiv'26 | [Echoes in the Loop: Diagnosing Risks under Feedback Loops](https://arxiv.org/abs/2602.07442) |
| Arxiv'26 | [Is Your LLM-as-a-Recommender Agent Trustable?](https://arxiv.org/abs/2603.17417) |

#### :white_check_mark: Fairness and Controllability
LLM4Rec expose multiple control points (prompts, model objectives, decoding, agentic policies),
making fairness a controllable behavior rather than only an evaluative property.

| Venue | Paper |
|-------|-------|
| TORS'25 | Understanding Biases in ChatGPT-Based Recommender Systems |
| Arxiv'26 | [Can Fairness Be Prompted? Prompt-Based Debiasing Strategies](https://arxiv.org/abs/2603.12935) |
| EACL'24 | UP5: Unbiased Foundation Model for Fairness-Aware Recommendation |
| EMNLP'24 | Decoding Matters: Addressing Amplification Bias and Homogeneity Issue |
| ACL'25 | iAgent: LLM Agent as a Shield between User and Recommender Systems |

### :sushi: Open Challenges and Future Directions

- **Toward Cross-Target Fairness Analysis** — Research is unevenly distributed: user-side social and
  attribute bias is well studied, while item-side social bias and two-sided linguistic/knowledge bias
  remain underexplored. Future work should investigate how fairness objectives *interact* across
  stakeholders (e.g., improving user-side personalization may amplify provider exposure disparities).

- **Toward LLM-Specific Fairness Benchmarks** — Current protocols largely inherit static designs from
  traditional RecSys and focus on isolated sensitive-attribute perturbations. Future benchmarks should
  move beyond single-turn ranking and assess whether fairness remains stable under prompt variations,
  counterfactual user profiles, generated rationales, and feedback loops.

- **Toward Holistic Trustworthy Evaluation** — Fairness should be evaluated jointly with
  explainability, privacy, robustness, and controllability. In particular, the link between fairness
  and faithfulness is underexplored: biased recommendations may be made persuasive by fluent but
  unfaithful explanations.

## :green_book: Citations
If you find our survey and this repository beneficial for your research, please kindly cite our paper.

```bibtex
@misc{ma2026rethinkingfairness,
      title={Rethinking Fairness in LLM-Based Recommender Systems: A Survey},
      author={Song-Duo Ma and Chu-Yun Chen and Bang-An Li and Pin-Yu Chen and Shau-Yung Hsu and Yun-Nung Chen},
      year={2026},
      eprint={XXXX.XXXXX},
      archivePrefix={arXiv},
      primaryClass={cs.IR},
      url={https://arxiv.org/abs/XXXX.XXXXX},
}
```

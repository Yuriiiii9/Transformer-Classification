# Transformer-based Text Classification on 20 Newsgroups

## 项目简介 (Project Overview)

本项目基于 **Transformer 架构 (DistilBERT/BERT)**，对 **20 Newsgroups 数据集** 进行文本分类实验。  
目标是构建一个高性能、多类别的文本分类器，并在模型解释性与工程部署层面进行探索。

This project implements **Transformer models (DistilBERT/BERT)** for text classification on the **20 Newsgroups dataset**.  
The goal is to build a high-performance multi-class classifier and explore **interpretability** and **deployment** aspects.

---

## 方法与流程 (Methodology & Pipeline)

1. **数据预处理 (Data Preprocessing)**  
   - 文本清洗（小写化、停用词去除、分词）  
   - 使用 Hugging Face Tokenizer 转换为模型可读的张量格式  

2. **模型训练 (Model Training)**  
   - Fine-tuning 预训练的 DistilBERT  
   - 引入 Dropout 与 Early Stopping 防止过拟合  
   - 使用 F1-score、ROC-AUC、Confusion Matrix 评估模型性能  

3. **可解释性分析 (Interpretability)**  
   - **Attention Heatmap**：展示模型在不同层级如何关注关键单词  
   - **SHAP 分析**：识别哪些词对分类决策影响最大，增强业务可解释性  

4. **模型部署 (Deployment)**  
   - 通过 FastAPI 构建推理 API  
   - 支持 `curl` 与 Python requests 调用，输入一句话即可返回预测分类  

---

## 项目亮点 (Key Highlights)

- **多维度模型评估**：不仅关注准确率，还分析了召回率与混淆矩阵，识别模型在易混淆类别的表现。  
- **模型可解释性**：结合 Attention 与 SHAP，展示了模型的“决策逻辑”，方便非技术人员理解。  
- **可落地性**：提供 API 接口，演示了从建模 → 部署的完整流程，体现实际应用价值。  

- **Comprehensive Evaluation**: Beyond accuracy, evaluated with recall, confusion matrix, and error analysis.  
- **Interpretability**: Used Attention visualization and SHAP to reveal model reasoning, improving trustworthiness.  
- **Deployment Ready**: Delivered a FastAPI endpoint, demonstrating an end-to-end workflow from modeling to production.  

---

## 示例 (Example Inference)

```bash
curl -X POST "https://<your-ngrok-link>/predict" \
     -H "Content-Type: application/json" \
     -d '{"text": "NASA just released new photos from the Hubble telescope"}'

# Response:
{"predicted_label": "sci.space"}
```

## 文件结构 (Project Structure)
Transformer-Classification/
│── Transformer_20Newsgroup.ipynb   # 模型训练与解释性分析
│── Deployment.ipynb                # FastAPI 部署与 API 调用示例
│── requirements.txt                # 依赖库
│── README.md                       # 项目说明 (本文件)

## 技术栈 (Tech Stack)
- Python, PyTorch, Hugging Face Transformers
- Scikit-learn, SHAP, Matplotlib
- FastAPI, Ngrok

## 业务价值 (Business Value)
- 提供**可解释的文本分类方案**，适用于舆情分析、客服工单自动分流、内容审核等场景。
- 构建了一个从**数据 → 模型 → 可解释性 → 部署**的端到端流程，展示了机器学习项目的完整生命周期。

This project provides an interpretable text classification solution, with potential applications in sentiment analysis, customer service ticket routing, and content moderation.
It also demonstrates a complete end-to-end ML pipeline, covering data, modeling, interpretability, and deployment.

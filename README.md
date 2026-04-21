<div align="center">
  <h1>⚖️ Legal RAG Assistant</h1>
  <p><strong>Assistente Inteligente de Análise de Contratos com IA Generativa (100% Open Source)</strong></p>

  [![Python](https://img.shields.io/badge/Python-3.9+-blue.svg?style=flat&logo=python)](https://www.python.org/)
  [![LangChain](https://img.shields.io/badge/LangChain-Integration-green.svg?style=flat)](https://python.langchain.com/)
  [![HuggingFace](https://img.shields.io/badge/🤗_Hugging_Face-Transformers-yellow.svg)](https://huggingface.co/)
  [![FAISS](https://img.shields.io/badge/Vector_DB-FAISS-lightgrey.svg)](https://github.com/facebookresearch/faiss)
</div>

<br>

## 🚀 Sobre o Projeto
Este projeto implementa um modelo **Retrieval-Augmented Generation (RAG)** focado na análise semântica e auditoria de contratos jurídicos (aluguel, serviço, etc). A arquitetura utiliza inteiramente **modelos locais e gratuitos** (TinyLlama, Sentence-Transformers), processados via CPU/GPU, demonstrando sólida habilidade em contornar limitações de custo através da comunidade Open-Source.

O assistente vai além de responder perguntas estruturadas: ele classifica o risco associado a cláusulas financeiras e utiliza lógicas sofisticadas de segurança e tratamento de tokens para evitar "alucinações" (hallucinations) e vazamento de prompt.

---

## 💡 Destaques Técnicos & Melhorias Mencionadas em Portfolio
- **Prevenção de Prompt Leakage:** Implementação de pós-processamento utilizando limpeza em cascata, impedindo que instruções de "system prompts" sejam impressas na resposta final.
- **Avaliação de Risco Customizada:** Um motor de inferência sintático e semântico capaz de classificar o grau de penalidade de quebras de contrato em categorias (🟢 Baixo Risco, 🟡 Risco Moderado e 🔴 Alto Risco Financeiro).
- **Gerenciamento de Contexto Eficiente:** Utilização avançada do mecanismo *RecursiveCharacterTextSplitter*, controlando o *chunk_size* e o *chunk_overlap* para estabilizar janelas curtas de token sem corromper sentenças jurídicas vitais.
- **Pipelines do Hugging Face Totalmente Tunados:** Argumentos precisos para geração restrita de texto e workaround para fix de conflitos atrelados à pipeline HF default.

---

## 🛠️ Tecnologias Utilizadas

| Componente | Tecnologia | Papel no App |
| --- | --- | --- |
| **Linguagem Principal** | Python | Orquestração do sistema RAG |
| **Framework LLM** | LangChain | Corrente de busca e recuperação de contexto |
| **Banco de Dados Vetorial** | FAISS | Armazenamento seguro de _Embeddings_ |
| **Embeddings** | `all-MiniLM-L6-v2` | Criação ágil e local dos tensores a partir dos PDFs |
| **LLM (Large Language Model)** | `TinyLlama 1.1B` | Geração de respostas baseada e condicionada ao contexto |

---

## ⚙️ Funcionalidades
1. Leitura e interpretação robusta de PDFs locais (`PyPDF`).
2. Categorização de Metadados (Separação entre pagamentos, multa, rescisão, prazo).
3. Busca vetorial refinada por intenção do usuário (`get_relevant_documents`).
4. Pipeline RAG estruturado para garantir rastreabilidade (`fontes consultadas` disponíveis em cada output).
5. Output imune a verbosidade em excesso (Respostas forçadas e controladas sistematicamente).

---

## 📥 Como Rodar o Projeto

1. Clone o Repositório
```bash
git clone [https://github.com/natsousacosta311-dados/legal-rag-assistant]
cd legal_rag_assistant
```

2. Instale as Dependências necessárias
```bash
pip install langchain langchain-community langchain-text-splitters sentence-transformers faiss-cpu pypdf transformers accelerate huggingface_hub
```

3. Adicione contratos em `.pdf` no mesmo diretório (ex: `contrato_servico_1.pdf`).
4. Execute o Jupyter Notebook `assistente_com_rag_corrigido_1.ipynb`.

---

## 🧠 Considerações de Engenharia e Setup 
* **Memória vs Escalabilidade:** O framework foi moldado em `torch.float32` (visando hardwares domésticos ou instâncias standard/free CPU do Colab), todavia sua base em pipeline Transformers possibilita a transição imediata para `torch.float16` via cuda a fim de ganhar escala em aplicações enterprise.

***

<div align="center">
  <p>Desenvolvido com dedicação por <a href="https://github.com/natsousacosta311-dados"><strong>[Natasha Sousa]</strong></a> | Data Scientist & AI Engineer</p>
  <p>🤝 Quer bater um papo bacana sobre as abordagens de NLP aplicadas aqui? Me chama no <a href="[https://linkedin.com/in/SEU_LINKEDIN](https://www.linkedin.com/in/natasha-sousa-costa-46281a276/)">LinkedIn</a>!</p>
</div>

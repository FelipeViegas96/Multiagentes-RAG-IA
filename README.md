# Multiagentes-RAG-IA
Ecossistema de multiagentes de IA com RAG integrado ao Gmail — 4 agentes especializados orquestrados via n8n com Supabase Vector Store, OpenAI Embeddings e Google Gemini. Projeto prático da pós-graduação em Data Analytics e IA Aplicada a Negócios (FNAT).

# 🤖 Ecossistema de Multiagentes de IA — ViaSul Turismo

Projeto desenvolvido durante a pós-graduação em Data Analytics 
e IA Aplicada a Negócios (FNAT) — 2026.

## 📌 Sobre o Projeto

Automação completa de atendimento ao cliente via e-mail utilizando 
um ecossistema de 4 agentes de IA especializados, com roteamento 
inteligente, RAG e memória de sessão.

## 🏗️ Arquitetura

![Fluxo n8n](docs/arquitetura_fluxo.png)

## 🤖 Agentes

| Agente | Função |
|--------|--------|
| Avaliador | Identifica se o contato é cliente novo ou antigo |
| Orquestrador | Roteia para o agente correto sem gerar respostas |
| Vendedor | Atendimento consultivo para novos clientes |
| Fidelizador | Reativação de clientes antigos |
| Concierge | Suporte pré e pós-viagem |

## 🛠️ Stack Tecnológica

- **n8n** — orquestração dos fluxos
- **OpenAI** — LLM principal e embeddings (text-embedding-3-small)
- **Google Gemini** — LLM secundário
- **Supabase + pgvector** — Vector Store para RAG
- **Gmail API** — canal de entrada e saída
- **Google Sheets** — base de clientes cadastrados
- **Google Calendar** — agendamento automatizado

## 🧠 Como o RAG funciona

1. Documentos do portfólio carregados do Google Drive
2. Divididos em chunks pelo Recursive Character Text Splitter
3. Vetorizados com OpenAI Embeddings
4. Armazenados no Supabase com extensão pgvector
5. Acessados via similarity search a cada interação

## 🔐 Segurança

- System prompts estruturados em 5 camadas 
  (Identidade, Missão, Comportamento, Limitações e Conhecimento)
- Resistência a prompt injection por design
- Memória de sessão isolada por threadId + e-mail
- Agentes com acesso restrito apenas à base de conhecimento autorizada

## 📁 Prompts

Os system prompts completos de cada agente estão disponíveis 
na pasta `/prompts`.

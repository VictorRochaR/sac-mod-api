# Módulo Headless de SAC Inteligente e Moderação

<div align="center">
  <img src="https://img.shields.io/badge/Architecture-Headless-blue?style=flat-square" alt="Headless Architecture" />
  <img src="https://img.shields.io/badge/AI-RAG_Pipeline-orange?style=flat-square" alt="RAG Pipeline" />
  <img src="https://img.shields.io/badge/NLP-PT--BR_Optimized-brightgreen?style=flat-square" alt="PT-BR NLP" />
  <img src="https://img.shields.io/badge/Clean_Code-Strict-critical?style=flat-square" alt="Clean Code" />
</div>

<br>

> Solução unificada de atendimento consultivo e moderação de conteúdo para e-commerce, impulsionada por IA Generativa e arquitetura RAG (Retrieval-Augmented Generation). Proposta desenvolvida como projeto corporativo e acadêmico em parceria com a **Galvitech**.

---

## O Problema

O varejo digital brasileiro enfrenta um gargalo crítico de escalabilidade operacional. A demora no esclarecimento de dúvidas pré-compra impacta diretamente a taxa de conversão (abandono de carrinho), enquanto a incapacidade de auditar rapidamente avaliações de usuários expõe as marcas a conteúdos tóxicos, spam e concorrência desleal. 

As soluções de mercado atuais falham por dois motivos:
1. **Fragmentação:** Tratam atendimento e moderação em sistemas separados, aumentando o custo de licenciamento e a complexidade arquitetural da loja.
2. **Barreira Idiomática:** Utilizam modelos genéricos treinados majoritariamente em inglês, gerando atritos de interpretação com expressões, coloquialismos e gírias do português brasileiro.

## A Solução

Uma **API Headless (RESTful)** omnichannel projetada para atuar no coração do e-commerce, resolvendo ambas as dores em um único ecossistema:

- **Atendimento Consultivo Autônomo (RAG):** O sistema vetoriza os catálogos da loja e recupera apenas os fragmentos de texto matematicamente relevantes para responder às dúvidas dos consumidores em tempo real, evitando alucinações por parte da IA.
- **Moderação de Conteúdo (Middleware):** Filtro inteligente baseado em Processamento de Linguagem Natural (NLP) para interceptar avaliações. Conteúdos ofensivos são retidos no banco de dados com status "pendente de revisão humana", blindando a vitrine da loja.

## Arquitetura do Sistema

O projeto é estruturado para ser agnóstico ao canal de comunicação (WhatsApp, Web Chat, Página do Produto), atuando como o motor central de inteligência.

<div align="center">
  <img width="497" height="208" alt="Diagrama do Módulo Headless de SAC Inteligente e Moderação" src="https://github.com/user-attachments/assets/e0e4b381-07b7-49a6-a5de-9a0077d22b62" />
</div>

1. **Ingestão:** O lojista faz upload do catálogo via Painel Administrativo.
2. **Processamento Vetorial:** O texto é particionado (*chunking*) e convertido em *embeddings* que são armazenados em um Banco de Dados Vetorial.
3. **Atendimento/Moderação:** A API Headless recebe a requisição, realiza a busca por Similaridade de Cosseno (para dúvidas) ou orquestra o *System Prompt* de classificação (para reviews) junto ao LLM externo, devolvendo a resposta de forma otimizada.

## Princípios de Engenharia e Clean Code

Para garantir que a base de código seja altamente escalável e de fácil manutenção, o desenvolvimento é pautado por diretrizes rígidas de qualidade técnica:

* **Clean Architecture & Domain-Driven:** Separação clara entre a lógica de negócio central e as integrações externas (Banco de Dados, APIs de LLMs, Interfaces Web).
* **Responsabilidade Única (SRP):** Funções e classes são projetadas para fazer apenas **uma** coisa. Rotinas com múltiplas operações simultâneas são estritamente refatoradas e divididas, centralizando as regras de negócio em domínios isolados.
* **Código Autodocumentado (Zero Comments):** O projeto adota a premissa de que comentários geralmente indicam variáveis mal descritas ou métodos complexos demais que deveriam ser divididos. A clareza do sistema é garantida através de nomenclatura expressiva e fluxos lógicos, dispensando comentários no código-fonte.
* **Segurança e Privacidade (LGPD):** Estruturação de salvaguardas para ofuscação de dados financeiros e pessoais sensíveis antes da submissão de prompts ao modelo de linguagem.

## 📄 Licença
Este projeto está sob a licença **SSPL (Server Side Public License)**. O uso corporativo ou comercial não autorizado do código-fonte sem anuência prévia é restrito.

---
*Projeto desenvolvido por **Victor Rocha** | Portfólio de Aprendizagem Colaborativa (PAC).*

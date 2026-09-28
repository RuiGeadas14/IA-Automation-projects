# 📊 Gestão de Leads e Relatório Diário com n8n

Projeto de automação de processos desenvolvido com **n8n**, **Google Sheets** e **Gmail**, criado para simular um processo empresarial de captação, classificação e acompanhamento de leads.

O sistema recebe novos leads, classifica-os de acordo com o orçamento disponível, regista-os num CRM em Google Sheets e envia automaticamente um relatório diário à equipa. Depois do envio, cada lead é marcado como processado para impedir que volte a aparecer num relatório futuro.

## 🎯 Objetivo do projeto

O objetivo é reduzir tarefas manuais no acompanhamento de leads e criar um processo consistente entre a entrada de um novo contacto, a sua classificação e a comunicação diária com a equipa comercial.

A automação foi construída para lidar também com o cenário em que **não existem novos leads a reportar**, enviando uma notificação específica à equipa.

## ⚙️ Como funciona

### 1. Gestão e classificação de leads

O primeiro workflow é acionado quando é recebido um novo lead.

O processo:

- recebe os dados do novo lead;
- analisa o orçamento disponível;
- atribui uma prioridade — **Alta, Média ou Baixa**;
- guarda o lead na folha central de CRM;
- define inicialmente `Relatório Enviado = Não`.

### 2. Relatório diário de leads

O segundo workflow é executado automaticamente através de um agendamento.

O processo:

- consulta os leads existentes no CRM;
- identifica os registos com `Relatório Enviado = Não`;
- separa os leads por prioridade;
- constrói o relatório em HTML;
- envia o relatório através do Gmail;
- atualiza os leads processados para `Relatório Enviado = Sim`;
- envia uma notificação independente quando não existem novos leads.

## 🏗️ Arquitetura da automação

```text
Google Forms / Origem dos Leads
              │
              ▼
       Google Sheets
              │
              ▼
      Gestão de Leads
              │
              ├──► Classificação por orçamento
              │
              ├──► Atribuição de prioridade
              │
              ▼
          CRM de Leads
              │
              │  Relatório Enviado = Não
              ▼
       Relatório Diário
              │
              ├──► Alta
              ├──► Média
              └──► Baixa
              │
              ▼
        Relatório HTML
              │
              ▼
            Gmail
              │
              ▼
    Relatório Enviado = Sim
```

## 🧩 Tecnologias utilizadas

- **n8n** — orquestração e automação dos processos;
- **Google Sheets** — armazenamento e gestão dos leads;
- **Gmail** — envio automático dos relatórios;
- **JavaScript** — tratamento e preparação dos dados;
- **HTML** — estrutura e formatação dos emails;
- **Agendamentos** — execução automática do relatório diário;
- **Lógica condicional** — encaminhamento dos dados de acordo com diferentes condições.

## 💡 Conceitos de automação demonstrados

Este projeto demonstra vários padrões relevantes para automação de processos empresariais:

- automação orientada por eventos;
- automação baseada em agendamento;
- lógica condicional;
- classificação de dados;
- utilização de múltiplos caminhos num workflow;
- utilização do Google Sheets como CRM simplificado;
- geração de emails em HTML;
- gestão de estado através do campo `Relatório Enviado`;
- prevenção de relatórios duplicados;
- tratamento do cenário sem novos leads;
- atualização dos registos após o processamento.

## 📁 Estrutura do repositório

```text
n8n-lead-management/
├── README.md
├── PROJECT_INFO.md
├── .gitignore
├── workflows/
│   ├── lead-management.json
│   └── daily-lead-report.json
└── docs/
    └── setup.md
```

## 🚀 Configuração

Os ficheiros JSON incluídos neste repositório são **modelos preparados para portefólio**. As referências privadas, credenciais e identificadores específicos não devem ser publicados no GitHub.

Para utilizar os workflows, é necessário configurar no n8n:

1. Credenciais OAuth do Google Sheets;
2. Credenciais OAuth do Gmail;
3. O documento e as folhas do Google Sheets utilizados pelo projeto;
4. O endereço de email de destino;
5. Os nomes das folhas e respetivas colunas;
6. O horário e fuso horário pretendidos para o relatório diário.

Os valores reais devem permanecer configurados diretamente no n8n e não devem ser colocados no repositório.

Para instruções detalhadas, consulta o ficheiro [`docs/setup.md`](docs/setup.md).

## 🔐 Segurança

Nunca publiques no GitHub:

- chaves de API;
- client secrets OAuth;
- palavras-passe;
- ficheiros `.env` com informação privada;
- credenciais do n8n;
- identificadores privados desnecessários;
- outros dados que permitam acesso a serviços ou contas.

O objetivo deste repositório é apresentar a **estrutura e a lógica do projeto**, e não expor as credenciais utilizadas na implementação real.

## 📌 Contexto de portefólio

Este projeto foi desenvolvido como parte de um percurso prático de aprendizagem em **AI Automation e automação de processos empresariais**.

O cenário representa uma necessidade comum numa equipa comercial: receber leads, organizar a informação, definir prioridades e garantir que a equipa recebe diariamente apenas os contactos que ainda não foram reportados.

Além da automatização do processo principal, foi implementado um tratamento específico para o caso em que não existem novos leads, evitando que a equipa fique sem informação sobre o estado do processo.

## 👤 Autor

Projeto desenvolvido como parte de um **portefólio de AI Automation e n8n**.

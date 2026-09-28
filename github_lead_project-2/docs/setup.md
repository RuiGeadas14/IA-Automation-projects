# 🚀 Guia de Configuração

Este documento explica como importar e configurar os workflows deste projeto no n8n.

## 1. Importar os workflows

No n8n, importa os ficheiros JSON existentes na pasta `workflows/`:

- `lead-management.json`
- `daily-lead-report.json`

Os ficheiros são preparados para utilização como modelos de portefólio. Depois da importação, deves configurar as tuas próprias credenciais e referências aos serviços.

## 2. Configurar o Google Sheets

Cria ou liga uma credencial OAuth do **Google Sheets** no n8n e seleciona a folha utilizada para armazenar os leads.

A estrutura recomendada inclui as seguintes colunas:

- Nome
- E-mail
- Empresa
- Telefone
- Serviço pretendido
- Orçamento disponível
- Data do projeto
- Descrição do projeto
- Prioridade
- Relatório Enviado

Os novos leads devem começar com:

`Relatório Enviado = Não`

Depois de serem incluídos num relatório enviado com sucesso, o estado deve passar para:

`Relatório Enviado = Sim`

## 3. Configurar o Gmail

Cria ou liga uma credencial OAuth do **Gmail** no n8n.

Define o endereço de destino utilizado pela equipa comercial ou responsável pelo acompanhamento dos leads.

O projeto contempla dois cenários:

- envio do relatório quando existem novos leads;
- envio de uma notificação quando não existem novos leads.

## 4. Configurar o agendamento

No workflow **Relatório Diário de Leads**, configura o nó de agendamento para executar o processo no horário pretendido.

Confirma também que o fuso horário do n8n está corretamente configurado para o local onde o workflow será executado.

## 5. Testar o workflow

Antes de utilizar a automação em produção, testa os dois cenários principais.

### Cenário A — Existem novos leads

Pelo menos um lead deve apresentar:

`Relatório Enviado = Não`

**Resultado esperado:**

- o lead é incluído no relatório;
- o relatório é enviado através do Gmail;
- o lead processado é atualizado para `Sim`.

### Cenário B — Não existem novos leads

Todos os leads devem apresentar:

`Relatório Enviado = Sim`

**Resultado esperado:**

- não é criado um relatório de leads;
- a equipa recebe uma notificação a indicar que não existem novos leads.

## 🔐 Segurança e credenciais

Não coloques credenciais, passwords, chaves de API ou outros dados privados nos ficheiros do repositório.

As credenciais devem ser configuradas diretamente no n8n.

Se o workflow original utilizar identificadores privados, substitui-os por referências próprias antes de partilhar o projeto publicamente.

## 📦 Estrutura dos ficheiros

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

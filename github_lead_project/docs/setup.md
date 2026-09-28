# Setup Guide

## 1. Import the workflows

In n8n, import the JSON files from `workflows/`.

Because this repository contains sanitized templates, replace the placeholder Google Sheet references and reconnect your own credentials.

## 2. Connect Google Sheets

Create/connect a Google Sheets OAuth credential and select the spreadsheet used for the lead CRM.

Recommended columns:

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

New leads should start with:

`Relatório Enviado = Não`

## 3. Connect Gmail

Create/connect a Gmail OAuth credential and set the destination address used by the sales/reporting team.

## 4. Configure the schedule

Set the Daily Lead Report workflow to run at the desired local time. Make sure the n8n timezone is configured correctly for the deployment.

## 5. Test

Test both cases:

### New leads
At least one lead has:

`Relatório Enviado = Não`

Expected result:
- lead enters the report;
- report is sent;
- processed lead is changed to `Sim`.

### No new leads
All leads have:

`Relatório Enviado = Sim`

Expected result:
- no lead report is generated;
- the team receives the "no new leads" notification once.


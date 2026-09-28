# n8n Lead Management & Daily Reporting

An end-to-end lead automation project built with **n8n**, **Google Sheets** and **Gmail**.

The system captures incoming leads, classifies them by budget, stores them in a CRM-style Google Sheet, generates a daily report and prevents the same lead from being reported more than once.

## What the project does

### 1. Lead Management
The first workflow is triggered when a new row is added to the lead-response spreadsheet.

It:
- receives the new lead;
- evaluates the available budget;
- assigns a priority (`Alta`, `Média` or `Baixa`);
- stores the lead in a central CRM sheet;
- starts each new lead with `Relatório Enviado = Não`.

### 2. Daily Lead Report
The second workflow runs automatically on a schedule.

It:
- reads the CRM sheet;
- checks which leads still have `Relatório Enviado = Não`;
- separates leads by priority;
- builds an HTML email report;
- sends the report through Gmail;
- updates processed leads to `Relatório Enviado = Sim`;
- sends a separate notification when there are no new leads.

## Architecture

```text
Google Forms / Lead Source
          |
          v
   Google Sheets
          |
          v
   Lead Management
          |
          +--> Budget classification
          |
          +--> Priority assignment
          |
          v
      Leads CRM
          |
          |  Relatório Enviado = Não
          v
  Daily Lead Report
          |
          +--> Alta
          +--> Média
          +--> Baixa
          |
          v
    HTML report
          |
          v
        Gmail
          |
          v
Relatório Enviado = Sim
```

## Technologies

- n8n
- Google Sheets
- Gmail
- JavaScript
- HTML email
- Scheduled workflows
- Conditional logic

## Key automation concepts demonstrated

This project demonstrates practical automation patterns used in business workflows:

- event-driven automation;
- scheduled automation;
- conditional routing;
- data classification;
- multi-branch workflows;
- Google Sheets as a lightweight CRM;
- HTML email generation;
- state management with `Relatório Enviado`;
- duplicate-report prevention;
- handling the "no new leads" case;
- updating records after successful processing.

## Repository structure

```text
n8n-lead-management/
├── README.md
├── .gitignore
├── workflows/
│   ├── lead-management.json
│   └── daily-lead-report.json
└── docs/
    └── setup.md
```

## Setup

The workflow JSON files in this repository are **sanitized templates**. Private Google Sheet IDs, email addresses and n8n credential identifiers have been replaced with placeholders.

Before importing/using them, configure:

1. Google Sheets OAuth credentials.
2. Gmail OAuth credentials.
3. The Google Sheet/document IDs.
4. The destination email address.
5. The required sheet/tab names.
6. The desired schedule and timezone.

For the original private workflow, keep the real credentials and IDs only inside n8n — never commit them to GitHub.

## Important security note

Do not publish:
- OAuth client secrets;
- API keys;
- passwords;
- private email addresses;
- private Google Drive/Sheets identifiers if you want the repository to remain fully public;
- n8n instance identifiers or other sensitive deployment information.

The JSON files included here have been sanitized for public portfolio use.

## Portfolio context

This project was created as a practical automation project to simulate a business lead-management process. It focuses on reducing manual work for a sales team and ensuring that daily reports contain only leads that have not already been reported.

## Author

Built as part of an **AI Automation / n8n learning portfolio**.

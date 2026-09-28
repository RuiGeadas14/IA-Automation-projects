# 📋 Informações do Projeto

**Projeto:** Gestão de Leads e Relatório Diário com n8n  
**Área:** AI Automation / Automação de Processos Empresariais  
**Tecnologias principais:** n8n, Google Sheets, Gmail, JavaScript e HTML  

## Objetivo

Automatizar o processo de receção, classificação e acompanhamento de leads, desde a entrada de um novo contacto até ao envio do relatório diário à equipa.

O sistema utiliza o campo `Relatório Enviado` para controlar o estado de cada lead e evitar que o mesmo contacto seja incluído em relatórios futuros depois de já ter sido processado.

## Workflows

### Gestão de Leads

Responsável por receber novos leads, analisar o orçamento disponível, atribuir uma prioridade e guardar a informação no CRM em Google Sheets.

### Relatório Diário de Leads

Responsável por consultar os leads ainda não reportados, organizar a informação por prioridade, gerar o email de relatório, enviá-lo através do Gmail e atualizar o estado dos leads processados.

Quando não existem novos leads, o workflow envia uma notificação específica à equipa.

## Resultado

O projeto demonstra um fluxo completo de automação empresarial, desde a entrada e tratamento dos dados até à comunicação automática e atualização do estado dos registos.

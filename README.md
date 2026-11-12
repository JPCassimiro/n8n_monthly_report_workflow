# n8n_monthly_report_workflow
Workflow no N8N para geração de relatórios mensais.</br>
Este workflow automatiza a geração de relatórios de desempenho dos pedidos de uma gráfica, utilizando como fontes de informação uma planilha contendo os dados dos pedidos, um documento com as metas e expectativas de desempenho e dois modelos de relatório. A partir da análise dessas informações, o workflow gera mensalmente um relatório com indicadores e análises relevantes, seguindo a estrutura dos modelos fornecidos. Sua execução é programada para ocorrer todo dia 1º, às 6h da manhã, contemplando os dados do mês anterior. Ao final do processo, o relatório é exportado em formato PDF e enviado automaticamente por e-mail, além de gerar uma cópia editável do documento no Google Drive de uma conta previamente designada.

## Pré-requisitos
Caso queira rodar esse fluxo localmente.

### Ambiente
  Docker
  N8N instalado
  Projeto no Google Cloud Workspace 

### Credenciais e permissões necessárias
- Google Sheets
  - Autenticação: OAuth2
  - Permissão: Leitura de planilhas.
- Google Docs
  - Autenticação: OAuth2
  - Permissões: Leitura e edição de documentos.
- Google Drive
  - Autenticação: OAuth2
  - Permissões: Leitura, cópia, criação e download de arquivos.
- Gmail
  - Autenticação: OAuth2
  - Permissão: Envio de e-mails.
- Groq API
  - Autenticação: API Key
  - Permissão: Acesso à API de inferência de modelos de linguagem (LLM).

## Utilização
  Utilize a função de importar por arquivo no workplace do N8N</br>
  Preencha os nodos com as devidas requisições como links de documentos, contas para autorização e chaves de API.</br>

## Documentos necessários
  Para funcionar corretamente, esse fluxo obrigatoriamente precisa de 4 documentos.</br>
  - Tabela de dados
    - Essa tabela vai informar os valores a serem analisados
    - O Google Sheets deve ser utilizado
  - Documento de previsão de performance
    - Documento Google com informações sobre a previsão da performance da empresa para o período de tempo a ser analisado.
  - Modelo de relatório
    - Documento modelo com informações sobre o que o relatório deve conter
    - Documento separado por seções
    - Conteúdo de cada seção é uma descrição detalhada de como o LLM deve gerar textos, quais fatores deve analisar e quais KPIs devem ser calculados.
  - Modelo a ser copiado
    - Esse modelo é uma versão simplificada do modelo acima
    - Textos descritivos são substituídos por variáveis
    - Essas variaveis serão substituidas pelo texto gerado pelo modelo através de uma requisição HTTP
  

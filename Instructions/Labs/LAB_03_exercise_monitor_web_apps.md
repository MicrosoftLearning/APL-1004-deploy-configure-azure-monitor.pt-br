---
lab:
  title: 'Exercício: Monitorar aplicativos Web'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tarefas de habilidades

- Habilitar o Application Insights
- Desabilitar o registro em log para o depurador de instantâneos do .NET Core
- Configurar os logs HTTP do aplicativo Web para serem gravados no workspace do Log Analytics
- Configurar os dados do SQL Insights a serem gravados no workspace do Log Analytics
- Habilitar o controle de alterações de arquivos e alterações de aplicativos Web

## Instruções para o exercício

### Habilitar o Application Insights

1. Na barra de pesquisa do portal do Azure, digite **rg-alpha** e selecione **rg-alpha** na lista de resultados.
1. Na lista de itens no grupo de recursos, escolha **Serviços de aplicativos para o aplicativo Web com um Banco de Dados SQL**.
1. Em **Configurações**, escolha **Application Insights**.
1. No painel do **Application Insights**, selecione **Ativar o Application Insights**.
1. Na página **Application Insights**, verifique se **Criar um novo recurso** está selecionado e se o Workspace do Log Analytics está definido como **LogAnalytics1** e escolha **Aplicar**.
1. Na caixa de diálogo **Aplicar configurações de monitoramento**, escolha **Sim**.

### Desabilitar o registro em log para o depurador de instantâneos do .NET Core

1. Na barra de pesquisa do portal do Azure, digite **rg-alpha** e selecione **rg-alpha** na lista de resultados.
1. Na lista de itens no grupo de recursos, escolha **Serviços de aplicativos para o aplicativo Web com um Banco de Dados SQL**.
1. Em **Configurações**, escolha **Application Insights**.
1. Em **Instrumentar o aplicativo**, selecione **.NET Core** e defina a configuração do Depurador de instantâneo como **Desativado**. Escolha **Aplicar**.
1. Na caixa de diálogo **Aplicar configurações de monitoramento**, escolha **Sim**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Nome da configuração de diagnóstico  | httplogs   |
    | Categorias    | Logs HTTP  |
    | Detalhes do destino   | Enviar para o workspace do Log Analytics  |
    | Subscription  | Sua assinatura  |
    | Espaço de trabalho do Log Analytics   | LogAnalytics1   |

### Configurar os logs HTTP do aplicativo Web para serem gravados no workspace do Log Analytics

1. Na barra de pesquisa do portal do Azure, digite **rg-alpha** e selecione **rg-alpha** na lista de resultados.
1. Na lista de itens no grupo de recursos, escolha **Serviços de aplicativos para o aplicativo Web com um Banco de Dados SQL**.
1. Em **Monitoramento**, escolha **Configurações de diagnóstico**.
1. Na página **Configurações de diagnóstico**, selecione **+Adicionar configurações de diagnóstico**.
1. Na página **Configurações de diagnóstico**, escolha o seguinte e selecione **Salvar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Nome da configuração de diagnóstico  | httplogs   |
    | Categorias    | Logs HTTP  |
    | Detalhes do destino   | Enviar para o workspace do Log Analytics  |
    | Subscription  | Sua assinatura  |
    | Espaço de trabalho do Log Analytics   | LogAnalytics1   |

### Configurar os dados do SQL Insights a serem gravados no workspace do Log Analytics

1. Na barra de pesquisa do portal do Azure, digite **rg-alpha** e selecione **rg-alpha** na lista de resultados.
1. Na lista de itens no grupo de recursos, escolha o banco de dados SQL de exemplo.
1. Em **Monitoramento**, escolha **Configurações de diagnóstico**.
1. Na página **Configurações de diagnóstico**, escolha **Adicionar configuração de diagnóstico**.
1. Na **página de Configuração de diagnóstico**, forneça as seguintes informações e escolha **Salvar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Nome da configuração de diagnóstico  | InsightLogAnalytics   |
    | Categorias    | SQL Insights  |
    | Detalhes do destino   | Enviar para o workspace do Log Analytics  |
    | Subscription  | Sua assinatura  |
    | Espaço de trabalho do Log Analytics   | LogAnalytics1   |

### Habilitar o controle de alterações de arquivos e alterações de aplicativos Web

1. Na barra de pesquisa do portal do Azure, digite **rg-alpha** e selecione **rg-alpha** na lista de resultados.
1. Na lista de itens no grupo de recursos, escolha o AzureLinuxAppWXYZ-webapp.
1. Selecione **Diagnosticar e solucionar problemas**.
1. Na caixa de diálogo de pesquisa, digite **Alterações do aplicativo**.
1. Na página **Análise de alterações**, escolha **Configurar**.
1. Na página **Habilitar controle de alterações de arquivo e configuração**, altere o controle deslizante Status para **Ativado** e escolha **Salvar**.

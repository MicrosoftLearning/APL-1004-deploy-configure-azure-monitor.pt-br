---
lab:
  title: 'Exercício: implantar o Log Analytics'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tarefas de habilidades

- Criar um workspace do Log Analytics
- Configurar políticas de arquivamento e retenção de dados do Log Analytics
- Habilitar o acesso a um workspace do Log Analytics

## Instruções para o exercício

### Criar um workspace do Log Analytics

1. Na barra de pesquisa do portal do Azure, insira **Log Analytics** e selecione **Espaços de trabalho do Log Analytics** na lista de resultados.
1. Na página **Workspaces do Log Analytics**, escolha **Criar**.
1. Na página **Noções básicas** do assistente Criar workspace do Log Analytics, forneça as informações a seguir e escolha **Revisar + Criar**.
   
    | Propriedade | Valor    |
    |:---------|:---------|
    | Subscription  | Sua assinatura   |
    | Grupo de Recursos    | rg-alpha  |
    | Nome  | LogAnalytics1  |
    | Region    | Leste dos EUA  |

4. Analise as informações e escolha **Criar**.

### Instalar e configurar o agente do Log Analytics na Linux-VM2

1. Na barra de pesquisa do Portal do Azure, insira **Máquinas Virtuais** e selecione **Máquinas Virtuais** na lista de resultados.
1. Na página **Máquinas virtuais**, selecione **Linux-VM2**.
1. Na page da **Linux-VM2**, em **Configurações**, selecione **Extensões + aplicativos**.
1. Escolha **Adicionar** e selecione o **Agente do Log Analytics para Linux** (também conhecido como OmsAgentForLinux). Escolha **Avançar**.
1. Para o ID e a chave do workspace, navegue até **LogAnalytics1 > Configurações > Agentes** em uma guia ou janela separada do navegador.
1. 1. Copie e cole o **ID** e a **Chave Primária do workspace** a partir do workspace LogAnalytics1.
1. Retorne à página de instalação da extensão Linux-VM2 e cole a ID do workspace e a chave do workspace. Escolha **Revisar e Criar** e, em seguida, escolha **Criar**.
1. Após a conclusão da instalação, na página **Extensões + Aplicativos da Linux-VM2**, selecione **AzureNetworkWatcherExtension**.
1. Na página de detalhes da extensão, verifique se **Habilitar a atualização automática** está definido como **Sim**. Caso não esteja, habilite essa opção e selecione **Salvar**.
1. Retorne à página **Extensões + Aplicativos** e selecione a extensão **OmsAgentForLinux**.
1. Na página de detalhes da extensão, verifique se **Habilitar a atualização automática** está definido como **Sim**. Caso não esteja, habilite essa opção e selecione **Salvar**.

### Configurar políticas de arquivamento e retenção de dados do Log Analytics

1. Na barra de pesquisa do portal do Azure, insira **Log Analytics** e selecione **Espaços de trabalho do Log Analytics** na lista de resultados.
1. Na página **Workspaces do Log Analytics**, escolha **LogAnalytics1**.
1. Na página **Workspace do Log Analytics** para LogAnalytics1, selecione **Uso e custos estimados**.
1. Selecione **Retenção de dados** e ajuste o controle deslizante para 60 dias. Escolha **OK**.
1. Na página **Workspace do Log Analytics** para LogAnalytics1, selecione **Uso e custos estimados**.
1. Selecione o **Limite diário**. Escolha **Ativado**. Defina o limite diário para 10 GB e escolha **OK**.

### Habilitar o acesso a um workspace do Log Analytics

1. Na barra de pesquisa do portal do Azure, insira **Log Analytics** e selecione **Espaços de trabalho do Log Analytics** na lista de resultados.
1. Na página **Workspaces do Log Analytics**, escolha **LogAnalytics1**.
1. Selecione **IAM (Controle de acesso)**.
1. Selecione **Adicionar** e, em seguida, **Adicionar atribuição de função**.
1. Na lista de funções, selecione **Leitor do Log Analytics** e escolha **Avançar**.
1. Na página **Membros**, escolha **Selecionar membros** e o grupo de segurança de Examinadores de log de aplicativo. **Escolha Selecionar**.
1. No espaço de **Membros**, escolha **Analisar + Atribuir**.

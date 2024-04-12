---
lab:
  title: 'Exercício: implantar o Log Analytics'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tarefas de habilidades

- Criar um espaço de trabalho do Log Analytics
- Configurar políticas de arquivamento e retenção de dados do Log Analytics
- Habilitar o acesso a um workspace do Log Analytics

## Instruções para o exercício

### Criar um espaço de trabalho do Log Analytics

1. Na barra de pesquisa do portal do Azure, insira **Log Analytics** e selecione **Espaços de trabalho do Log Analytics** na lista de resultados.
1. Na página **Workspaces do Log Analytics**, escolha **Criar**.
1. Na página **Noções básicas** do assistente Criar workspace do Log Analytics, forneça as informações a seguir e escolha **Revisar + Criar**.
   
    | Propriedade | Valor    |
    |:---------|:---------|
    | Subscription  | Sua assinatura   |
    | Grupo de recursos    | rg-alpha  |
    | Nome  | LogAnalytics1  |
    | Região    | Leste dos EUA  |

4. Analise as informações e escolha **Criar**.

### Configurar políticas de arquivamento e retenção de dados do Log Analytics

1. Na barra de pesquisa do portal do Azure, insira **Log Analytics** e selecione **Espaços de trabalho do Log Analytics** na lista de resultados.
1. Na página **Workspaces do Log Analytics**, escolha **LogAnalytics1**.
1. Na página **Workspace do Log Analytics** para LogAnalytics1, selecione **Uso e custos estimados**.
1. Selecione **Retenção de dados** e ajuste o controle deslizante para 60 dias. Selecione **OK**.
1. Na página **Workspace do Log Analytics** para LogAnalytics1, selecione **Uso e custos estimados**.
1. Selecione o **Limite diário**. Escolha **Ativado**. Defina o limite diário para 10 GB e escolha **OK**.

### Habilitar o acesso a um workspace do Log Analytics

1. Na barra de pesquisa do portal do Azure, insira **Log Analytics** e selecione **Espaços de trabalho do Log Analytics** na lista de resultados.
1. Na página **Workspaces do Log Analytics**, escolha **LogAnalytics1**.
1. Selecione **IAM (Controle de acesso)** .
1. Selecione **Adicionar** e, em seguida, **Adicionar atribuição de função**.
1. Na lista de funções, selecione **Leitor do Log Analytics** e escolha **Avançar**.
1. Na página **Membros**, escolha **Selecionar membros** e o grupo de segurança de Examinadores de log de aplicativo. **Escolha Selecionar**.
1. No espaço de **Membros**, escolha **Analisar + Atribuir**.

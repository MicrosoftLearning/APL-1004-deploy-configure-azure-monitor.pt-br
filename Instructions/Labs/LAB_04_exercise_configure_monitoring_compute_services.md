---
lab:
  title: 'Exercício: configurar o monitoramento para serviços de computação'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tarefas de habilidades

- Criar um ponto de extremidade de coleta de dados
- Criar uma regra de coleta de dados
- Adicionar uma coleção de logs do IIS a uma regra de coleta de dados já existente
- Configure o Monitor da Conexão de Rede para uma máquina virtual IaaS do Linux

## Instruções para o exercício

### Criar um ponto de extremidade de coleta de dados

1. Na barra de pesquisa do Portal do Azure, insira **Monitor** e selecione **Monitor** na lista de resultados.
1. Na página **Monitor**, em **Configurações**, escolha **Pontos de Extremidade de Coleta de Dados**.
1. Na página **Pontos de Extremidade de Coleta de Dados**, selecione **Criar**.
1. Na página Criar Pontos de Extremidade de Coleta de Dados, forneça as seguintes configurações e, em seguida, selecione Revisar + Criar.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Nome do ponto de extremidade  | IaaSVMCollectionEndpoint   |
    | Subscription  | Sua assinatura  |
    | Grupo de recursos    | rg-alpha  |
    | Região    | Leste dos EUA  |

5. Revise as configurações e escolha **Criar**.

### Criar uma regra de coleta de dados

1. Na barra de pesquisa do Portal do Azure, insira **Monitor** e selecione **Monitor** na lista de resultados.
1. Na página **Monitor**, em **Configurações**, escolha **Regras de Coleta de Dados**.
1. Na página **Regras de Coleta de Dados**, selecione **Criar**.
1. Na página **Criar Regra de Coleta de Dados**, defina as seguintes configurações e selecione **Próximo**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Nome da regra  | WinVMDCR   |
    | Subscription  | Sua assinatura   |
    | Grupo de recursos    | rg-alpha  |
    | Região    | Leste dos EUA  |
    | Tipo de plataforma | Windows  |
    | Ponto de extremidade da coleta de dados  | IaaSVMCollectionEndpoint   |

5. Na página **Recursos**, selecione **Adicionar Recursos**.
1. Na página **Selecionar um escopo**, marque a caixa de seleção **WS-VM1** e selecione **Aplicar**.
1. Na página **Criar Regra de Coleta de Dados**, selecione **Próximo**.
1. Na página **Coletar e Entregar**, selecione **Adicionar fonte de dados**.
1. Na página **Adicionar fonte de dados**, selecione **Logs de Eventos do Windows**. Na categoria **Aplicativo**, habilite as categorias **Crítico** e **Erro**. Na categoria **Segurança**, selecione a categoria **Falha de Auditoria**. Na categoria **Sistema**, habilite as categorias **Crítico** e **Erro**. 
1. Selecione **Próximo**.
1. Na página **Destino**, defina as seguintes configurações:

    | Propriedade | Valor    |
    |:---------|:---------|
    | Tipo de destino  | Logs do Azure Monitor   |
    | Subscription  | Sua assinatura   |
    | Conta ou namespace  | LogAnalytics1  |

12. Selecione **Adicionar origem de dados**.
1. Selecione **Revisar + Criar** e, em seguida, **Criar**.


### Adicionar uma coleção de logs do IIS a uma regra de coleta de dados já existente

1. Na barra de pesquisa do Portal do Azure, insira **Monitor** e selecione **Monitor** na lista de resultados.
1. Na página **Monitor**, em **Configurações**, escolha **Regras de Coleta de Dados**.
1. Selecione a regra **WinVMDRC** em rg-alpha.
1. Em **Configuração**, selecione **Fontes de Dados**.
1. Na página **Fontes de Dados**, selecione **Adicionar**.
1. Na página **Adicionar Fonte de Dados**, selecione **Logs do IIS**.
1. Selecione **Próximo**.
1. Na página **Destino**, defina as seguintes configurações:

    | Propriedade | Valor    |
    |:---------|:---------|
    | Tipo de destino  | Logs do Azure Monitor   |
    | Subscription  | Sua assinatura   |
    | Conta ou namespace  | LogAnalytics1  |

9. Selecione **Adicionar origem de dados**.

### Configure o Monitor da Conexão de Rede para uma máquina virtual IaaS do Linux

1. Na barra de pesquisa do portal do Azure, digite **Observador de Rede** e selecione **Observador de Rede** na lista de resultados.
1. Em **Monitoramento**, selecione **Monitor de Conexão**.
1. Na página **Monitor de Conexão**, selecione **Criar**.
1. Na página **Básicos** do assistente **Criar Monitor de Conexão**, forneça as seguintes informações e selecione **Próximo**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Nome do Monitor da Conexão  | LinuxVMPubIP   |
    | Subscription  | Sua assinatura   |
    | Região    | Leste dos EUA  |
    | Workspace | LogAnalytics1  |

5. Na página **Adicionar detalhes do grupo de teste**, digite o nome **LinuxIPTest** e selecione **Adicionar fontes**.
1. Na página **Adicionar Fontes**, selecione **Pontos de Extremidade do Azure** e defina o tipo como **Máquinas virtuais**. Selecione **Sub-rede** e ative a caixa de seleção **Linux-VM**. Selecione **Adicionar Pontos de Extremidade**.
1. Selecione **Adicionar Configuração de Teste**. 
1. Na página **Adicionar Configuração de Teste**, digite o nome **DefaultHTTP** e, em seguida, selecione **Adicionar Configuração de Teste**.
1. Selecione **Adicionar Destinos**. Selecione **Azure Pontos de Extremidade** e defina o tipo como **Máquinas virtuais**. Selecione **Sub-rede** e ative a caixa de seleção **WS-VM1**. Selecione **Adicionar Pontos de Extremidade**.
1. Selecione **Adicionar Grupo de Teste**.
1. Selecione **Revisar e Criar** e, em seguida, **Criar**.

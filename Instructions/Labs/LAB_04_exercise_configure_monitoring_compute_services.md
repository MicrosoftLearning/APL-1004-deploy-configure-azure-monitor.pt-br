---
lab:
  title: 'Exercício: configurar o monitoramento para serviços de computação'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tarefas de habilidades

- Criar um ponto de extremidade de coleta de dados
- Criar uma regra de coleta de dados
- Adicionar uma coleta de logs do IIS a uma regra de coleta de dados existente
- Configurar o Monitor da conexão de rede para uma máquina virtual IaaS do Linux

## Instruções para o exercício

### Criar um ponto de extremidade de coleta de dados

1. Na barra de pesquisa do portal do Azure, digite Monitor e, em seguida, selecione Monitor na lista de resultados.
1. Na página Monitor, em Configurações, escolha Pontos de Extremidade de coleta de dados.
1. Na página Pontos de extremidade de coleta de dados, escolha Criar.
1. Na página Criar ponto de extremidade de coleta de dados, forneça as seguintes configurações e escolha Analisar + Criar.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Nome do ponto de extremidade  | IaaSVMCollectionEndpoint   |
    | Subscription  | Sua assinatura  |
    | Grupo de recursos    | rg-alpha  |
    | Região    | Leste dos EUA  |

5. Analise as configurações e escolha Criar.

### Criar uma regra de coleta de dados

1. Na barra de pesquisa do portal do Azure, digite **Monitor** e selecione **Monitor** na lista de resultados.
1. Na página **Monitor**, em **Configurações**, selecione **Regras de coleta de dados**.
1. Na página **Regras de coleta de dados**, selecione **Criar**.
1. Na página **Criar regra de coleta de dados**, defina as seguintes configurações e escolha **Avançar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Nome da regra  | WinVMDCR   |
    | Subscription  | Sua assinatura   |
    | Grupo de recursos    | rg-alpha  |
    | Região    | Leste dos EUA  |
    | Tipo de plataforma | Windows  |
    | Ponto de extremidade da coleta de dados  | IaaSVMCollectionEndpoint   |

5. Na página **Recursos**, selecione **Adicionar recursos**.
1. Na página **Selecionar um escopo**, habilite a caixa de seleção **WS-VM1** e escolha **Aplicar**.
1. Na página **Criar regra de coleta de dados**, escolha **Avançar**.
1. Na página **Coletar e entregar**, selecione **Adicionar fonte de dados**.
1. Na página **Adicionar fonte de dados**, selecione **Logs de eventos do Windows**. Na categoria Aplicativo, habilite as categorias **Crítico** e **Erro**. Na categoria **Segurança**, selecione a categoria **Falha de auditoria**. Na categoria **Sistema**, habilite as categorias **Crítico** e **Erro**. 
1. Selecione **Próximo**.
1. Na página **Destino**, defina as seguintes configurações:

    | Propriedade | Valor    |
    |:---------|:---------|
    | Tipo de destino  | Logs do Azure Monitor   |
    | Subscription  | Sua assinatura   |
    | Conta ou namespace  | LogAnalytics1  |

12. Escolha **Adicionar fonte de dados**.
1. Selecione **Analisar + Criar** e escolha **Criar**.


### Adicionar uma coleta de logs do IIS a uma regra de coleta de dados existente

1. Na barra de pesquisa do portal do Azure, digite **Monitor** e selecione **Monitor** na lista de resultados.
1. Na página **Monitor**, em **Configurações**, selecione **Regras de coleta de dados**.
1. Selecione a regra **WinVMDRC** em rg-alpha.
1. Em **Configuração**, selecione **Fontes de dados**.
1. Na página **Fontes de dados**, selecione **Adicionar**.
1. Na página **Adicionar fonte de dados**, selecione **Logs do IIS**.
1. Selecione **Próximo**.
1. Na página **Destino**, defina as seguintes configurações:

    | Propriedade | Valor    |
    |:---------|:---------|
    | Tipo de destino  | Logs do Azure Monitor   |
    | Subscription  | Sua assinatura   |
    | Conta ou namespace  | LogAnalytics1  |

9. Escolha **Adicionar fonte de dados**.

### Configurar o Monitor da conexão de rede para uma máquina virtual IaaS do Linux

1. Na barra de pesquisa do portal do Azure, digite **Observador de Rede** e selecione **Observador de Rede** na lista de resultados.
1. Em **Monitoramento**, escolha **Monitor da Conexão**.
1. Na página **Monitor da Conexão**, selecione **Criar**.
1. Na página **Noções básicas** do assistente Criar Monitor da Conexão, forneça as informações a seguir e escolha **Avançar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Nome do Monitor da Conexão  | LinuxVMPubIP   |
    | Subscription  | Sua assinatura   |
    | Região    | Leste dos EUA  |
    | Workspace | LogAnalytics1  |

5. Na página **Adicionar detalhes do grupo de teste**, digite o nome **LinuxIPTest** e selecione **Adicionar fontes**.
1. Na página **Adicionar fontes**, selecione **Pontos de extremidade do Azure** e defina o tipo como **Máquinas virtuais**. Selecione **Sub-rede** e habilite a caixa de seleção **Linux-VM**. Clique em **Adicionar pontos de extremidade**.
1. Selecione **Adicionar configuração de teste**. 
1. Na página **Adicionar configuração de teste**, digite o nome **DefaultHTTP** e selecione **Adicionar configuração de teste**.
1. Escolha **Adicionar destinos**. Selecione **Pontos de extremidade do Azure** e defina o tipo como **Máquinas virtuais**. Selecione **Sub-rede** e habilite a caixa de seleção **WS-VM1**. Selecione **Adicionar pontos de extremidade**.
1. Escolha **Adicionar grupo de teste**.
1. Selecione **Analisar e criar** e, em seguida, **Criar**.

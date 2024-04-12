---
lab:
  title: 'Exercício: configurar alertas'
  module: Guided Project - Deploy and configure Azure Monitor
---

## Tarefas de habilidades

- Criar um grupo de ações para enviar um email
- Criar um alerta de utilização da CPU da máquina virtual

## Instruções para o exercício

### Criar um grupo de ações para enviar um email

1. Na barra de pesquisa do portal do Azure, digite **Monitor** e selecione **Monitor** na lista de resultados.
1. No menu de navegação, selecione **Alertas**.
1. Escolha os **Grupos de ações**.
1. Na página **Grupos de ações**, escolha **Criar**.
1. Na página **Noções básicas** do assistente Criar grupo de ações, defina as configurações a seguir e escolha **Avançar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Subscription  | Sua assinatura   |
    | Grupo de recursos  | rg-alpha   |
    | Region    | Global  |
    | Nome do grupo de ações | NotifyCPU  |
    | Nome para Exibição  | NotifyCPU  |

6. Na página **Notificações**, defina o tipo de notificação para **Email/mensagem SMS/Push/Voz** e defina o Nome como **NotificationEmail**. Selecione o ícone **Editar** (lápis).
1. Em Email/Mensagem SMS/Push/Voz, ative a caixa de seleção **Email** e digite o endereço **prime@fabrikam.com**. Selecione **OK**. 
1. Escolha **Analisar e criar**. Escolha **Criar**.


### Criar um alerta de utilização da CPU da máquina virtual

1. Na barra de pesquisa do portal do Azure, digite **rg-alpha** e selecione **rg-alpha** na lista de resultados.
1. Na lista de itens no grupo de recursos, escolha **Linux-VM2**.
1. Na página **Propriedade do Linux-VM2**, escolha **Alertas** em **Monitoramento**.
1. Na página **Alertas**, selecione **Criar** e **Regra de alerta**.
1. Na página **Condição** do assistente Criar uma regra de alerta, defina o Nome do sinal como **Porcentagem de CPU**. Use as configurações padrão e selecione **Avançar**.
1. Na página **Ações**, escolha **Selecionar grupo de ações**.
1. Na página **Selecionar grupos de ações**, escolha **NotifyCPU** e **Selecionar**.
1. Na página **Detalhes**, insira o nome da regra de alerta **HighCPU**. Selecione **Analisar e criar** e, em seguida, **Criar**.

## Limpar subscrição

Para limpar a subscrição, exclua o grupo de recursos **rg-alpha** e exclua o grupo de segurança **Examinadores de log do aplicativo**.

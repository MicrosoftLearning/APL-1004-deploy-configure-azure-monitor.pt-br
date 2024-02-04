---
lab:
  title: Preparar seu ambiente do Azure
  module: Guided Project - Deploy and configure Azure Monitor
---

## Prepare seu BYOS (bring-your-own-subscription)

Este conjunto de exercícios de laboratório considera que você tem permissões de administrador global para uma assinatura do Azure.

1. Na barra de pesquisa do Portal do Azure, digite **Grupos de Recursos** e selecione **Grupos de Recursos** na lista de resultados.
1. Na página **Grupos de recursos**, selecione **Criar**.
1. Na página **Criar um grupo de recursos**, selecione a assinatura e digite o nome rg-alpha. Defina a região como Leste dos EUA, escolha **Analisar + Criar** e escolha **Criar**.

> [!NOTE]
> Esse conjunto de exercícios considera que você opta por implantar na região Leste dos EUA, mas é possível alterar isso para outra região, se desejar. Lembre-se: cada vez que você vir Leste dos EUA mencionado nestas instruções, você precisará substituir a região escolhida.

## Criar grupo de segurança Examinadores de log de aplicativo

Neste exercício, você cria um grupo de segurança do Entra ID.

1. Na barra de pesquisa do portal do Azure, insira Azure Active Directory (ou Entra ID) e Azure Active Directory (ou Entra ID) na lista de resultados.
1. Na página **Diretório padrão**, selecione **Grupos**.
1. Na página **Grupos**, escolha **Novo grupo**.
1. Na página **Novo grupo**, forneça os valores na tabela a seguir e escolha **Criar**.


    | Propriedade | Valor    |
    |:---------|:---------|
    | Tipo de grupo  | Segurança   |
    | Nome do grupo  | AppLogExaminers   |
    | Descrição do grupo  | AppLogExaminers   |


## Implantar e configurar o WS-VM1

Neste exercício, você implanta e configura uma máquina virtual do Windows Server.

1. Na barra de pesquisa do Portal do Azure, insira **Máquinas Virtuais** e selecione **Máquinas Virtuais** na lista de resultados.
1. Na página **Máquinas virtuais**, escolha **Criar** e selecione **Máquina virtual do Azure**.
1. Na página **Noções básicas** do assistente Criar uma máquina virtual, selecione as configurações a seguir e escolha **Analisar + Criar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Subscription  | Sua assinatura   |
    | Grupo de recursos    | rg-alpha  |
    | Nome da máquina virtual  | WS-VM1   |
    | Região    | Leste dos EUA  |
    | Opções de disponibilidade  | Sem necessidade de redundância de infraestrutura  |
    | Tipo de segurança | Standard   |
    | Imagem | Datacenter do Windows Server 2022: Azure Edition – x64 Gen 2  |
    | Arquitetura de VMs;   | x64  |
    | Tamanho  | Standard_D4s_v3 – 4 vcpus, 16 GiB de memória  |
    | Conta de administrador | prime  |
    | Senha  | [Selecione uma senha segura exclusiva] P@ssw0rdP@ssw0rd   |
    | Portas de entrada | RDP 3389   |

4. Examine as configurações e selecione **Criar**.
1. Aguarde até que a implantação seja concluída. Quando a implantação for concluída, escolha **Ir para recursos**.
1. Na página de **propriedades do WS-VM1**, escolha **Rede**.
1. Na página **Rede**, selecione a regra de RDP. 
1. No espaço de regra de RDP, altere a Origem para Meu endereço IP e escolha **Salvar**.

    Isso restringe as conexões de RDP de entrada ao endereço IP usado no momento.

9. Na página **Rede**, escolha **Adicionar regra de porta de entrada**.
1. Na página **Adicionar regra de segurança de entrada**, defina as configurações a seguir e escolha **Adicionar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Fonte  | Qualquer  |
    | Intervalos de portas de origem    | *   |
    | Destino  | Qualquer   |
    | Ação    | Permitir  |
    | Prioridade  | 310   |
    | Nome  | AllowAnyHTTPInbound  |

11. Na página **WS-VM1**, escolha **Conectar**.
1. Em RDP nativo, escolha **Selecionar**.
1. Na página **RDP nativo**, escolha **Baixar arquivo RDP** e abra o arquivo. Ao abrir o arquivo RDP, abre-se a caixa de diálogo Conexão de Área de Trabalho Remota.
1. Na caixa de diálogo **Segurança do Windows**, selecione **Mais Opções** e, em seguida, escolha Usar uma conta diferente.
1. Digite o nome de usuário como .\prime e a senha segura que você escolheu na Etapa 3 e, em seguida, escolha **OK**.
1. Quando estiver conectado à máquina virtual do Windows Server, clique com o botão direito do mouse na dica **Iniciar** e escolha **Windows PowerShell (administrador)**.
1. No prompt de comando elevado, digite o seguinte comando e pressione **Enter**.
    Install-WindowsFeature Web-Server  -IncludeAllSubFeature -IncludeManagementTools 
1. Quando a instalação for concluída, execute o seguinte comando e alterne para o diretório raiz do servidor Web.
    Cd c:\inetpub\wwwroot\
1. Execute o comando a seguir.
    Wget https://raw.githubusercontent.com/Azure-Samples/html-docs-hello-world/master/index.html-OutFile index.html


## Implantar e configurar o LX-VM2

Neste exercício você vai implantar e configurar uma máquina virtual Linux.

1. Na barra de pesquisa do Portal do Azure, insira **Máquinas Virtuais** e selecione **Máquinas Virtuais** na lista de resultados.
1. Na página **Máquinas virtuais**, escolha **Criar** e selecione **Máquina virtual do Azure**.
1. Na página **Noções básicas** do assistente Criar uma máquina virtual, selecione as configurações a seguir e escolha **Analisar + Criar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Subscription  | Sua assinatura   |
    | Grupo de recursos    | rg-alpha  |
    | Nome da máquina virtual  | Linux-VM2   |
    | Região    | Leste dos EUA  |
    | Opções de disponibilidade  | Sem necessidade de redundância de infraestrutura  |
    | Tipo de segurança | Standard   |
    | Imagem | Ubuntu Server 20.04 LTs – x64 Gen2  |
    | Arquitetura de VMs;   | x64  |
    | Tamanho  | Standard_D2s_v3 – 2 vcpus, 8 GiB de memória  |
    | Tipo de autenticação   | Senha  |
    | Nome de Usuário  | Prime   |
    | Senha  | [Selecione uma senha segura exclusiva] P@ssw0rdP@ssw0rd   |
    | Porta de entrada públicas  | Nenhum   |

4. Analise as informações e escolha **Criar**.
1. Depois que a VM for implantada, abra a página de **Propriedades da VM** e escolha **Extensões + Aplicativos** em **Configurações**.
1. Escolha **Adicionar** e selecione o **Observador de Rede para Linux**. Selecione **Avançar** e, em seguida, escolha **Analisar e criar**. Escolha **Criar**.
1. Configure o AzureNetworkWatcherExtension e a extensão OmsAgentForLinux para que sejam atualizados automaticamente.


## Implantar um aplicativo Web com um Banco de Dados SQL

1. Verifique se você está conectado ao portal do Azure.
1. No navegador, abra uma nova guia e acesse https://github.com/Azure/azure-quickstart-templates/tree/master/quickstarts/microsoft.web/web-app-sql-database
1. Na página do GitHub, escolha **Implantar no Azure**.
1. Uma nova guia é aberta. Se necessário, entre novamente no Azure com a conta que tem privilégios de Administrador global.
1. Na página **Básico**, selecione **Editar modelo**.
1. No editor de modelos, exclua o conteúdo das linhas 158 a 174 inclusive e exclua a "," na linha 157. Selecione **Salvar**.
1. Na página **Básico**, insira as seguintes informações e escolha **Avançar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Subscription  | Sua assinatura   |
    | Grupo de recursos    | rg-alpha  |
    | Região    | Leste dos EUA  |
    | Nome do Sku  | F1  |
    | Capacidade de Sku  | 1   |
    | Logon de Administrador do SQL   | prime  |
    | Senha de Logon de Administrador do SQL  | [Selecione uma senha segura exclusiva] P@ssw0rdP@ssw0rd   |

8. Analise as informações e selecione **Criar**.
1. Após a conclusão da implantação, selecione **Ir para o grupo de recursos**.

## Implantar um aplicativo Web do Linux

1. Verifique se você está conectado ao portal do Azure.
1. No navegador, abra uma nova guia e acesse https://learn.microsoft.com/en-us/samples/azure/azure-quickstart-templates/webapp-basic-linux/
1. Na página do GitHub, escolha **Implantar no Azure**.
1. Na página **Básico**, insira as seguintes informações e escolha **Avançar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Subscription  | Sua assinatura   |
    | Grupo de recursos    | rg-alpha  |
    | Região    | Leste dos EUA  |
    | Nome do aplicativo Web  | AzureLinuxAppWXYZ (atribua um número aleatório aos quatro caracteres finais do nome)  |
    | Sku   | S1   |
    | Versão do Linux Fx  | php|7.4  |

5. Analise as informações e escolha **Criar**.

---
lab:
  title: Preparar seu ambiente do Azure
  module: Guided Project - Deploy and configure Azure Monitor
---

## Prepare sua BYOS (trazer sua própria assinatura)

Este conjunto de exercícios de laboratório pressupõe que você tenha permissões de administrador global em uma assinatura do Azure.

1. Na barra de pesquisa do portal do Azure, digite **Grupos de Recursos** e selecione **Grupos de recursos** na lista de resultados.
1. Na página **Grupos de Recursos**, selecione **Criar**.
1. Na página **Criar um Grupo de Recursos**, selecione sua assinatura e digite o nome rg-alpha. Defina a região como Leste dos EUA, escolha **Revisar + Criar** e escolha **Criar**.

> [!NOTE]
> Este conjunto de exercícios pressupõe que você opte por implantar na região Leste dos EUA, mas você pode alterar isso para outra região, se desejar. Apenas lembre-se de que cada vez que você vir o Leste dos EUA mencionado nestas instruções, você precisará substituir pela região escolhida.

## Criar grupo de segurança examinadores de log de aplicativo

Neste exercício, você cria um grupo de segurança do Entra ID.

1. Na barra de pesquisa do portal do Azure, insira Azure Active Directory (ou ID Entra) na lista de resultados.
1. Na página **Diretório Padrão**, selecione **Grupos**.
1. Na página **Grupos**, selecione **Novo Grupo**.
1. Na página **Novo Grupo**, insira os valores da tabela a seguir e selecione **Criar**.


    | Propriedade | Valor    |
    |:---------|:---------|
    | Tipo de grupo  | Segurança   |
    | Nome do grupo  | Examinadores de log de aplicativo   |
    | Descrição do grupo  | Examinadores de log de aplicativo   |


## Implantar e configurar o WS-VM1

Neste exercício, você vai implantar e configurar uma máquina virtual do Windows Server. 

1. Na barra de pesquisa do portal do Azure, insira **Máquinas Virtuais** e selecione **Máquinas Virtuais** na lista de resultados.
1. Na página **Máquinas Virtuais**, selecione **Criar** e selecione **Máquina Virtual do Azure**.
1. Na página **Básicos** do assistente Criar uma Máquina Virtual, selecione as seguintes configurações e, em seguida, escolha **Revisar + Criar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Subscription  | Sua assinatura   |
    | Grupo de recursos    | rg-alpha  |
    | Nome da máquina virtual  | WS-VM1   |
    | Região    | Leste dos EUA  |
    | Opções de disponibilidade  | Sem necessidade de redundância de infraestrutura  |
    | Tipo de segurança | Standard   |
    | Imagem | Windows Server 2022 Datacenter: Azure Edition – x64 Gen2  |
    | Arquitetura de VMs;   | x64  |
    | Tamanho  | Standard_D4s_v3 – 4 vcpus, 16 GiB de memória  |
    | Conta de administrador | prime  |
    | Senha  | [Selecione uma senha segura e exclusiva] P@ssw0rdP@ssw0rd   |
    | Portas de entrada | RDP 3389   |

4. Examine as configurações e selecione **Criar**.
1. Aguarde até que a implantação seja concluída. Quando a implantação for concluída, selecione **Ir para recursos**.
1. Na página **propriedades do WS-VM1**, selecione **Rede**.
1. Na página **Rede**, selecione a regra RDP. 
1. No espaço da regra RDP, altere a Origem para Meu endereço IP e selecione **Salvar**.

    Isso restringe as conexões RDP de entrada ao endereço IP que você está usando atualmente.

9. Na página **Rede**, selecione **Adicionar regra de porta de entrada**.
1. Na página **Adicionar regra de segurança de entrada**, defina as seguintes configurações e selecione **Adicionar**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Fonte  | Qualquer  |
    | Intervalos de portas de origem    | *   |
    | Destino  | Qualquer   |
    | Serviço   | HTTP  |
    | Ação    | Permitir  |
    | Prioridade  | 310   |
    | Nome  | AllowAnyHTTPInbound  |

11. Na página **WS-VM1**, selecione **Conectar**.
1. Em RDP nativo, selecione **Selecionar**.
1. Na página **RDP Nativo**, selecione **Baixar arquivo RDP** e, em seguida, abra o arquivo. Ao abrir o arquivo RDP, a caixa de diálogo Conexão da Área de Trabalho Remota também será aberta.
1. Na caixa de diálogo **Segurança do Windows**, selecione **Mais Opções** e, em seguida, escolha Usar uma conta diferente.
1. Digite o nome de usuário como .\prime e a senha é a senha segura que você escolheu na Etapa 3 e clique em **OK**.
1. Quando estiver conectado à máquina virtual do Windows Server, clique com o botão direito na dica **Iniciar** e escolha **Windows PowerShell (Admin)**.
1. No prompt de comando elevado, digite o seguinte comando e pressione **Enter**.
    Install-WindowsFeature Web-Server  -IncludeAllSubFeature -IncludeManagementTools 
1. Quando a instalação for concluída, execute o seguinte comando para mudar para o diretório raiz do servidor web.
    cd c:\inetpub\wwwroot\
1. Execute o comando a seguir.
    Wget https://raw.githubusercontent.com/Azure-Samples/html-docs-hello-world/master/index.html -OutFile index.html


## Implantar e configurar o LX-VM2

Neste exercício você implantará e configurará uma máquina virtual Linux.

1. Na barra de pesquisa do portal do Azure, insira **Máquinas Virtuais** e selecione **Máquinas Virtuais** na lista de resultados.
1. Na página **Máquinas Virtuais**, selecione **Criar** e selecione **Máquina Virtual do Azure**.
1. Na página **Básicos** do assistente Criar uma Máquina Virtual, selecione as seguintes configurações e, em seguida, escolha **Revisar + Criar**.

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
    | Senha  | [Selecione uma senha segura e exclusiva] P@ssw0rdP@ssw0rd   |
    | Porta de entrada públicas  | Nenhum   |

4. Revise as informações e selecione **Criar**.
1. Após a implantação da VM, abra a página **Propriedades da VM** e selecione **Extensões + Aplicativos** em **Configurações**.
1. Escolha **Adicionar** e selecione **Agente Observador de Rede para Linux**. Selecione **Next** e, em seguida selecione, **Revisar e Criar**. Escolha **Criar**.
1. Configure as extensões AzureNetworkWatcherExtension e OmsAgentForLinux para que sejam atualizados automaticamente.


## Implantar um aplicativo Web com um Banco de Dados SQL

1. Conecte-se ao portal do Azure.
1. Abra uma nova guia do navegador e navegue até https://github.com/Azure/azure-quickstart-templates/tree/master/quickstarts/microsoft.web/web-app-sql-database
1. Na página do GitHub, selecione **Implantar no Azure**.
1. Uma nova guia é aberta. Se necessário, entre novamente no Azure com a conta que tem privilégios de administrador global.
1. Na página **Básico**, selecione **Editar modelo**.
1. No editor de modelos, exclua o conteúdo das linhas 158 a 174 (inclusive) e exclua a vírgula “,” na linha 157. Selecione **Salvar**.
1. Na página **Básico**, forneça as informações a seguir e escolha **Próximo**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Subscription  | Sua assinatura   |
    | Grupo de recursos    | rg-alpha  |
    | Região    | Leste dos EUA  |
    | Nome do Sku  | F1  |
    | Capacidade de Sku  | 1   |
    | Logon de Administrador do SQL   | prime  |
    | Senha de Logon de Administrador do SQL  | [Selecione uma senha segura e exclusiva] P@ssw0rdP@ssw0rd   |

8. Revise as informações apresentadas e selecione **Criar**.
1. Após a conclusão da implantação, escolha **Ir para o grupo de recursos**.

## Implantar um aplicativo web do Linux

1. Conecte-se ao portal do Azure.
1. Abra uma nova guia do navegador e acesse https://learn.microsoft.com/en-us/samples/azure/azure-quickstart-templates/webapp-basic-linux/
1. Na página do GitHub, selecione **Implantar no Azure**.
1. Na página **Básico**, forneça as informações a seguir e escolha **Próximo**.

    | Propriedade | Valor    |
    |:---------|:---------|
    | Subscription  | Sua assinatura   |
    | Grupo de recursos    | rg-alpha  |
    | Região    | Leste dos EUA  |
    | Nome do aplicativo Web  | AzureLinuxAppWXYZ (atribua um número aleatório aos quatro caracteres finais do nome)  |
    | Sku   | S1   |
    | Versão Linux FX  | php|7.4  |

5. Revise as informações e selecione **Criar**.

# dio-azure7
entrega projeto azure

Componentes da arquitetura do Azure
Regiões disponíveis variam os preços, conforme regras e impostos locais.
60 regiões, mais de 140 países.
As regiões são compostas de um ou mais datacenters muito próximos - conectados entre si.
Eles fornecem flexibilidade e escala para reduzir a latência do cliente.
regiões preservam a residencia dos dados com uma oferta abrangente de conformidade.

Pares de região
no mínimo 300 milhas de separação entre pares de regiões
replicação automática para alguns serviços
recuperação de região priorizada em caso de interrupção
as atualizações são distribuídas sequencialmente

Curiosamente a região par do Brasil (sul do Brasil) é o Centro - Sul dos EUA
Regiões soberanas do Azure: instancia separada do Azure, exclusiva ao Governo dos EUA.
Na China, a Microsoft foi o primeiro provedor estrangeiro de serviço de nuvem pública e é fisicamente separada dos serviços, operado pela 21ViaNet - com todos os dados dentro da China.
Recursos do Azure

**No Microsoft Azure, um “recurso” é qualquer serviço ou componente que você cria e gerencia na nuvem (como máquinas virtuais, bancos de dados, redes virtuais, contas de armazenamento). Esses recursos precisam estar organizados dentro de um “grupo de recursos”, e a regra é clara: cada recurso só pode existir em um único grupo de recursos por vez

VM - virtual machine
contas de armazenamento
redes virtuais
serviços de aplicativos
banco de dados SQL
funções: São os blocos fundamentais que compõem suas soluções na nuvem.

grupos de recursos
Web + BD, VM, armazenamento - em um grupo
um grupo de recursos é um conteiner que voce usa para gerenciar e agregar recursos em uma única unidade.
Ciclo de vida: É recomendado colocar no mesmo grupo os recursos que compartilham o mesmo ciclo de vida (implantação, atualização e exclusão).

Se você criar uma máquina virtual, ela estará vinculada a um único grupo de recursos.
Para reorganizar, é possível mover o recurso para outro grupo ou até para outra assinatura, mas nunca duplicá-lo em múltiplos grupos.
Benefício: Evita confusão e garante que cada recurso tenha um escopo único de gerenciamento.
Em resumo: recursos são os serviços que você cria no Azure, e cada um deles só pode pertencer a um único grupo de recursos. Essa estrutura é essencial para manter organização, governança e controle de custos na nuvem.

Assinaturas do Azure
uma conta pode ter várias assinaturas diferentes - desenvolvimento, teste e produção.
uma fatura por assinatura.
essa pode ser uma estratégia para dividir custos por projeto
rlatórios de cobrança e faturas separados para cada assinatura, assim como possibilidade de limitar o controle de acesso

Grupos de gerenciamento (Management Groups)

São o nível mais alto da hierarquia.
Permitem organizar várias assinaturas do Azure sob uma mesma estrutura administrativa.
Úteis para aplicar políticas e controles de governança em larga escala.
Assinaturas (Subscriptions)

Cada assinatura representa um contrato de uso do Azure, com limites de cobrança e acesso.
Dentro de uma assinatura, você pode criar diversos grupos de recursos.
É o ponto onde se controla custos e faturamento.
Grupos de recursos (Resource Groups)

São contêineres lógicos que agrupam recursos relacionados.
Servem para organizar e gerenciar recursos que compartilham ciclo de vida.
Cada recurso só pode pertencer a um único grupo de recursos.
Recursos (Resources)

São os elementos finais: máquinas virtuais, bancos de dados, contas de armazenamento, redes virtuais, etc.
Eles são criados dentro de um grupo de recursos e não podem existir fora dele.
Ícones na imagem (computador, banco SQL, engrenagens) representam exemplos desses recursos.
Em resumo: a imagem mostra que no Azure tudo começa em grupos de gerenciamento, que contêm assinaturas, que por sua vez contêm grupos de recursos, e dentro deles estão os recursos. Essa estrutura garante organização, governança e controle eficiente.

Passo a passo básico no Portal Azure

Entrar no Portal AzureAcesse portal.azure.com e faça login com sua conta.
Selecionar “Grupos de recursos”No menu lateral, clique em Grupos de recursos.
Em seguida, clique em Criar.
Preencher informações obrigatóriasAssinatura: escolha a assinatura do Azure onde o grupo será criado.
Nome do grupo de recursos: insira um nome único e descritivo (ex.: Dev-Test, Prod-DB).
Região: selecione a localização (ex.: Brazil South ou East US).Essa região define onde os metadados do grupo serão armazenados.
Os recursos dentro do grupo podem estar em outras regiões, mas é recomendável escolher a mesma região para simplificar a gestão.
Revisar e criarClique em Examinar + criar.
Confirme os dados e selecione Criar.
Confirmar criaçãoEm poucos segundos o grupo estará disponível.
Você pode acessá-lo pela lista de grupos de recursos ou pela notificação exibida no topo do portal
PROJETO ENTREGUE 5
Computação e rede
Serviços de computação do Azure
Serviço sob demanda que fornece recursos de computação, como discos, processadores, memória, rede e sistemas operacionais.
Virtual machines:
conjuntos de dimensionamento
permite balancear a carga para dimensionar os recursos automaticamente.
Conjunto de disponibilidade 
domínio de falha (3) e domínio de atualização 
Área de trabalho virtual do Azure
A Área de Trabalho Virtual do Azure (Azure Virtual Desktop) é um serviço de virtualização de desktops e aplicativos que permite acessar um ambiente Windows completo ou apenas aplicativos específicos de forma remota, segura e escalável, a partir de qualquer dispositivo. Em outras palavras, você pode ter um “PC na nuvem” rodando Windows 10, Windows 11 ou Windows Server, sem precisar manter infraestrutura local.

Serviço de VDI (Virtual Desktop Infrastructure) baseado em nuvem.
Permite criar e gerenciar ambientes de trabalho virtuais hospedados no Azure.
Substitui soluções tradicionais de Remote Desktop Services (RDS).
🔹 Principais recursos

Experiência completa do Windows: acesso ao Windows 10, Windows 11 ou Windows Server.
Sessões múltiplas: vários usuários podem compartilhar a mesma máquina virtual, reduzindo custos.
RemoteApp: publicar apenas aplicativos específicos em vez de todo o desktop.
Integração com Microsoft 365: otimizado para rodar aplicativos como Word, Excel, Teams em cenários multiusuários.
Flexibilidade: escolha entre desktops persistentes (cada usuário tem seu ambiente) ou não persistentes (ambientes compartilhados).
Escalabilidade automática: aumenta ou reduz capacidade conforme demanda, otimizando custos.
Segurança e conformidade: dados ficam centralizados no Azure, com políticas de acesso e proteção integradas.
🔹 Como funciona na prática

Configuração no Azure: você cria conjuntos de máquinas virtuais (host pools).
Publicação: decide se vai disponibilizar desktops completos ou apenas aplicativos.
Acesso do usuário: os usuários se conectam via cliente de Área de Trabalho Remota (Windows, macOS, iOS, Android, navegador).
Gerenciamento centralizado: tudo é administrado pelo portal do Azure, PowerShell, CLI ou API REST.
🔹 Benefícios para empresas

Redução de custos: aproveita sessões múltiplas e paga apenas pelo uso.
Mobilidade: colaboradores acessam seus ambientes de qualquer lugar.
Simplificação de TI: elimina a necessidade de manter servidores locais de RDS.
Segurança: dados não ficam nos dispositivos dos usuários, mas centralizados na nuvem.
Serviços de conteiner
Serviços de contêiner no Azure são soluções que permitem criar, executar e gerenciar aplicativos em contêineres (como Docker) de forma escalável e segura. Eles oferecem desde execução simples de contêineres até orquestração avançada com Kubernetes.
🔹 O que são contêineres

Definição: Pacotes leves que incluem código, bibliotecas e dependências necessárias para executar um aplicativo (Paas).
Benefício: Garantem consistência entre ambientes (desenvolvimento, teste e produção).
Uso comum: Microsserviços, aplicações modernas, integração contínua (CI/CD).

O Azure Kubernetes Service (AKS) é o serviço gerenciado de Kubernetes da Microsoft que simplifica a criação, execução e administração de aplicações em contêineres. Ele elimina grande parte da complexidade de configurar e manter clusters Kubernetes, permitindo que você foque nos aplicativos em vez da infraestrutura.

O Azure Functions é um serviço de computação sem servidor (serverless) que permite executar pequenos blocos de código sob demanda, em resposta a eventos, sem precisar gerenciar servidores ou infraestrutura. Ele é ideal para automatizar tarefas, criar APIs rápidas e processar dados em tempo real com baixo custo. 


Máquinas Virtuais (VMs)São ambientes completos que simulam um computador físico.
Cada VM tem seu próprio sistema operacional, kernel e recursos dedicados (CPU, memória, disco).
Mais pesadas, consomem mais recursos e demoram mais para iniciar.
Indicadas para aplicações que precisam de isolamento total ou sistemas legados.
ContêineresSão pacotes leves que compartilham o mesmo sistema operacional do host.
Contêm apenas o aplicativo e suas dependências.
Mais rápidos de iniciar, consomem menos recursos e são altamente portáveis.
Ideais para microsserviços, aplicações modernas e ambientes de CI/CD.

👉 Em resumo: VMs oferecem isolamento completo, mas são mais pesadas; contêineres são leves, rápidos e ideais para aplicações modernas.


Os Serviços de Aplicativos do Azure (Azure App Service) são uma plataforma PaaS (Platform as a Service) que permite hospedar e gerenciar aplicativos web, APIs e backends móveis sem se preocupar com infraestrutura.
🔹 Explicação rápida

Hospedagem gerenciada: você publica seu código e o Azure cuida de servidores, escalabilidade e segurança.
Suporte a várias linguagens: .NET, Java, Python, Node.js, PHP, entre outras.
Escalabilidade automática: aumenta ou reduz recursos conforme a demanda.
Integração nativa: conecta-se facilmente ao Azure DevOps, GitHub, bancos de dados e serviços de identidade.
Segurança: autenticação integrada com Azure Active Directory e certificados SSL.

🔹 Casos de uso

Hospedar sites e portais corporativos.
Criar APIs REST para aplicações móveis ou web.
Rodar backends de aplicativos móveis com integração a notificações push.
Automatizar pipelines de CI/CD para implantar novas versões rapidamente.

👉 Em resumo: o Azure App Service é a forma mais simples e rápida de colocar um aplicativo web ou API em produção na nuvem, com escalabilidade e segurança já embutidas.

Serviços de Rede do Azure são recursos que permitem conectar, proteger e otimizar a comunicação entre aplicações, usuários e dados dentro da nuvem. Eles garantem que tudo funcione de forma segura, rápida e escalável.
🔹 Explicação rápida

Rede Virtual (VNet): cria redes privadas na nuvem para conectar recursos com segurança.
VPN Gateway: conecta sua rede local ao Azure por meio de uma VPN segura.
ExpressRoute: conexão dedicada de alta velocidade entre sua infraestrutura local e o Azure.
Azure Firewall / Network Security Groups (NSG): protegem contra acessos não autorizados e controlam tráfego.
Load Balancer / Application Gateway: distribuem tráfego entre servidores para garantir desempenho e alta disponibilidade.
Azure DNS: gerencia nomes de domínio com alta confiabilidade.
Content Delivery Network (CDN): acelera entrega de conteúdo para usuários em diferentes regiões.
🔹 Em resumo
Os serviços de rede do Azure são a base para conectar e proteger seus recursos na nuvem, oferecendo desde redes privadas até balanceamento de carga e segurança avançada.
PROJETO ENTREGUE
Armazenamento
Conta de armazenamento - nome globalmente exclusivo , voce pode escolher uma parte do nome inicial e dar um auto completar que a Microsoft determina o restante.
Redundância de armazenamento
LRS - redundancia local, trabalha na primeira região, datacenter individual. Durabilidade 11 noves. Cópia assíncrono, um delay na copia.
11 noves” é uma forma abreviada de dizer 99,999999999% de durabilidade.
Exemplo cria um arquivo - ele replica 3 copias em 1 datacenter. 
ZRS - redundancia de zona, ou seja é distribuído em 3 zonas na região primaria, com 12 noves.
GRS - redundancia geográfica, funciona como o LRS + uma copia na região secundária. 16 noves.
GZRS - funciona como o ZRS + uma copia na região secundária. 16 noves.
--
O Azure garante alta disponibilidade e durabilidade dos dados através de diferentes opções de replicação:

LRS (Locally Redundant Storage)Mantém 3 cópias dos dados em um único datacenter.
Mais barato, mas menos resiliente a falhas regionais.
ZRS (Zone Redundant Storage)Replica os dados em 3 zonas de disponibilidade dentro da mesma região.
Protege contra falhas de datacenter, mantendo baixa latência.
GRS (Geo-Redundant Storage)Replica os dados em uma região secundária distante (com LRS lá também).
Alta resiliência contra desastres regionais.


Serviços de armazenamento
4 estilos de dados
Blob: otimizado para o armazenamento de quantidade massiva de dados não estruturados, como texto ou dados binários, como sites.
Disco do Azure: fornece discos para máquinas virtuais, aplicativos e outros serviços. adicionar discos não reseta a maquina, so se mudar família.
Fila do Azure: serviço de armazenamento de mensagens que  fornece armazenamento e recuperação para grande quantidade de mensagem, cada uma com até 64KB.
Arquivos do Azure: configura um compartilhamento de rede altamente disponível que pode ser utilizado usando protocolo bloco de mensagens do servidor.
--
O Azure Storage oferece diferentes serviços, cada um adequado a um tipo de dado:

Blob StoragePara dados não estruturados (imagens, vídeos, documentos).
Suporta acesso via HTTP/HTTPS.
Modos de acesso: Hot, Cool e Archive (dependendo da frequência de uso).
File StorageCompartilhamento de arquivos via protocolo SMB.
Ideal para migração de servidores de arquivos locais para a nuvem.
Queue StorageArmazena mensagens para comunicação assíncrona entre componentes de aplicações distribuídas.
Table StorageBanco NoSQL para dados estruturados em pares chave-atributo.
Escalável e de baixo custo.
Disk StorageDiscos gerenciados para VMs (SSD ou HDD).
Usado como armazenamento persistente para máquinas virtuais.
Pontos de extremidade público do serviço de armazenamento

São URLs exclusivos que permitem acessar os serviços de armazenamento do Azure pela internet.
Cada conta de armazenamento recebe um nome único e, a partir dele, são criados os pontos de extremidade para cada tipo de serviço.
Exemplo de formato:Blob: https://<nomeconta>.blob.core.windows.net
File: https://<nomeconta>.file.core.windows.net
Queue: https://<nomeconta>.queue.core.windows.net
Table: https://<nomeconta>.table.core.windows.net

🔑 Características principais

Acesso via HTTPS: garante segurança na comunicação.
Escopo global: qualquer cliente com internet pode acessar, desde que tenha credenciais válidas.
Autenticação e autorização: feita por meio de chaves de acesso, SAS (Shared Access Signatures) ou Azure AD.
Isolamento por serviço: cada tipo de dado (Blob, File, Queue, Table) tem seu próprio endpoint.

📌 Por que isso é importante no AZ-900?

Demonstra como o Azure organiza o acesso aos diferentes serviços de armazenamento.
Mostra que, mesmo sendo um serviço único (Azure Storage), ele é dividido em subserviços com endpoints próprios.
É essencial entender que o nome da conta de armazenamento define a URL pública usada para acessar os dados.

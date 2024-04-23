# Ponderada-MVC - Lucas Magalhães Castro Rodrigues

## Nome do projeto 
DELL Training Platform

## Descrição
A plataforma de treinamento da DELL é uma aplicação web destinada a facilitar o acesso dos funcionários aos manuais de montagem de produtos da empresa, permitindo uma aprendizagem eficaz e atualizações contínuas nos processos de montagem através de materiais ricos como documentos, vídeos, imagens e modelos 3D.

## Arquitetura
MVC (Model-View-Controller)

## Ferramenta de Diagramação
draw.io

## Modelos (Models)
### Entidades e seus atributos
- **User**: `{ id, name, email, role }`
- **Manual**: `{ id, title, description, product_type, version, date_updated, content_files[] }`
- **ContentFile**: `{ id, manual_id, file_type, url }`
- **UserActivity**: `{ user_id, manual_id, status, date }`

### Relações entre as entidades
- **User** e **UserActivity** têm uma relação um-para-muitos, indicando que um usuário pode ter várias atividades registradas.
- **Manual** e **ContentFile** também têm uma relação um-para-muitos, refletindo que um manual pode incluir vários arquivos de conteúdo.

## Controladores (Controllers)
### Controladores e suas responsabilidades
- **UserController**: Gerencia autenticação e perfil de usuários.
- **ManualController**: Administra as operações de criação, atualização e exclusão dos manuais.
- **ViewController**: Controla a exibição de conteúdo e listagens de manuais.
- **NotificationController**: Gerencia o envio de notificações para os usuários.

### Ações de cada controlador
- **UserController**: Métodos incluem `login()`, `logout()`, `register(user)`, `updateProfile(user)`.
- **ManualController**: Métodos incluem `addManual(manual)`, `updateManual(manual)`, `deleteManual(manualId)`.
- **ViewController**: Métodos incluem `showManual(manualId)`, `listManuals()`, `searchManuals(query)`.
- **NotificationController**: Métodos incluem `sendNotification(userId, message)`.

### Interação dos controladores com modelos e views
Controladores solicitam dados dos modelos e enviam esses dados para as views para renderização. Por exemplo, `ViewController` usa `listManuals()` para obter dados de `Manual` e passa esses dados para a `ManualListView` para exibição.

## Views (Views)
### Views e suas funções
- **HomePage**: Mostra a barra de busca e manuais recentemente acessados.
- **ManualDetailsPage**: Exibe detalhes completos de um manual.
- **ProfilePage**: Mostra o perfil do usuário e histórico de atividades.
- **AdminDashboard**: Fornece uma visão geral das estatísticas e gerenciamento de manuais.

## Infraestrutura
### Componentes de infraestrutura
- **Banco de Dados**: Armazena todas as informações de usuários e manuais.
- **Servidores e Containers**: Utilização de tecnologia de containers para distribuição e escalabilidade do sistema.
- **APIs Externas**: Integração com sistemas de Single Sign-On (SSO) e serviços de armazenamento de arquivos.

### Integração da infraestrutura à arquitetura MVC
A infraestrutura suporta a arquitetura MVC, onde o banco de dados é acessado pelos modelos, os servidores hospedam a aplicação e as APIs externas fornecem serviços complementares como autenticação e armazenamento de mídia.

## Implicações da Arquitetura
### Escalabilidade, Manutenção, Testabilidade, Performance
- **Escalabilidade**: A arquitetura permite escalar cada componente de forma independente, facilitando o gerenciamento de carga e crescimento do usuário.
- **Manutenção**: A separação clara entre modelos, vistas e controladores facilita a manutenção e atualização do sistema.
- **Testabilidade**: Cada componente do MVC pode ser testado isoladamente, o que melhora a qualidade do código e reduz os bugs.
- **Performance**: O uso de containers e sistemas de cache pode melhorar significativamente a performance da aplicação.

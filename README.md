CloudConnect: Cadastro de Clientes com Airtable
Este é um projeto de aplicação web simples para gerenciar uma lista de clientes. Ele permite criar, ler, atualizar e excluir (CRUD) registros, que são persistidos em nuvem utilizando a API da plataforma Airtable.

🚀 Funcionalidades
Listagem de Clientes: Visualiza todos os clientes cadastrados em cards.

Criação de Clientes: Adiciona um novo cliente através de um formulário.

Edição de Clientes: Atualiza as informações de um cliente existente em uma janela modal.

Exclusão de Clientes: Remove um cliente da base de dados.

Busca em Tempo Real: Filtra a lista de clientes conforme o usuário digita no campo de busca.

Interface Reativa: Exibe estados de carregamento, erro e lista vazia para uma melhor experiência do usuário.

🛠️ Tecnologias Utilizadas
Frontend: HTML5, CSS3 com Tailwind CSS, JavaScript (ES6+)

Nuvem/Backend: Airtable como banco de dados (BaaS - Backend as a Service)

⚙️ Como Rodar o Projeto
Clone ou baixe o arquivo:

Faça o download do arquivo index.html para o seu computador.

Configure as variáveis:

Abra o arquivo index.html em um editor de código (como VS Code).

Localize a seção <script> no final do arquivo.

Altere as três constantes a seguir com as suas credenciais do Airtable:

// --- CONFIGURAÇÃO DO AIRTABLE ---
const AIRTABLE_PAT = 'SEU_TOKEN_DE_ACESSO_PESSOAL_AQUI'; 
const BASE_ID = 'SEU_BASE_ID_AQUI';
const NOME_TABELA = 'SEU_NOME_DA_TABELA_AQUI';

Abra no navegador:

Salve o arquivo index.html após inserir suas credenciais.

Abra o arquivo diretamente em qualquer navegador de internet moderno (Google Chrome, Firefox, etc.).

🔑 Variáveis Necessárias
Para que a aplicação se conecte à sua base do Airtable, você precisa fornecer as seguintes informações:

AIRTABLE_PAT: Seu Token de Acesso Pessoal (PAT - Personal Access Token) gerado no Airtable. Ele funciona como sua senha de acesso à API.

BASE_ID: O identificador da sua Base no Airtable (geralmente começa com app...).

NOME_TABELA: O nome exato da sua Tabela onde os clientes estão armazenados (ex: Clientes).

Você encontra essas informações na documentação da sua API do Airtable.

📊 Diagrama de Sequência de Conexão
O diagrama abaixo ilustra como o frontend (navegador) se comunica com a API do Airtable para buscar e exibir a lista de clientes.

sequenceDiagram
    participant Navegador (Frontend)
    participant API do Airtable (Backend)

    Navegador->>Navegador: Carrega index.html e executa o script
    Navegador->>Navegador: Chama a função buscarClientes()
    Note right of Navegador: Prepara a requisição GET com o Token de Acesso
    Navegador->>API do Airtable: GET /v0/BASE_ID/NOME_TABELA
    API do Airtable-->>API do Airtable: Valida o Token de Acesso
    alt Requisição bem-sucedida
        API do Airtable-->>Navegador: Responde com 200 OK (JSON com os dados)
        Navegador->>Navegador: Processa o JSON e renderiza os clientes na tela
    else Token inválido ou outro erro
        API do Airtable-->>Navegador: Responde com Erro (ex: 401 Unauthorized)
        Navegador->>Navegador: Exibe uma mensagem de erro na interface
    end

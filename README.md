<div align="center">
   <img src="./assets/microsoft.svg">
   <h1>Microsoft Learn : Criar uma API Web com o ASP.NET Core</h1>
</div>

40 min restante | Módulo | 9 Unidades

Iniciante | Desenvolvedor | Estudante | .NET | ASP.NET Core

<h3> Descrição </h3>
<p> Crie um serviço RESTful com o ASP.NET Core que dá suporte a operações de CRUD (criação, leitura, atualização e exclusão).</p>

<h3> Objetivos de aprendizagem </h3>

>Neste módulo, você vai:

* Criar um projeto de API Web com o ASP.NET Core.
* Criar um banco de dados em memória para manter produtos.
* Adicionar suporte para operações CRUD.
* Testar métodos de ação de API Web no shell de comando.

<h3> Pré-requisitos </h3>

* Capacidade de escrever em C# no nível iniciante
* Instalações locais do SDK do .NET e do Visual Studio Code
* Extensão do C# para Visual Studio Code
* Experiência com o uso da linha de comando

<h3>Este módulo faz parte destes roteiros de aprendizagem</h3>

> Criar aplicativos .NET com C#

| Módulo                                          | Tempo  | Status |
|-------------------------------------------------|--------|--------|
| Introdução                                      | 1 min  | ✔️     |
| REST no ASP.NET Core                            | 3 min  | 🚧     |
| Exercício – Criar um projeto de API Web         | 8 min  | 🚧     |
| Controladores da API Web do ASP.NET Core        | 4 min  | 🚧     |
| Exercício – Adicionar um armazenamento de dados | 4 min  | 🚧     |
| Exercício – Adicionar um controlador            | 5 min  | 🚧     |
| Ações CRUD no ASP.NET Core                      | 5 min  | 🚧     |
| Exercício – implementar operações CRUD          | 10 min | 🚧     |
| Resumo                                          | 1 min  | 🚧     |

<h2>Introdução</h2>

Este módulo explora a criação de um serviço RESTful multiplataforma usando a API Web do ASP.NET Core com .NET Core e C#.

Este módulo usa a CLI (interface de linha de comando) do .NET e o Visual Studio Code para desenvolvimento local. Depois de concluir este módulo, você poderá aplicar os conceitos dele usando um ambiente de desenvolvimento como o Visual Studio (Windows) e o Visual Studio para Mac (macOS), ou de desenvolvimento contínuo, como o Visual Studio Code (Windows, Linux e macOS).

Cenário de Exemplo
Digamos que você trabalhe para uma empresa chamada Contoso Pizza. Seu gerente pediu que você desenvolvesse um serviço RESTful de gerenciamento de estoque de pizza como pré-requisito para a vitrine Web e o aplicativo móvel da empresa. O serviço deve dar suporte à adição, exibição, modificação e remoção de tipos de pizza— um uso padronizado de verbos de ação HTTP mais conhecido como CRUD (C riar, L er, A tualizar, E xcluir).

O que faremos?
Neste módulo, você vai criar um aplicativo da API Web usando ASP.NET Core e executá-lo e testá-lo na linha de comando. Em seguida, você vai adicionar um armazenamento de dados e um novo controlador de API. Por fim, você vai implementar e testar os métodos de API para criar, ler, atualizar e excluir pizzas do armazenamento de dados.

Qual é a meta principal?
Ao final desta sessão, você poderá criar aplicativos da API Web com ASP.NET Core e criar controladores de API que implementem a lógica CRUD básica.

<h2>REST no ASP.NET Core</h2>

Quando você navega para uma página da Web, o servidor Web se comunica com seus navegadores usando HTML, CSS e JavaScript. Se você interagir com a página fazendo algo como enviar um formulário de logon ou clicar em um botão de compra, o navegador enviará as informações de volta para o servidor Web.

De maneira semelhante, os servidores Web podem se comunicar com uma ampla gama de clientes, incluindo navegadores, dispositivos móveis, outros servidores Web e muito mais, usando serviços Web. Clientes de API se comunicam com o servidor por HTTP, e os dois trocam informações usando um formato de dados como JSON ou XML. Muitas vezes, as APIs são usadas em SPAs (aplicativos de página única) que executam a maior parte da lógica da interface do usuário em um navegador da Web, comunicando-se com o servidor Web usando principalmente APIs Web.

<h3>REST: um padrão comum para criar APIs com HTTP</h3>

REST (Transferência de Estado Representacional) é um estilo de arquitetura para a criação de serviços Web. As solicitações REST são feitas por HTTP usando os mesmos verbos HTTP que os navegadores da Web usam para recuperar páginas da Web e enviar dados para os servidores. Os verbos são:

* GET – essa operação é usada para recuperar dados do serviço Web.
* POST – essa operação é usada para criar um item de dados no serviço Web.
* PUT – essa operação é usada para atualizar um item de dados no serviço Web.
* PATCH – essa operação é usada para atualizar um item de dados no serviço Web, descrevendo um conjunto de instruções sobre como o item deve ser modificado. Esse verbo não é usado no aplicativo de exemplo.
*DELETE – essa operação é usada para excluir um item de dados no serviço Web.

APIs de serviço Web que aderem ao REST são chamadas de APIs RESTful e são definidas usando:

* Um URI de base.
* Métodos HTTP, como GET, POST, PUT, PATCH ou DELETE.
* Um tipo de mídia para os dados, como JSON (JavaScript Object Notation) ou XML.

Geralmente, uma API precisará fornecer serviços para algumas coisas diferentes e relacionadas. Por exemplo, nossa API de pizza pode gerenciar pizzas, clientes e pedidos. Usamos o roteamento para mapear URIs para divisões lógicas em nosso código, de modo que solicitações para http://localhost:5000/Pizza são roteadas para um PizzaController, enquanto solicitações para http://localhost:5000/order são roteadas para um OrderController.

<h3>Benefícios de criar APIs no ASP.NET Core</h3>

Com o ASP.NET, você pode usar a mesma estrutura e padrões para criar páginas da Web e serviços. Isso significa que você pode reutilizar classes de modelo, a lógica de validação e até mesmo atender páginas da Web e serviços lado a lado no mesmo projeto. Essa abordagem traz vários benefícios.

<h3>Benefício: serialização simples</h3>

O ASP.NET foi projetado para experiências modernas na Web. Os pontos de extremidade serializam automaticamente suas classes para JSON formatado corretamente de maneira pré-configurada. Nenhuma configuração especial é necessária. É claro que a serialização pode ser personalizada para pontos de extremidade que têm requisitos exclusivos.

<h3>Benefício: autenticação e autorização</h3>

Proteja os pontos de extremidade da API com suporte interno para JWT (Token Web JSON) padrão do setor. A autorização baseada em políticas oferece a flexibilidade de definir regras de controle de acesso poderosas, tudo no código.

<h3>Benefício: roteamento com o código</h3>

O ASP.NET permite que você defina rotas e verbos embutidos no código usando atributos. Os dados do caminho da solicitação, da cadeia de consulta e do corpo da solicitação são associados automaticamente aos parâmetros do método.

<h3>Benefício: HTTPS por padrão</h3>

O HTTPS é uma parte importante das APIs Web modernas e profissionais. Ele se baseia na criptografia de ponta a ponta para fornecer privacidade e garantir que as chamadas à API não sejam interceptadas e alteradas entre o cliente e o servidor. O ASP.NET tem suporte de primeira classe para HTTPS pronto para uso. Ele gera automaticamente um certificado de teste e o importa facilmente para habilitar o HTTPS local, para que você execute e depure aplicativos com segurança antes de publicá-los.

<h3>Benefício: compartilhar código e conhecimento com aplicativos .NET</h3>

Aproveite suas habilidades e o ecossistema do .NET para compartilhar lógica de sua API Web com outros aplicativos criados com .NET, incluindo dispositivos móveis, Web, desktop, serviços e muito mais.

<h3>Testando APIs Web usando o REPL HTTP do .NET</h3>

Ao desenvolver um site tradicional, você geralmente exibe e testa seu trabalho em um navegador da Web. As APIs da Web aceitam e retornam dados em vez de HTML, de modo que um navegador da Web não é a melhor ferramenta para testes de APIs Web. Uma das opções mais fáceis de usar para explorar e interagir com APIs Web é o REPL HTTP do .NET. REPL significa R ead-E val-P rint L oop. Trata-se de um modo simples e popular de criar ambientes de linha de comando interativos. Na próxima seção, você criará uma API Web simples e interagirá com ela usando o REPL HTTP do .NET.

<h3>Verificar seu conhecimento</h3>
1. Qual das alternativas a seguir não é um motivo para criar uma API Web usando ASP.NET Core?

- [ ] - Fornecer um servidor de back-end para um front-end de SPA (aplicativo de página única), como Angular ou React.
- [ ] - Fornecer dados a um aplicativo cliente móvel usando XML ou JSON.
- [x] - Atender um aplicativo Web tradicional baseado em HTML.


<h2></h2>
<h2></h2>
<h2></h2>
<h2></h2>
<h2></h2>
<h2></h2>
<h2></h2>

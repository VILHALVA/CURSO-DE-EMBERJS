# ROUTING SYSTEM
**Sistema de Roteamento (Routing System):**
O sistema de roteamento no Ember.js é um componente fundamental que controla a estrutura da URL da sua aplicação e determina qual conteúdo deve ser exibido na tela. Aqui está uma explicação em português sobre o sistema de roteamento no Ember.js:

1. **Rota (Route)**: Uma rota é uma representação da URL da sua aplicação e é responsável por carregar dados do servidor (se necessário) e preparar o modelo (model) que será usado para renderizar o template. No Ember.js, as rotas são definidas no arquivo `app/routes/nome-da-rota.js`.

2. **Modelo (Model)**: O modelo é a representação dos dados que serão usados para renderizar a interface do usuário. Ele é obtido pela rota e geralmente consiste em informações carregadas do servidor. Os modelos são usados nos templates para exibir dados.

3. **Template**: O template é uma representação da interface do usuário e define como os dados do modelo são renderizados. Os templates são escritos em Handlebars, uma linguagem de modelo, e permitem a inclusão de variáveis e lógica de exibição.

4. **Roteador (Router)**: O roteador controla a estrutura da URL da aplicação e determina qual rota deve ser carregada com base na URL atual. Ele é definido no arquivo `app/router.js` e mapeia URLs para rotas.

5. **URLs Dinâmicas**: O Ember.js permite a criação de URLs dinâmicas, onde partes da URL representam parâmetros que podem ser usados para buscar informações específicas. Isso é útil para aplicativos que precisam exibir diferentes conjuntos de dados com base em seleções do usuário.

6. **Navegação de Página**: O sistema de roteamento no Ember.js facilita a navegação entre páginas no aplicativo. Você pode usar links e transições para alterar a URL e carregar novas rotas e modelos.

7. **Carregamento Assíncrono de Dados**: O sistema de roteamento suporta o carregamento assíncrono de dados do servidor, o que é útil para aplicativos que dependem de recursos externos, como APIs.

O sistema de roteamento no Ember.js é poderoso e flexível, permitindo a criação de aplicativos com várias páginas e uma estrutura de URL clara. Com ele, é possível criar interfaces de usuário dinâmicas e interativas que respondem às ações do usuário.

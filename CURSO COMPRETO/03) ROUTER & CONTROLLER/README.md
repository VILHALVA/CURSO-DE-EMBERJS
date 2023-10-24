# ROUTER & CONTROLLER
## CONCEITO:
**Roteador (Router) e Controlador (Controller):**
No Ember.js, o roteador (router) e o controlador (controller) desempenham papéis importantes na estrutura de um aplicativo web. Aqui está uma explicação em português sobre esses dois conceitos:

**Roteador (Router):**

1. **Definição de Rotas**: O roteador é responsável por definir as rotas da sua aplicação e mapear as URLs para essas rotas. Isso envolve a criação de um mapa de URLs, indicando qual rota deve ser ativada quando uma URL específica é acessada.

2. **Transições entre Rotas**: O roteador controla a transição entre diferentes estados do aplicativo, o que inclui carregar novas rotas, carregar modelos e atualizar a interface do usuário. Você pode usar métodos como `transitionTo` e `transitionToRoute` para navegar entre as rotas programaticamente.

3. **Roteamento Aninhado**: O Ember.js suporta roteamento aninhado, o que significa que você pode ter rotas dentro de outras rotas. Isso é útil para criar hierarquias de URL complexas.

**Controlador (Controller):**

1. **Representação de Estado**: O controlador representa o estado atual da interface do usuário e fornece uma camada para gerenciar o comportamento e as ações relacionadas a essa interface. Cada rota geralmente está associada a um controlador.

2. **Lógica da Interface do Usuário**: Os controladores contêm lógica relacionada à exibição e à interação do usuário. Você pode definir propriedades e métodos no controlador para controlar como os modelos são exibidos e manipulados.

3. **Gerenciamento de Ações**: Os controladores também são responsáveis por responder a ações do usuário. Você pode definir métodos que são acionados quando os eventos, como cliques em botões, ocorrem na interface do usuário.

4. **Observação de Modelos**: Os controladores observam as mudanças nos modelos e atualizam automaticamente a interface do usuário quando os modelos são modificados.

No Ember.js, o modelo (model) de dados, que representa os dados do aplicativo, geralmente é gerenciado pelas rotas. O controlador gerencia a interação e a representação desse modelo na interface do usuário.

É importante notar que, a partir do Ember.js 2.x, os controladores de rota foram desencorajados em favor dos controladores de objeto único (single-object controllers) e controladores de array (array controllers), já que as rotas podem gerenciar diretamente o modelo. No entanto, os controladores de objeto único e array ainda podem ser usados se necessário.

## EXEMPLOS:
Aqui estão exemplos de código que demonstram como o roteador e o controlador funcionam no Ember.js. Vou fornecer exemplos simples para ilustrar os conceitos.

**Exemplo de Roteador (Router):**

Para definir rotas no Ember.js, você pode usar o roteador. Suponhamos que você deseja criar uma rota chamada "dashboard" que corresponde à URL "/dashboard". Aqui está como você definiria isso:

```javascript
// app/router.js
import EmberRouter from '@ember/routing/router';
import config from './config/environment';

const Router = EmberRouter.extend({
  location: config.locationType,
  rootURL: config.rootURL
});

Router.map(function() {
  this.route('dashboard'); // Define a rota "dashboard"
});

export default Router;
```

Aqui, o método `this.route('dashboard')` define a rota "dashboard" no seu aplicativo. Quando você acessar "/dashboard" no navegador, o Ember.js carregará a rota correspondente.

**Exemplo de Controlador (Controller):**

Vamos criar um controlador simples para a rota "dashboard" que define uma propriedade "message" que será exibida no template:

```javascript
// app/controllers/dashboard.js
import Controller from '@ember/controller';

export default Controller.extend({
  message: "Bem-vindo ao painel de controle!" // Define uma propriedade no controlador
});
```

No código acima, um controlador chamado "dashboard" é criado e possui uma propriedade chamada "message". Você pode definir propriedades e métodos adicionais neste controlador para gerenciar a lógica da interface do usuário.

Agora, vamos criar o template correspondente que exibirá a mensagem:

```handlebars
{{! app/templates/dashboard.hbs }}
<h1>Painel de Controle</h1>
<p>{{message}}</p>
```

O template `dashboard.hbs` usa `{{message}}` para exibir a propriedade "message" definida no controlador. Quando você acessa a rota "/dashboard", verá a mensagem na interface do usuário.

Estes são exemplos simples, e no desenvolvimento real, você terá rotas mais complexas e controladores com lógica mais elaborada. O Ember.js fornece muitas ferramentas e convenções para facilitar a criação de aplicativos web robustos.



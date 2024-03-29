# SINTAXE
## CRIANDO UM PROJETO:
Criar um projeto no Ember.js é um processo simples, assim como no Angular. Aqui está um guia passo a passo para ajudá-lo a começar:

### Passo 1: Instalar o Ember CLI (Command Line Interface)
Certifique-se de ter o Ember CLI instalado globalmente em sua máquina. Você pode instalar usando o npm (Node Package Manager) através do seguinte comando:

```
npm install -g ember-cli
```

### Passo 2: Criar um novo projeto Ember
Depois de instalar o Ember CLI, você pode criar um novo projeto Ember executando o seguinte comando no terminal:

```
ember new nome-do-projeto
```

Substitua "nome-do-projeto" pelo nome que você deseja dar ao seu projeto.

### Passo 3: Navegar para o diretório do projeto
Após a criação do projeto, navegue até o diretório do projeto usando o comando `cd`:

```
cd nome-do-projeto
```

### Passo 4: Executar o projeto
Depois de estar no diretório do seu projeto, você pode iniciar o servidor de desenvolvimento executando:

```
ember serve
```

Isso iniciará um servidor de desenvolvimento e seu aplicativo estará acessível em `http://localhost:4200/` por padrão.

### Passo 5: Visualizar o projeto
Abra seu navegador da web e vá para `http://localhost:4200/` para visualizar seu novo aplicativo Ember.

### Passo 6: Começar a desenvolver
Agora você pode começar a desenvolver seu projeto Ember. O Ember CLI já gerou a estrutura básica do projeto para você. Você pode adicionar componentes, rotas, modelos e muito mais conforme necessário para o seu aplicativo.

## EXEMPLOS DE CÓDIGOS:
Abaixo está um exemplo básico de um aplicativo Ember.js que exibe uma lista de tarefas (to-do list) e permite adicionar novas tarefas:

1. **HTML (index.html)**:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Ember.js Todo App</title>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css">
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/skeleton/2.0.4/skeleton.min.css">
</head>
<body>

<div class="container">
    <h1>My Todo List</h1>
    <ul id="todo-list"></ul>
    <input type="text" id="new-todo" placeholder="Add new todo">
    <button onclick="addTodo()">Add</button>
</div>

<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/3.6.0/jquery.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/handlebars.js/4.7.7/handlebars.min.js"></script>
<script src="https://cdnjs.cloudflare.com/ajax/libs/ember.js/3.28.2/ember.prod.js"></script>
<script src="app.js"></script>
</body>
</html>
```

2. **JavaScript (app.js)**:
```javascript
// Definindo o modelo de dados (Data Model)
const Todo = Ember.Object.extend({
    title: null,
    completed: false
});

// Criando instâncias do modelo
const todo1 = Todo.create({ title: 'Learn Ember.js' });
const todo2 = Todo.create({ title: 'Build an Ember app' });

// Definindo o controlador (Controller)
const TodosController = Ember.Controller.extend({
    todos: [todo1, todo2],

    actions: {
        addTodo() {
            const newTitle = $('#new-todo').val();
            const newTodo = Todo.create({ title: newTitle });
            this.todos.pushObject(newTodo);
            $('#new-todo').val(''); // Limpar o campo de entrada
        }
    }
});

// Instanciando o controlador
const todosController = TodosController.create();

// Definindo a visualização (View)
const TodosView = Ember.View.extend({
    template: Handlebars.compile(`
        {{#each controller.todos as |todo|}}
            <li>{{todo.title}}</li>
        {{/each}}
    `)
});

// Renderizando a visualização
TodosView.create({ controller: todosController }).appendTo('#todo-list');
```

3. **Explicação**:
   - Este exemplo cria um aplicativo Ember.js simples para gerenciar uma lista de tarefas.
   - No arquivo HTML, definimos a estrutura da página, incluindo uma lista de tarefas, um campo de entrada para adicionar novas tarefas e um botão "Add".
   - No JavaScript, definimos um modelo de dados `Todo` usando `Ember.Object.extend()`, que possui propriedades `title` e `completed`.
   - Criamos algumas instâncias de `Todo` para representar tarefas existentes.
   - Definimos um controlador `TodosController` para gerenciar a lista de tarefas e a lógica de adicionar novas tarefas.
   - Instanciamos o controlador e definimos uma visualização `TodosView` para renderizar a lista de tarefas usando Handlebars.js.
   - Por fim, renderizamos a visualização na página, exibindo todas as tarefas existentes e permitindo adicionar novas tarefas.


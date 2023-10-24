# FORM INPUT & @TRACKED CLASS
Ao criar um componente em Ember.js para uma lista de itens com funcionalidades como enriquecer a visualização de itens, adicionar itens com uma classe ou objeto `@tracked`, atualizar indicadores de itens no carrinho, adicionar controles de entrada de formulário para atualizar a contagem de itens e o total. Vou fornecer um exemplo de como você pode implementar essa funcionalidade em um componente Ember.js.

**Componente de Lista de Itens:**

Primeiro, vamos criar um componente de lista de itens que exibe uma lista de itens e suas informações, como nome, preço e quantidade. Este é um exemplo simplificado:

```javascript
// app/components/item-list.js
import Component from '@glimmer/component';

export default class ItemListComponent extends Component {
  // Aqui você pode usar um array de objetos para representar os itens
  items = [
    { name: 'Item 1', price: 10, quantity: 0 },
    { name: 'Item 2', price: 15, quantity: 0 },
    // ... adicione mais itens
  ];

  // Método para enriquecer a visualização de um item
  enrichItem(item) {
    // Implemente a lógica para enriquecer a visualização do item, se necessário
    return `Nome: ${item.name}, Preço: $${item.price.toFixed(2)}, Quantidade: ${item.quantity}`;
  }
}
```

Agora, no seu template `item-list.hbs`, você pode usar um loop `{{#each}}` para iterar pelos itens e exibir as informações enriquecidas:

```handlebars
{{! app/templates/components/item-list.hbs}}
<ul>
  {{#each this.items as |item|}}
    <li>{{enrichItem item}}</li>
  {{/each}}
</ul>
```

**Componente de Controle de Formulário:**

Agora, crie um componente de controle de formulário para adicionar, atualizar a contagem de itens e calcular o total:

```javascript
// app/components/item-form.js
import Component from '@glimmer/component';
import { action } from '@ember/object';

export default class ItemFormComponent extends Component {
  @tracked newItemName = '';
  @tracked newItemPrice = 0;
  @tracked newItemQuantity = 0;

  @action
  addItem() {
    // Implemente a lógica para adicionar um novo item à lista de itens
    this.args.onAddItem({
      name: this.newItemName,
      price: parseFloat(this.newItemPrice),
      quantity: parseInt(this.newItemQuantity),
    });

    // Limpe os campos após a adição
    this.newItemName = '';
    this.newItemPrice = 0;
    this.newItemQuantity = 0;
  }
}
```

**Componente Principal:**

Agora, você pode criar um componente principal que usa os componentes `item-list` e `item-form` para exibir a lista de itens e o formulário de adição:

```javascript
// app/templates/application.hbs
<div>
  <ItemList />
  <ItemForm @onAddItem={{action 'addItem'}} />
</div>
```

Este é um exemplo básico de como você pode criar uma lista de itens com controles de formulário para adicionar, atualizar a contagem de itens e calcular o total em um aplicativo Ember.js. Você pode estender essa funcionalidade para atender às necessidades específicas do seu aplicativo. Certifique-se de adicionar a lógica necessária para adicionar, remover ou atualizar itens na lista de itens e calcular o total com base na quantidade e no preço.
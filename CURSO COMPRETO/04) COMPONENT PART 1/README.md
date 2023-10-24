# COMPONENT PART 1
Vamos explorar o conceito de componentes no Ember.js, bem como alguns exemplos de uso. Os componentes são blocos de construção reutilizáveis que permitem encapsular lógica e aparência em aplicativos Ember.

**Conceito:**

Os componentes no Ember.js são pedaços isolados de interface do usuário que podem ser reutilizados em todo o aplicativo. Eles encapsulam HTML, CSS e JavaScript em um único pacote e podem aceitar parâmetros para personalização. Os componentes são úteis para criar partes reutilizáveis da interface do usuário, como botões, barras de navegação, formulários e muito mais.

**Exemplo de Alto Nível:**

Suponhamos que você deseje criar um componente de botão reutilizável. Aqui está um exemplo de código para criar um componente de botão no Ember.js:

```javascript
// app/components/my-button.js
import Component from '@ember/component';

export default Component.extend({
  tagName: 'button',
  classNames: ['my-button'],
  click() {
    // Lógica de clique do botão
  }
});
```

No código acima, definimos um componente chamado "my-button" que é representado por um botão HTML. Ele também possui uma classe CSS "my-button" e uma função "click()" para a lógica de clique.

**Componente com Conteúdo Filho:**

Os componentes podem incluir conteúdo filho. Por exemplo, você pode criar um componente de painel que aceita conteúdo inserido entre as tags de abertura e fechamento do componente. Aqui está um exemplo:

```handlebars
{{! app/templates/components/panel.hbs }}
<div class="panel">
  {{yield}}
</div>
```

Agora, você pode usar o componente "panel" em seu template e inserir conteúdo dentro dele:

```handlebars
{{!-- Seu template --}}
{{#panel}}
  <h2>Conteúdo do Painel</h2>
  <p>Este é um exemplo de painel com conteúdo filho.</p>
{{/panel}}
```

**Componentes no Ember Inspector:**

Você pode inspecionar componentes no Ember Inspector, uma extensão do navegador para depurar aplicativos Ember. Isso permite visualizar a hierarquia de componentes em execução e depurar o estado e as propriedades dos componentes.

**Componente de Tag de Auto-Fechamento:**

Você pode criar componentes com tags de auto-fechamento, como um ícone ou uma imagem. Por exemplo:

```handlebars
{{! app/templates/components/icon.hbs }}
<img src="{{iconUrl}}" alt="{{iconAlt}}" />
```

**Componente em um Subdiretório:**

Para organizar seus componentes em subdiretórios, você pode criar um diretório com o nome do componente e armazenar os arquivos relacionados a ele nesse diretório. Por exemplo, para um componente "meu-botao", você pode criar a seguinte estrutura:

```
app/components/meu-botao/
  |- meu-botao.js
  |- meu-botao.hbs
```

Essa organização facilita a gestão de muitos componentes em um aplicativo grande.

Os componentes são uma parte fundamental do Ember.js e são muito úteis para criar uma interface de usuário modular e reutilizável. Eles podem ser personalizados com propriedades e aceitar conteúdo filho, tornando-os flexíveis para atender às necessidades do aplicativo.


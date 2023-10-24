# HELPER PART 1
**Helpers - Parte 1: Helpers Incorporados e Implementação**

Os "helpers" são funções no Ember.js que você pode usar nos templates para realizar operações, criar lógica condicional e formatar dados. Vamos começar explorando alguns dos helpers incorporados no Ember.js e, em seguida, veremos como você pode criar seus próprios helpers personalizados.

**Helper Aninhado (Nested Helper):**

Em Ember.js, você pode usar helpers aninhados para combinar a saída de um helper com a entrada de outro. Por exemplo, você pode usar o helper `{{get}}` para acessar uma propriedade e, em seguida, concatenar seu valor usando `{{concat}}`. Aqui está um exemplo:

```handlebars
{{concat (get user 'firstName') ' ' (get user 'lastName')}}
```

Neste exemplo, usamos o helper `{{get}}` para acessar as propriedades `firstName` e `lastName` de um objeto `user` e, em seguida, o helper `{{concat}}` para concatenar os valores em um único nome completo.

**Helpers Incorporados:**

Aqui estão alguns exemplos de helpers incorporados no Ember.js:

- **`{{concat}}`**: Concatena várias strings.
- **`{{get}}`**: Obtém uma propriedade de um objeto.
- **`{{hash}}`**: Cria um objeto hash a partir de pares chave-valor.
- **`{{let}}`**: Declara variáveis locais.
- **`{{if}}`**: Executa conteúdo condicionalmente com base em uma expressão.
- **`{{unless}}`**: Inverso do `{{if}}`, executando conteúdo quando a expressão é falsa.
- **`{{each}}`**: Itera sobre uma lista e rende um bloco para cada item.

Aqui está um exemplo de uso do helper `{{if}}`:

```handlebars
{{#if isUserLoggedIn}}
  <p>Olá, {{user.name}}!</p>
{{else}}
  <p>Por favor, faça login.</p>
{{/if}}
```

Neste exemplo, o conteúdo entre `{{#if}}` e `{{else}}` é renderizado com base na condição `isUserLoggedIn`.

**Implementação de Helpers Personalizados:**

Você também pode criar seus próprios helpers personalizados no Ember.js. Para fazer isso, você deve definir um arquivo JavaScript que exporta uma função e registrá-lo como um helper. Aqui está um exemplo simplificado:

```javascript
// app/helpers/meu-helper.js
import { helper } from '@ember/component/helper';

function meuHelper([param1, param2]) {
  // Lógica personalizada com os parâmetros passados
  return `${param1} e ${param2}`;
}

export default helper(meuHelper);
```

Agora, você pode usar seu helper personalizado em um template:

```handlebars
{{meu-helper "Olá" "Mundo"}}
```

Este é um exemplo básico de um helper personalizado que aceita dois parâmetros e os concatena.

Lembrando que esta é apenas uma introdução aos helpers no Ember.js. Eles são uma parte importante do framework e permitem adicionar lógica e manipulação de dados aos seus templates de forma flexível.


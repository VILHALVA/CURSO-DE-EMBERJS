# HELPER PART 2
**Helpers - Parte 2: Helpers Personalizados e Características Avançadas**

Continuando com a exploração dos helpers no Ember.js, veremos como criar helpers personalizados e exploraremos algumas funcionalidades avançadas, como o uso dos helpers `if` e `unless`, um exemplo de helper personalizado, o helper `class`, e a função de zoom.

**Usando `if` e `unless` Helper:**

Os helpers `if` e `unless` são incorporados no Ember.js e permitem a execução condicional de conteúdo em seus templates. O `if` executa o conteúdo se a expressão for verdadeira, enquanto o `unless` executa o conteúdo se a expressão for falsa.

```handlebars
{{#if isUserLoggedIn}}
  <p>Olá, {{user.name}}!</p>
{{/if}}

{{#unless isUserLoggedIn}}
  <p>Por favor, faça login.</p>
{{/unless}}
```

**Helper Personalizado:**

Vamos criar um exemplo de um helper personalizado chamado `capitalize` que capitaliza a primeira letra de uma string.

```javascript
// app/helpers/capitalize.js
import { helper } from '@ember/component/helper';

function capitalize([str]) {
  return str.charAt(0).toUpperCase() + str.slice(1);
}

export default helper(capitalize);
```

Agora, você pode usar este helper personalizado em um template:

```handlebars
{{capitalize "hello"}}
```

Isso resultaria em "Hello".

**Helper `class`:**

O helper `class` é útil para adicionar classes condicionalmente com base em uma expressão. Aqui está um exemplo:

```handlebars
<button class={{class 'active' isActive}}>Clique Aqui</button>
```

Neste exemplo, a classe "active" é adicionada ao botão se a variável `isActive` for verdadeira.

**Função de Zoom:**

A função de zoom permite ampliar parte do texto em um template para facilitar a leitura. Você pode fazer isso com o helper `if` para alternar entre a versão ampliada e não ampliada do texto, por exemplo:

```handlebars
{{#if isZoomedIn}}
  <span style="font-size: 24px">{{textoAmpliado}}</span>
{{else}}
  {{textoPequeno}}
{{/if}}
```

No exemplo acima, o texto é ampliado quando `isZoomedIn` é verdadeiro e mostrado normalmente caso contrário.

Estas são algumas das funcionalidades avançadas e personalizadas que você pode utilizar com os helpers no Ember.js para melhorar a funcionalidade e a aparência do seu aplicativo.
# APPLICATION - ACCEPTANCE TEST
**Testes de Aplicação/Aceitação no Ember.js**

Vamos recapitular os testes de aplicação/aceitação no Ember.js, discutir os objetivos desses testes, examinar a estrutura de arquivos, resolver erros inesperados, pausar um teste e implementar um teste de aceitação.

**Recapitulação:**

Os testes de aplicação/aceitação no Ember.js são testes de ponta a ponta (end-to-end) que simulam a interação do usuário com o aplicativo. Eles verificam se as funcionalidades do aplicativo funcionam conforme o esperado, incluindo a navegação entre páginas, preenchimento de formulários e interações do usuário.

**Objetivo dos Testes de Aplicação/Aceitação:**

Os testes de aplicação/aceitação têm os seguintes objetivos:

1. Verificar se as principais funcionalidades do aplicativo estão funcionando corretamente.
2. Garantir que a navegação entre rotas e páginas esteja funcionando conforme o esperado.
3. Testar cenários comuns do usuário.

**Estrutura de Arquivos:**

Os testes de aplicação/aceitação estão normalmente organizados na seguinte estrutura de diretórios:

```
my-app/
  tests/
    acceptance/
```

Os testes de aceitação são mantidos no diretório "acceptance."

**Resolver Erros Inesperados:**

Às vezes, os testes de aceitação podem falhar devido a erros inesperados. Para identificar e resolver esses erros, você pode usar as ferramentas de depuração do navegador, como o console e o "Ember Inspector." Além disso, adicionar `debugger;` no código do teste permite pausar a execução e investigar o estado do aplicativo durante o teste.

**Pausar um Teste:**

Para pausar a execução de um teste de aceitação e depurá-lo, você pode adicionar a função `pauseTest()`:

```javascript
// Exemplo de como pausar um teste
test('pausar o teste para depuração', async function(assert) {
  await visit('/minha-rota');
  pauseTest();
});
```

Isso interromperá a execução do teste e permitirá que você inspecione o estado do aplicativo.

**Implementação de um Teste de Aceitação:**

Aqui está um exemplo de como você pode implementar um teste de aceitação simples:

```javascript
// my-app/tests/acceptance/meu-teste.js
import { module, test } from 'qunit';
import { visit, currentURL } from '@ember/test-helpers';
import { setupApplicationTest } from 'ember-qunit';

module('Acceptance | meu teste', function(hooks) {
  setupApplicationTest(hooks);

  test('visiting /minha-rota', async function(assert) {
    await visit('/minha-rota');

    assert.equal(currentURL(), '/minha-rota');
    assert.dom('.classe-do-elemento').exists();
  });
});
```

Neste exemplo, o teste verifica se a página em `/minha-rota` é visitada com sucesso, se a URL atual corresponde à rota correta e se um elemento com a classe "classe-do-elemento" existe na página.

Os testes de aceitação são valiosos para garantir que as funcionalidades do seu aplicativo funcionem corretamente e que a navegação e a interação do usuário ocorram conforme o esperado. Certifique-se de escrever testes de aceitação que abranjam os principais cenários de uso do aplicativo.
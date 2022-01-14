# NodeJS - Template de projeto

Esse repositório é um template extremamente completo para um projeto de NodeJS com JavaScript, incluindo as seguintes ferramentas:

- **Prettier**
  - Formatação de código com **Prettier**, garantindo padrão de código
  - Arquivo de configuração do **Prettier** bem completo
- **ESLint**
  - Formatação de código com **ESLint**, garantindo qualidade no código
  - Arquivo de configuração do **ESLint** bem completo
- **Visual Studio Code**
  - Suporte e configuração total ao VSCode
- **WebStorm**
  - Suporte e configuração total para o WebStorm ou IDEs da Jetbrains num geral
- **Husky, Lint-Staged e Pretty-Quick**
  - Garantindo que todas as validações são feitas antes de entrar no GitHub (funciona com GitLab, BitBucket, ou qualquer sistema Git que você usa)
- **Git Ignore**
  - Arquivo `.gitignore` bem completo, considerando **VSCode**, **Webstorm** (IDEs da JetBrains num geral), **NodeJS**, com uma modificação para que aceite os arquivos de configuração de IDEs específicas
- **Correção de final de linha dos arquivos**
  - Geralmente muitas equipes possuem problema com devs que usam Linux, Mac e Windows, pelos sistemas tratarem diferente os finais de linha de arquivo.
  - Isso está corrigido nesse template, forçando os finais de linha de arquivos sempre como `\n`, padrão utilizado pelos sistemas baseados em Unix (Linux e Mac), sem afetar nada a utilização/modificação dos arquivos por quem usa Windows

# Utilização do template

### 1ª opção

Você pode criar um repositório seu utilizando esse template de projeto clicando no link acima `Use this template`.

### 2ª opção

Também e possível acessar diretamente o link [https://github.com/FabricaDeSinapse/nodejs-template/generate](https://github.com/FabricaDeSinapse/nodejs-template/generate).

## Aplicando esse template em um projeto existente

Caso você queira aplicar as mesmas coisas que estão disponíveis nesse template, mas em um projeto seu que já existe, você pode seguir os passos nos capítulos a seguir.

## Criação do projeto

>  Caso já tenha o projeto criado, pule este passo.

1. Crie uma nova pasta com o nome do projeto;

2. Abra a pasta com o Visual Studio Code;

3. Abra o Terminal do VSCode;

4. Inicie o projeto Node, gerando o `package.json`, digitando no terminal:

   - ```bash
     npm init -y
     ```

5. Criação do `package-lock.json`:

   - ```bash
     npm i
     ```

6. Crie uma pasta na raiz do projeto chamada `src` e crie um arquivo dentro chamado`src/main.js`;

7. Coloque um código para testar:

   - ```js
     const numero = 2;
     console.info("numero: " + numero);
     ```

8. Crie o projeto no Git via GitHub Desktop ou da forma que achar melhor.


## Instalar e Configurar o Prettier

1. Instale o `prettier` no projeto:

   - ```bash
     npm i -D prettier
     ```

2. Instale a extensão do `prettier` no VSCode;

   - **ID da extensão:** `esbenp.prettier-vscode`

3. Crie uma pasta na raiz do projeto chama `.vscode` com um novo arquivo chamado `settings.json`

4. Coloque o seguinte conteúdo no arquivo `settings.json`:

   - ```json
     {
         "editor.codeActionsOnSave": {
             "source.fixAll": true
         },
         "files.eol": "\n",
         "editor.defaultFormatter": "esbenp.prettier-vscode",
         "[javascript]": {
             "editor.defaultFormatter": "esbenp.prettier-vscode"
         }
     }
     ```

5. Hora de testar o `prettier`, digite algo no `src/main.js` e salve com o `Ctrl + S`

6. Habilite o auto save do VSCode, clicando em  `File > Auto Save`.

   - Note que o auto save não formata o código, só quando usamos o `Ctrl+S` diretamente.

## Configurando EOL e Git Ignore/Attributes

No passo anterior, quando adicionamos uma configuração no `settings.json`, indicamos para o VSCode utilizar final de linha (end-of-line ou EOL) `\n` nos arquivos, também conhecido como `LF`, que é o caractere de EOL padrão dos sistemas Unix (Linux/Mac).

Geralmente isso dá bastante conflito com quem usa windows, que usa o EOL `CRLF`, que representa `\r\n`. Para evitar conflitos no futuros, iremos marcar o repositório `git` para sempre versionar arquivos usando o EOL `LF`.

3. Abra o arquivo `.gitattributes` e adicione o seguinte conteúdo:

   - ```bash
     # Handle line endings automatically for files detected as text
     # and leave all files detected as binary untouched.
     * text=false
     
     #
     # The above will handle all files NOT found below
     #
     # These files are text and should be normalized (Convert crlf => lf)
     *.css             eol=lf
     *.df              eol=lf
     *.htm             eol=lf
     *.html            eol=lf
     *.java            eol=lf
     *.js              eol=lf
     *.json            eol=lf
     *.jsp             eol=lf
     *.jspf            eol=lf
     *.jspx            eol=lf
     *.properties      eol=lf
     *.sh              eol=lf
     *.tld             eol=lf
     *.ts              eol=lf
     *.txt             eol=lf
     *.tag             eol=lf
     *.tagx            eol=lf
     *.xml             eol=lf
     *.yml             eol=lf
     
     .gitignore        eol=lf
     .gitattributes    eol=lf
     .eslintignore     eol=lf
     .prettierignore   eol=lf
     
     # These files are binary and should be left untouched
     # (binary is a macro for -text -diff)
     *.class           binary
     *.dll             binary
     *.ear             binary
     *.gif             binary
     *.ico             binary
     *.jar             binary
     *.jpg             binary
     *.jpeg            binary
     *.png             binary
     *.so              binary
     *.war             binary
     ```
   
4. Abra o site https://gitignore.io/ e digite na busca `Node`, `JetBrains`, `VisualStudioCode` e clique em `Create`;
   
   - Isso irá gerar o conteúdo do arquivo do `gitignore` para nós, contemplando as IDEs da JetBrains (WebStorm, no caso do JS), o VSCode e os arquivos do projeto Node;
   
3. Copie o conteúdo do link gerado;

   - No meu caso, o link foi: https://www.toptal.com/developers/gitignore/api/jetbrains,visualstudiocode,node
   - Você também pode pegar conteúdos de arquivos `.gitignore` no projeto oficial do GitHub: https://github.com/github/gitignore

4. Faça um commit do progresso atual e suba as modificações na nuvem.

## Modificando estilização padrão do Prettier

1. Crie um arquivo na raiz do projeto chamado `.prettierrc.json` e coloque o seguinte conteúdo:

   - ```json
     {
      "trailingComma": "all",
      "singleQuote": true,
      "endOfLine": "lf",
      "tabWidth": 4,
      "arrowParens": "avoid",
      "printWidth": 80
     }
     ```

2. Com o arquivo de configuração do `prettier` estando no formato JSON é possível usar o atalho `Ctrl + Espaço` para ter um autocomplete com os nomes das chaves que o `prettier` aceita;

3. Volte para o arquivo `main.js` e apenas salve com o `Ctrl + S`;
   
   - Note que o `quote` muda de aspas duplas para aspas simples.
   
4. Crie uma condição grande, como o código a seguir:

   - ```javascript
     const variavelNumerica = 2;
     
     if (variavelNumerica == true && variavelNumerica == true && variavelNumerica == true && variavelNumerica == true && variavelNumerica == true && variavelNumerica == true && variavelNumerica == true && variavelNumerica == true) {
         console.info('data');
     }
     ```

5. Salve o arquivo com o `Ctrl + S`;

   - Note que os operadores ficam na direita por padrão.

6. Para corrigir isso, vamos utilizar o fork `@btmills/prettier`;

  - https://www.npmjs.com/package/@btmills/prettier

7. Abra o arquivo `package.json`;

8. Rode o seguinte comando no terminal:

   - ```bash
     npm i -D prettier@npm:@btmills/prettier
     ```

9. Volte para o arquivo `main.js` e salve novamente;

   - Note que os operadores vão para a esquerda.

10. Faça um commit com progresso atual.

## Formatando o projeto inteiro e ignorando arquivos

1. Além de apertar o `Ctrl + S` para formatar o código atual, também é possível executar um comando pelo terminal para aplicar o `prettier`.

2. O comando para aplicar no projeto inteiro é:
   
   - ```bash
      npx prettier --write --ignore-unknown .
      ```
   
   - Mais informações sobre a CLI do `prettier`, acesse: https://prettier.io/docs/en/cli.html
   
- Ao executar o comando, note que diversos arquivos recebem as modificações. Arquivos com o nome em branco foram formatados e arquivos em cinza escuro não foram.

```bash
npx: instalou 1 em 1.264s
.prettierrc.json 34ms
.vscode\settings.json 5ms
package-lock.json 3ms
package.json 6ms
src\main.js 6ms
```

No casos de projetos que possuem uma pasta com o arquivo compilado ou até mesmo arquivos que não são do projeto em si, mas estão na mesma pasta, é interessante configurar o `prettier` para ignorá-los.

1. Crie uma pasta chamada `dist` com um arquivo dentro chamado `build.js`;

   - Geralmente arquivos compilados ficam em uma pasta chamada `dist`, `build` ou `bin`.

2. Adicione o seguinte conteúdo no arquivo:

   - ```javascript
     console.log(1);console.log(2);
     ```
     
   - Note que ao salvar o arquivo com o `Ctrl + S`, o `prettier` aplica a formatação.

3. Aperte `Ctrl + Z` para desfazer a formatação aplicada.

4. Experimente rodar o seguinte comando no terminal.

   - ```bash
     npx prettier --write --ignore-unknown .
     ```

   - Note que ele considera o novo arquivo criado:
     - ```bash
       npx: instalou 1 em 1.267s
       .prettierrc.json 52ms
       .vscode\settings.json 5ms
       dist\build.js 6ms
       package-lock.json 3ms
       package.json 4ms
       src\main.js 5ms
       ```

> É bem importante ter em mente que o comando `npx` só funciona caso o computador tenha conexão com a internet. Caso queira executar os comandos offline, é necessário instalar as dependências de maneira global, usando o comando:
> ```bash
> npm i -g prettier
> ```

5. Abra o arquivo `dist/build.js` e dê `Ctrl + Z` novamente para desfazer a formatação aplicada pelo comando.

6. Para ignorar essa pasta, crie um arquivo na raiz do projeto chamado `.prettierignore`;

7. Adicione o seguinte conteúdo:

   - ```bash
     [Bb]uild*
     [Dd]ist*
     [Bb]in*
     package-lock.json
     ```

   - Isso irá ignorar pastas que comecem com a palavra `build` ou `Build`.
     
      - **Por exemplo:** `build_v1` também será ignorada.
   
13. Volte para o arquivo `dist/build.js` e salve o arquivo novamente. A formatação **não** será aplicada.

14. Executando o comando do `prettier` novamente.

    - ```bash
      npx prettier --write --ignore-unknown .
      ```
      - Note ele passa a ignorar os arquivos indesejados:
    
        - ```
          npx: instalou 1 em 1.233s
          .prettierrc.json 37ms
          .vscode\settings.json 5ms
          package-lock.json 3ms
          package.json 4ms
          src\main.js 6ms
          ```

Para finalizar, o comando de execução do `prettier` pode virar um script do `npm`, para executar sempre que quiser formatar o projeto inteiro.

16. Abra o arquivo `package.json` e procure pela chave `scripts`. Substitua o script de `test` pelo seguinte conteúdo:

    - ```json
      "scripts": {
          "prettier": "npx prettier --write --ignore-unknown ."
      },
      ```

## Encontrando e corrigindo problemas no código

Além da estilização de código pelo `prettier`, é possível encontrar e corrigir possíveis problemas. Um problema clássico do JavaScript é a comparação de variáveis utilizando apenas dois iguais, que compara apenas a informação da variável, sem validar o tipo dessa informação.

**Por exemplo:** `'2'` representa uma `string` contendo o número 2, sendo diferente do que ter direto o `2` representado como `number`. No entanto, as comparações usando `==` e `===` trazem resultados diferentes:

- `'2' == 2 -> True`
- `'2' === 2 -> False`

As vezes esquecemos desse detalhe a IDE deveria nos ajudar informando esse problema de checagens não darem o resultado esperado. Uma forma de integrar isso no nosso projeto é usando o ESLint (https://eslint.org/), uma biblioteca que possibilita uma série de configurações e validações.

```js
const variavelNumerica = '2';

if (variavelNumerica == 2 && variavelNumerica === 2) {
    console.info('data');
}
```

1. Abra o arquivo `main.js` e adicione o seguinte conteúdo:

    - ```javascript
        const variavelNumerica = '2';
        
        if (variavelNumerica == 2 && variavelNumerica === 2) {
            console.info('data');
        }
        ```

2. Instale o ESLint com o comando:

    -  ```bash
        npm i -D eslint
        ```

3. Em seguida, inicialize o ESLint através do comando:

    - ```bash
        npx eslint --init
        ```

        - Selecione as seguintes opções:
          1. `To check syntax, find problems, and enforce code style`
          2. `CommonJS (require/exports)`
          3. `None of these`
          4. `No`
          5. `Node`
          6. `Use a popular style guide`
          7. `Airbnb`
          8. `JavaScript`
          9. `Yes`

4. Instale a extensão do ESLint para o VSCode;

    - Isso fará com que o save através do `Ctrl + S` também aplique as modificações do ESLint;

5. Abra o arquivo `main.js`;

    - Note os erros que o ESLint passa a exibir.

6. Abra o arquivo `.eslintrc.js` e troque a configuração que foi gerada automaticamente pelo seguinte conteúdo:
    - ```js
       module.exports = {
           env: {
               browser: true,
               commonjs: true,
               es2021: true,
           },
           extends: ['airbnb-base', 'eslint:recommended'],
           parserOptions: {
               ecmaVersion: 12,
           },
           rules: {
               'arrow-parens': 'off',
               eqeqeq: 'error',
               'function-paren-newline': 'off',
               indent: ['error', 4],
               'linebreak-style': [2, 'unix'],
               'no-console': [
                   'error',
                   {
                       allow: ['info', 'warn', 'error', 'time', 'timeEnd'],
                   },
               ],
               'no-duplicate-imports': 'error',
               'no-extra-parens': 'error',
               'no-return-await': 'error',
               'no-shadow': [
                   'error',
                   {
                       builtinGlobals: false,
                       hoist: 'functions',
                       allow: [],
                   },
               ],
               'operator-linebreak': [2, 'before', { overrides: { '?': 'after' } }],
               'import/prefer-default-export': 'off',
           },
      };
      ```

7. Abra o arquivo `main.js` e bagunce a formatação do arquivo, colocando uma aspa dupla, parênteses a mais, tabs a mais, etc.

    - Perceba que o ESLint marca tudo aquilo que está fora do padrão como sendo um erro

8. Rode o comando:

    - ```bash
        npx eslint --fix src --ext .js
        ```

    - Isso irá corrigir diversos problemas apontados pelo link, mas um deles não será corrigido, o `eqeqeq`:

       - ```
         $ npx eslint --fix src --ext .js
         
         src/main.js
           3:22  error  Expected '===' and instead saw '=='  eqeqeq
         
         ✖ 1 problem (1 error, 0 warnings)
         ```
       
       - Como esse problema altera a maneira que o código executa, o ESLint não faz a alteração, ele apenas avisa que você precisa realizá-la.

9. Corrija os problemas e execute o comando novamente;

    - Com isso, nenhuma mensagem aparecerá no console.

10. Faça um commit do progresso atual.

## Automatizando o processo no commit

Além realizar todo o processo via linha de comando ou no `Ctrl + S`, é possível automatizar isso sempre que um novo commit for feito.

1. Para isso, utilizaremos as bibliotecas `husky` e `lint-staged`.

   - O `npm husky` permite a execução de comandos a partir dos eventos do `git` como `pre-commit`, `pre-push` etc.
     - ```bash
       npm i -D husky@~4
       ```
     
     - No meu caso, a versão do `husky 5` apresentou alguns problemas, então o comando mencionado anteriormente deve instalar a versão mais recente do `husky 4`.
   - O `lint-staged` permite com que você execute comandos em arquivos que estão no `stage` do repositório `git`, para evitar com que eles entrem no seu projeto sem as validações necessárias.

     - ```bash
       npm i -D lint-staged
       ```

2. Além das duas bibliotecas mencionadas, precisamos instalar uma terceira biblioteca chamada `pretty-quick`, que permite a execução do `prettier` via linha de comando apenas para arquivos que estão no `staged`, ou seja, que estão sendo considerados no `commit` que está sendo criado.

   - ```bash
     npm i -D pretty-quick
     ```

4. Com isso, abra o arquivo `package.json` e, logo **após** a chave `scripts`, adicione o seguinte conteúdo:

   - ```json
     "husky": {
         "hooks": {
             "pre-commit": "npx lint-staged"
         }
     },
     "lint-staged": {
         "src/**/*.js": [
             "npx pretty-quick --staged",
             "npx eslint --fix src --ext .js"
         ]
     },
     ```

   - Note que adicionamos a linha `npx pretty-quick --staged` que executa o `prettier` para os arquivos no `stage` do Git.

5. Para testar, abra o arquivo `src/main.js` e realize algumas modificações que vão contra o estilo do `prettier` e do `ESLint`, mas que não quebram o código, como a modificação do `eqeqeq` que vimos anteriormente.

   - ```javascript
                const variavelNova = 9;const variavelNova2 = 3;
                   
         if (variavelNova === 9) {
                     console.info("teste " + variavelNova2);}
         ```

6. Também é importante ignorar alguns arquivos para o `ESLint`. Crie um arquivo na raiz do projeto chamado `.eslintignore` e adicione o seguinte conteúdo:

   - ```
     [Bb]uild*
     [Dd]ist*
     [Bb]in*
     package-lock.json
     ```

7. Vá no terminal e digite `git status`.

   - ```
     Changes not staged for commit:
       (use "git add <file>..." to update what will be committed)
       (use "git restore <file>..." to discard changes in working directory)
             modified:   package-lock.json
             modified:   package.json
             modified:   src/main.js
     
     Untracked files:
       (use "git add <file>..." to include in what will be committed)
             .eslintignore
     ```

8. Adicione as modificações em `stage` com o comando `git add . ` Confirme que deu certo com o `git status` exibindo o seguinte resultado:

   - ```
     Changes to be committed:
       (use "git restore --staged <file>..." to unstage)
             new file:   .eslintignore
             modified:   package-lock.json
             modified:   package.json
             modified:   src/main.js
     ```

9. Abra o arquivo `src/main.js` antes de realizar o `commit` para observar as modificações de formatação.

9. Crie um commit através do comando:

   - ```bash
     git commit -m "husky-lint"
     ```

   - O `commit` será realizado e o `husky`/`lint-staged` devem entrar em ação:

     - ```bash
       husky > pre-commit (node v12.18.4)
       [STARTED] Preparing...
       [SUCCESS] Preparing...
       [STARTED] Running tasks...
       [STARTED] Running tasks for src/**/*.js
       [STARTED] npx pretty-quick --staged
       [SUCCESS] npx pretty-quick --staged
       [STARTED] npx eslint --fix src --ext .js
       [SUCCESS] npx eslint --fix src --ext .js
       [SUCCESS] Running tasks for src/**/*.js
       [SUCCESS] Running tasks...
       [STARTED] Applying modifications...
       [SUCCESS] Applying modifications...
       [STARTED] Cleaning up...
       [SUCCESS] Cleaning up...
       [main f731c51] husky-lint
       4 files changed, 860 insertions(+), 4 deletions(-)
       create mode 100644 .eslintignore
       ```


## Commit via GitHub Desktop, VSCode, WebStorm

Com os hooks configurados no projeto, independente de qual sistema seja usada para criação dos commits, o `lint-staged` será executado. Experimente fazer os commits pelo GitHub Desktop, VSCode Source Control ou pelo VCS do WebStorm.

## Conclusão

Com essa configuração, o projeto está preparadíssimo para o desenvolvimento em NodeJS com JavaScript. As configurações apresentadas são resultados de alguns anos trabalhando com NodeJS e diversos problemas enfrentados como:

- Equipe usando diferentes IDEs no mesmo ambiente (Visual Studio Code, WebStorm, etc)
- Diferentes sistemas operacionais (Linux, Mac e Windows)
- Formatação de código gerado pelo sistema ou códigos de bibliotecas
- Erros ao realizar o commit pelo `git` no terminal, GitHub Desktop ou pelas próprias IDEs
- Padronização de código ficava diferente dependendo da IDE que a pessoa usava
- Extensas discussões sobre qual padrão de código usar e como melhorar a leitura dos projetos. O padrão apresentado nesse template é uma sugestão, modifique da forma que achar melhor.
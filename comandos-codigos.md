# Linhas de Comandos e Trechos de Código

> Os trechos de código estão atualizados nos arquivos do template, disponíveis em: https://github.com/FabricaDeSinapse/fabrica-sinapse-nodejs-template



Inicie o projeto Node, gerando o `package.json`, digitando no terminal:

- ```bash
  npm init -y
  ```



Criação do `package-lock.json`:

- ```bash
  npm i
  ```



Instale o `prettier` no projeto:

- ```bash
  npm i -D prettier
  ```



Arquivo `settings.json`:

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



Arquivo `.gitattributes`:

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



Arquivo `.gitignore`:

- https://www.toptal.com/developers/gitignore/api/jetbrains,visualstudiocode,node



Arquivo `.prettierrc.json`:

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



Fork `@btmills/prettier`:

  - ​	https://www.npmjs.com/package/@btmills/prettier

Instalar o fork `@btmills/prettier`:

- ```bash
  npm i -D prettier@npm:@btmills/prettier
  ```



Aplicar o `prettier` no projeto inteiro:

- ```bash
   npx prettier --write --ignore-unknown .
   ```

   - Mais informações sobre a CLI do `prettier`, acesse: https://prettier.io/docs/en/cli.html



> É bem importante ter em mente que o comando `npx` só funciona caso o computador tenha conexão com a internet. Caso queira executar os comandos offline, é necessário instalar as dependências de maneira global, usando o comando:
> ```bash
> npm i -g prettier
> ```



Conteúdo do arquivo `.prettierignore`:

- ```bash
  [Bb]uild*
  [Dd]ist*
  [Bb]in*
  package-lock.json
  ```



Declaração do script `npm run prettier` no `package.json`:

- ```json
  "scripts": {
      "prettier": "npx prettier --write --ignore-unknown ."
  },
  ```




ESLint

- https://eslint.org/

Instale o ESLint com o comando:

-  ```bash
    npm i -D eslint
    ```

Inicialize o ESLint através do comando:

- ```bash
    npx eslint --init
    ```



Conteúdo do arquivo `.eslintrc.js`:

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



Rodar o ESLint:

- ```bash
    npx eslint --fix src --ext .js
    ```



Instalar o Husky 4:

- ```bash
  npm i -D husky@~4
  ```



Instalar o Lint-Staged:

- ```bash
  npm i -D lint-staged
  ```



Instalar o Pretty-Quick:

- ```bash
  npm i -D pretty-quick
  ```



Husky e Lint-Staged no arquivo `package.json`:

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



Conteúdo do arquivo `.eslintignore`:

- ```
  [Bb]uild*
  [Dd]ist*
  [Bb]in*
  package-lock.json
  ```



Comandos Git

- ```bash
  git status
  git add .
  git commit -m "husky-lint"
  ```


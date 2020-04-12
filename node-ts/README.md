# Configurando projeto TypeScript

## Iniciando um projeto Node.js

``` $ yarn init -y ```

## Adicionando libs 

``` $ yarn add express ```

- Nada de diferente até aqui, adicionamos um projeto normal com `yarn init -y` e 
adicionamos o express logo em seguida.

## Libs para o TypeScript

``` $ yarn add typescript @types/express -D ```

- Aqui já vem a primeira peculiaridade, primeiro precisamos adicionar o `TypeScript` 
ao projeto e depois uma lib de tipos para o express usando TypeScript, que são os 
`@types/express`, essa mesma lib também existe para diversos outros pacotes, 
usando sempre o prefixo `@types/LIB_NAME`. Consulte no NPM antes de fazer a instalação.

## Configurando estrutura

* Ao instalar o pacote `typescript` temos acesso ao binário `tsc`, ele permite rodar 
o TypeScript para gerar o JavaScript após finalização das alterações no código. 
Para rodar é só passar `yarn tsc index.js`, porém vamos criar uma organização para 
separa o nosso código mantido pelos desenvolvedores (TypeScript) do gerado para o 
Node.js (JavaScript).

``` $ yarn tsc --init ```

- Essce comando irá criar um arquivo `tsconfig.json` dentro do diretorio raiz do 
projeto, onde estão as configurações do TypeScript. Dentro dele iremos apenas tirar 
os comentários da linha `15` e colocar `"outDir": "./dist"`. Esse será nosso destino 
de saída após converter o TypeScript para JavaScript e serão os arquivos que iremos 
rodar com nosso servidor de aplicação Node.js já que ele não entende o TypeScript. 

``` $ touch src/index.ts ```

- Aqui criamos um arquivo na nossa pasta `src` com a extensão `.ts` que é a usada pelo
TypeScript, e dentro dele vamos colocar o seguinte código como exemplo: 

```
  import express from 'express';

  const app = express();

  app.get('/', (req, res) => {
    return res.json({message: 'Hello project in TypeScript.'})
  });


  app.listen(3333);
```

- Até o momento um código JavaScript normal, que está iniciando um servidor com 
express e expondo uma rota `GET: '/'` com um retorno em JSON. O TypeScript entra 
ação agora, roandao: 

``` $ yarn tsc ```

- Agora ele vai buscar todos os arquivos que tiverem a extensão `.ts`, converter 
eles para JavaScript e jogar a extensão `.js` permitindo a leitura pelo Node.js. 

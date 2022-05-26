# Busca Cep :green_heart:
## Aplicação para listar ceps e gerar endereços através da API ViaCEP com layout de dashboard.

### Telas
<div>
  <img src="https://user-images.githubusercontent.com/58118544/170554693-684b7768-ed36-4ed0-980a-d69fa2719fa3.png"/>
  <img src="https://user-images.githubusercontent.com/58118544/170554695-15744bd7-30a4-4545-8bc6-4e7fe437e801.png"/>
  <img src="https://user-images.githubusercontent.com/58118544/170554697-dca1db72-367a-4cc3-a746-4383b4703f70.png"/>
  <img src="https://user-images.githubusercontent.com/58118544/170554687-ce323b8a-2c75-4072-b9a4-0c66f4759f44.png"/>
 </div>

### Definições:
- insere cep digitado na lista
- verifica se cep existe
- mostra notificação caso cep digitado já existe na lista
- mostra notificação caso cep não exista
- mostra notificação caso tente se enviar com campo vazio
- é possível enviar cep para lista com enter ou clicando no botão Adicionar Endereço
- campo aceita formatos 0000000 e 00000-00
- clicando em Gerar Endereços mostra cards com rua, bairro, cidade e estado, seguido pelo cep correspondente na sua lateral e botão para excluir
- é possível excluir clicando no lixo localizado à direita do card
- caso excluido um dos cards é possível clicar em Gerar Endereços novamente, será verificado qual endereço falto em correspondencia com a lista de ceps e adicionado somente o faltante, não repetindo nem na lista nem nos cards.

### Tecnologias:
- <img src="https://img.shields.io/static/v1?label=vue&message=framework&color=green&style=for-the-badge&logo=Vue"/>
- <img src="https://img.shields.io/static/v1?label=axios&message=Request&color=blueviolet&style=for-the-badge&logo=AXIOS"/>
- <img src="https://img.shields.io/static/v1?label=javascript&message=Programming%20language&color=yellow&style=for-the-badge&logo=JAVASCRIPT"/>
- <img src="https://img.shields.io/static/v1?label=sass&message=Style Sheets&color=pink&style=for-the-badge&logo=SASS"/>

### Deploy com Surge: 📘 
[buscaCep]()

### Como rodar a aplicação:
No terminal clone o projeto:
```
https://github.com/ThiagodaSilva27/busca-cep.git
```
Entre na pasta do projeto:
```
cd busca-cep
```
Instale as dependencias:
```
npm i
npm i -g sass
npm i vue-router
npm i --save vue-basic-alert

```
Execute a aplicação:
```
npm run serve
```

## Linguagens e libs :books:

- [Vue](https://devdocs.io/vue/)
- [Javascript](https://developer.mozilla.org/pt-BR/docs/Web/JavaScript)
- [Axios](https://www.npmjs.com/package/axios)
- [Sass](https://sass-lang.com/)

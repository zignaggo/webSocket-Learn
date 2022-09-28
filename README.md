# Web Socket

## Criar novo WebSocket

```javascript
var exampleSocket = new WebSocket("ws://www.example.com/socketserver", "protocolOne");
```

> Dois parâmetros na criação do webSocket. O primeiro é a url, já o segundo são os protocolos a ser seguidos (Caso seja necessário o uso de mais de um protocolo, é só passar uma lista dos protocolos)

* ws - Será substituído por http
* wss - Será substituído por https

---

## Enviar dados ao servidor

```javascript
exampleSocket.send("Aqui vai algum texto que o servidor esteja aguardando urgentemente!");
```

> Método assíncrono, propenso a causar erros. Para garantir o envio somente quando a conexão é feita, chamamos o envio dentro do manipulador de eventos ***onopen***

```javascript
exampleSocket.onopen = function (event) {
  exampleSocket.send("Aqui vai algum texto que o servidor esteja aguardando urgentemente!");
};
```
---

## Receber dados do servidor

```javascript
exampleSocket.onmessage = function (event) {
  console.log(event.data);
}
```
> Nada a declarar. É bem intuitivo

---

## Fechar servidor

```javascript
exampleSocket.close();
```
> Nada a declarar. É bem intuitivo
---

## Erros
```javascript
exampleSocket.onerror = function(error) {
  alert(`[error] ${error.message}`);
};
```
---

## Links

* [JavaScriptInfo](https://javascript.info/websocket)
* [MdnWebDocs](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)

---
## Considerações de Segurança

WebSockets não devem ser utilizados em um contexto de um ambiente misto, isto é, você não deveria abrir uma conexão não-segura a partir de uma página previamente carregada utilizando HTTPS, ou vice-versa. A maioria dos browsers atuamente apenas permitem conexões seguras pelo Websocket, e não mais suportam contextos diferentes desse.
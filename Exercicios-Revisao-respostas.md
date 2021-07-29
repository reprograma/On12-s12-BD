<h1 align="center">
    <br>
    <p align="center">Exercício Revisão<p>
</h1>

## Documentação MongoDB - Tutorial
https://docs.mongodb.com/manual/tutorial/query-documents/

## Vendas de Roupas

Temos uma loja de roupas e queremos controlar nossas vendas.

### Criação de novo database

```
use loja-roupas
```

### Criação de nova collection

```
db.createCollection('vendas')
```

### Inserindo documentos na collection

```
db.vendas.insertMany([
    {
        "status": "ENTREGUE",
        "pagamento": "CARTAO_CREDITO",
        "valor": 189.70,
        "dataEntrega": ISODate("2021-06-20T09:00Z"),
        "itens" : [
            { 
                "categoria": "CALCA", 
                "nome": "Calça jeans",
                "valor": 59.90,
            },
            { 
                "categoria": "CAMISETA", 
                "nome": "Blusinha Pink",
                "valor": 39.90,
            },
            { 
                "categoria": "CALCADOS", 
                "nome": "Scarpin",
                "valor": 89.90,
            },
        ],
        "cliente": {
            "nome": "Maria do Bairro",
            "endereco": "Rua das Quitandas 123",
            "estado": "SP"
        },
    },
    {
        "status": "AGUARDANDO_PAGAMENTO",
        "pagamento": "BOLETO",
        "valor": 50.90,
        "dataEntrega": null,
        "itens" : [
            { 
                "categoria": "ACESSORIO", 
                "nome": "Cinto Preto",
                "valor": 45.90,
            },
            { 
                "categoria": "ACESSORIO", 
                "nome": "Brinco de Argola",
                "valor": 5.00,
            },
        ],
        "cliente": {
            "nome": "Jaqueline Souza",
            "endereco": "Rua das Margaridas 194 apto 403",
            "estado": "RJ"
        },
    },
    {
        "status": "EM_SEPARACAO",
        "pagamento": "CARTAO_CREDITO",
        "valor": 189.70,
        "dataEntrega": null,
        "itens" : [
            { 
                "categoria": "VESTIDO", 
                "nome": "Vestido Paete",
                "valor": 120.00,
            },
            { 
                "categoria": "CALCADO", 
                "nome": "Sandalia",
                "valor": 90.00,
            },
        ],
        "cliente": {
            "nome": "Jaqueline Souza",
            "endereco": "Rua das Laranjeiras 500 apto 303",
            "estado": "PE"
        },
    },
    {
        "status": "ENTREGUE",
        "pagamento": "CARTAO_CREDITO",
        "valor": 175.90,
        "dataEntrega": ISODate("2021-06-15T09:00Z"),
        "itens" : [
            { 
                "categoria": "VESTIDO", 
                "nome": "Vestido de Renda",
                "valor": 150.00,
            },
            { 
                "categoria": "ACESSORIO", 
                "nome": "Tiara",
                "valor": 25.90,
            },
        ],
        "cliente": {
            "nome": "Maria do Bairro",
            "endereco": "Rua das Quitandas 123",
            "estado": "SP"
        },
    },
    {
        "status": "ENTREGUE",
        "pagamento": "CARTAO_CREDITO",
        "valor": 195.90,
        "dataEntrega": ISODate("2021-06-19T09:00Z"),
        "itens" : [
            { 
                "categoria": "VESTIDO", 
                "nome": "Vestido de Renda",
                "valor": 150.00,
            },
            { 
                "categoria": "CALCA", 
                "nome": "Calça Legging",
                "valor": 45.90,
            },
        ],
        "cliente": {
            "nome": "Laura Maria",
            "endereco": "Rua da Esperança 90",
            "estado": "PE"
        },
    },
    {
        "status": "ENTREGUE",
        "pagamento": "BOLETO",
        "valor": 70.00,
        "dataEntrega": ISODate("2021-05-04T09:00Z"),
        "itens" : [
            { 
                "categoria": "ACESSORIO", 
                "nome": "Brinco Perolado",
                "valor": 30.00,
            },
            { 
                "categoria": "ACESSORIO", 
                "nome": "Pulseira dourada",
                "valor": 40.00,
            },
        ],
        "cliente": {
            "nome": "Fabiana Rita",
            "endereco": "Rua das Pedras 80",
            "estado": "BA"
        },
    },
    {
        "status": "ENTREGUE",
        "pagamento": "CARTAO_CREDITO",
        "valor": 15.00,
        "dataEntrega": ISODate("2021-05-14T09:00Z"),
        "itens" : [
            { 
                "categoria": "ACESSORIO", 
                "nome": "Chaveiro",
                "valor": 15.00,
            },
        ],
        "cliente": {
            "nome": "Fabiana Rita",
            "endereco": "Rua das Pedras 80",
            "estado": "BA"
        },
    },
    {
        "status": "ENTREGUE",
        "pagamento": "BOLETO",
        "valor": 35.00,
        "dataEntrega": ISODate("2021-05-14T09:00Z"),
        "itens" : [
            { 
                "categoria": "ACESSORIO", 
                "nome": "Tiara",
                "valor": 35.00,
            },
        ],
        "cliente": {
            "nome": "Laura Helena",
            "endereco": "Rua do Bosque 123",
            "estado": "SP"
        },
    },
]);
```

## Exercícios de Consultas

1 - Todas as vendas que já foram entregues;
```
db.getCollection('vendas').find({ status: 'ENTREGUE'})
```

2 - Todas as vendas que já foram entregues ordenando pela data de entrega (do que foi entregue ANTES para o que foi entregue depois); 
```
db.getCollection('vendas').find({ status: 'ENTREGUE'}).sort({'dataEntrega': 1})
```

3 - Todas as vendas que já foram entregues ordenando pela data de entrega (do que foi entregue DEPOIS para o que foi entregue antes); 
```
db.getCollection('vendas').find({ status: 'ENTREGUE'}).sort({'dataEntrega': -1})
```

4 - Todas as vendas que já foram entregues ordenando pela data de entrega (do que foi entregue DEPOIS para o que foi entregue antes) e valor (do mais barato para o mais caro)
```
db.getCollection('vendas').find({ status: 'ENTREGUE'}).sort({'dataEntrega': -1, 'valor': 1})
```

5 - Todas as vendas que tiveram o item de categoria VESTIDO;
```
db.getCollection('vendas').find({ "itens": { $elemMatch: {  categoria: "VESTIDO" } } } )
```

6 - Quantas vendas tiveram de categoria VESTIDO;
```
db.getCollection('vendas').count({ "itens": { $elemMatch: {  categoria: "VESTIDO" } } } )
```

7 - Todas as vendas que tiveram item de categoria ACESSORIO ou CALCA;
```
db.getCollection('vendas').find({ "itens": { $elemMatch: { $or: [ { categoria: "ACESSORIO" }, { categoria: "CALCA" } ] } } } )
```

ou

```
db.getCollection('vendas').find({ "itens": { $elemMatch: { categoria: {$in: ["ACESSORIO", "CALCA"] }  } } })
```

8 - Todas as vendas que o endereço de entrega é em PE (Pernambuco);
```
db.getCollection('vendas').find({ "cliente.estado": "PE"})
```

9 - Todas as vendas que o endereço de entrega não foi em PE (Pernambuco);
```
db.getCollection('vendas').find({ "cliente.estado": { $ne: "PE" } })
```

10 - Todas as vendas que o endereço de entrega é em PE (Pernambuco) e que o valor seja maior que 190 reais;
```
db.getCollection('vendas').find({ "cliente.estado": "PE", valor: { $gt: 190 } })
```

11 - Todas as vendas que o endereço de entrega é em PE (Pernambuco) e que o valor seja menor que 190 reais;
```
db.getCollection('vendas').find({ "cliente.estado": "PE", valor: { $lt: 190 } })
```

12 - Todas as vendas que o endereço de entrega é em PE (Pernambuco) e que o valor seja maior que 195.90 reais;
```
db.getCollection('vendas').find({ "cliente.estado": "PE", valor: { $gt: 195.90 } })
```

13 - Todas as vendas que o endereço de entrega é em PE (Pernambuco) e que o valor seja maior (INCLUSIVE) que 195.90 reais;
```
db.getCollection('vendas').find({ "cliente.estado": "PE", valor: { $gte: 195.90 } })
```

14 - Todas as vendas que o endereço de entrega é em PE (Pernambuco) e que o valor seja menor que 189.70 reais;
```
db.getCollection('vendas').find({ "cliente.estado": "PE", valor: { $lt: 189.70 } })
```

15 - Todas as vendas que o endereço de entrega é em PE (Pernambuco) e que o valor seja menor (INCLUSIVE) que 189.70 reais;
```
db.getCollection('vendas').find({ "cliente.estado": "PE", valor: { $lte: 189.70 } })
```

16 - As duas primeiras vendas que foram entregues (ordenada por data entrega e valor);
```
db.getCollection('vendas').find({status:'ENTREGUE'}).sort({ dataEntrega: 1, valor: 1}).limit(2)
```

17 - A terceira venda que foi entregue (ordenada por data entrega e valor);
```
db.getCollection('vendas').find({ "status": "ENTREGUE"}).sort({ dataEntrega: 1, valor: 1}).skip(2).limit(1)
```

18 - Selecionar apenas status e valor das vendas entregues (com id);
```
db.getCollection('vendas').find({status:'ENTREGUE'},{status: 1, valor: 1})
```

19 - Selecionar apenas status e valor da venda (sem id);
```
db.getCollection('vendas').find({status:'ENTREGUE'},{status: 1, valor: 1, _id: 0})
```

20 - Quantas vendas já foram entregues;
```
db.getCollection('vendas').count({status:'ENTREGUE'})
```

21 - Quanto de dinheiro a loja vendeu de itens;
```
db.getCollection('vendas').aggregate(
    { $match: {}},
    { $group: { _id : null, soma: { $sum: "$valor" } } }
)
```

22 - Quanto de dinheiro a loja vendeu de itens com pagamento BOLETO;
```
db.getCollection('vendas').aggregate(
    { $match: { pagamento: "BOLETO"}},
    { $group: { _id : null, soma: { $sum: "$valor" } } }
)
```

23 - Atualizar endereço da cliente Maria do Bairro;
```
db.getCollection('vendas').update(
    { "cliente.nome" : "Maria do Bairro" },
    { $set:
        { 
            "cliente.endereco": "Rua das Flores 40" 
        }
    }
);
```

24 - Excluir vendas que não tem o status ENTREGUE;
```
db.getCollection('vendas').remove({ status: { $ne: "ENTREGUE"}})
```

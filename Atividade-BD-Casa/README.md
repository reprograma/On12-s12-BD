#### On12-s12-BD Projeto | Projeto Database

### Olá nesta semana introduzimos sobre Banco de Dados MongoDB :eyes:

  
Criamos um Banco de dados com os seguintes comandos:

* Inserção de documentos
* Atualização de documentos
* Exclusão de documentos
* Consulta com projeção
* Consulta utilizando combinação entre os seletores
* Consulta paginada e ordenada (utilizar *skip*, *limit* e *sort*)


![robo t3.png](https://media-exp1.licdn.com/dms/image/C4D12AQE1KOkhZuskxw/article-cover_image-shrink_600_2000/0/1565746780682?e=1632960000&v=beta&t=PYHwYT8p0xmAB2CmQYHSsSKPdHEKkESVQWtW2zWXRu8)


1. Inicializei o mongoDB no Prompt de Comando , em seguida instalei o ROBO T3 para conectar ao nosso banco de dados .

2. Em um novo Pronpt de Comando usei o comando use CepCidades para criar o novo banco de dados e o db.createCollection para criar as consultas.

3. Agora já no Robo3T eu criei uma collection  chamada consulta para visualisar e buscar o ceps que  estão listados no arquivo Json.

4. O arquivo criado para consultar o endereço de algumas capitais do Brasil , salve o json e rode os comandos a seguir.


Agora vamos criar nossas consultas ? :rocket:

* para inserção de documentos:
* Inserir - `db.getcollection('consultas').insert(documento)`
```
 db.getCollection('Consultas').insert([
{
  "cep": "04180-112",
  "logradouro": "Travessa 19 de Agosto",
  "complemento": "",
  "bairro": "Jardim Maria Estela",
  "localidade": "São Paulo",
  "uf": "SP",
  "ibge": "3550308",
  "gia": "1004",
  "ddd": "11",
  "siafi": "7107"

}

])
```

* Atualização de documentos:
* Atualizar - `db.getcollection('consultas).update({selecao}, {$set:{campos-atualizados}})`
```
db.getCollection('Consultas').update(
    // query 
    {
        "logradouro.nome" :  "Travessa 19 de Agosto"
    },
    
    // update 
    {
        "logradouro":  "Travessa 19 de Agosto 1965"
    },
    
    // options 
    {
        "multi" : false,  // update only one document 
        "upsert" : false  // insert a new document, if no existing document match the query 
    }
);
```

* Exclusão de documentos:

* Excluir - `db.getcollection.remove({seleciona o que sera removido})`

`db.getCollection('Consultas').remove({ "logradouro":"Travessa 19 de Agosto 1965"})`


* Consulta com projeção:
* Projetar - `db.getcollection.find({selecao},{<key>:1})`

`db.getCollection('Consultas').find({},{"localidade": 1, "_id": 0})`

* Consulta utilizando combinação entre os ceps:

`db.getcollection('Consultas').find({informacao}).pretty()`

```
db.getCollection('Consultas').find(

{"logradouro": "Travessa 19 de Agosto",
  "complemento": "",
  "bairro": "Jardim Maria Estela",
  "localidade": "São Paulo",
  }).pretty() 
 ```


* Consulta paginada e ordenada (utilizar *skip*, *limit* e *sort*)

1. **db.getcollection.find({selecao}).skip(qtd)** 

* `db.getCollection('Consultas').find().skip(2)`

2. **db.getcollection.find({selecao}).limit(qtd)**

* `db.getCollection('Consultas').find().limit(2)`

3. **db.getcollection.find({selecao}).sort(decrescente -1)**

* `db.getCollection('Consultas').find().sort({cep: -1})`

4. **db.getcollection.find({selecao}).sort(crescente 1)**

* `db.getCollection('Consultas').find().sort({cep: 1})`
 


#### Particularmente gostei muito dessa ferramenta e espero que a conheçam e a utilizem em seu dia a dia.:sunglasses:

#### E é isso, até a próxima... :smile:
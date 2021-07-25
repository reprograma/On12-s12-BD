<h1 align="center">
    <br>
    <p align="center">Mongo Online<p>
</h1>

## Mongo Online

Criei um banco de dados online para caso não tenha sido possível realizar a instalação do mongo na máquina. Vou deixar esse banco de dados, que é compartilhado, disponível enquanto estiver acontecendo o curso.

Para acessá-lo deverá ter instalado na máquina o Mongosh. Para instalar o Mongosh no mac, deve-se rodar o comando abaixo no terminal:

```
brew install mongosh
```

Com o mongosh instalado deve-se utilizar o comando abaixo para se conectar na base de dados:

```
mongosh "mongodb+srv://cluster0.kuokc.mongodb.net/reprograma" --username alunareprograma
```

Ao rodar o comando irá pedir a senha. Com isso deverá digitar *@reprograma12* e pressionar enter. Com isso você estará conectada ao banco de dados mongo online que criei. Fique a vontade para criar novas Collections e fazer os exerícios da semana utilizando esse terminal.



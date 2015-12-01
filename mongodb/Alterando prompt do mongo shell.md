#Alterando o prompt do mongo shell

O prompt do mongo shell apresenta por padrão três informações 

 1. host onde esta em execução
 2. versão do mongodb em use, e
 3. banco de dados corrente

As duas primeiras informações são irrelevantes se a sua execução é local ou em servidor conhecido, além de atrapalhar a leitura do terminal. 

Veja abaixo alguns exemplos para diferentes sistemas operacionais, sendo o pior caso a instalação windows que apresenta ainda o drive e pasta onde o executável esta instalado:

 - MacBook-Pro-de-xxxxxxxxxx(mongod-3.0.7) be-mean-pokemons>
 - linux(mongod-2.6.10) be-mean-pokemons>
 - xxxxxxxxx-debian(mongod-3.0.7) be-mean-pokemons>
 - Mac-mini-de-xxxxxxxx(mongod-3.0.7) be-mean-pokemons>
 - 5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons>
 - Ubuntu-pc(mongod-3.0.7) be-mean-pokemons>
 - RNEQHOME(D:\mongodb\bin\mongod.exe-3.0.7)be-mean-pokemons>

Para alterar esse padrão, mostrando apenas o baco de dados em use digite o seguinte comando após iniciar o mongo client:
```
var prompt = function() {return db + "> ";}
```

fonte: https://docs.mongodb.org/manual/
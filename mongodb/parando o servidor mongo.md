#Parando o servidor mongodb

No ambiente windows você pode executar o servidor mongodb como um serviço para uso contínuo, ou em caso de estudo/desenvolvimento pode ativá-lo pelo shell apenas no momento necessário.

Parando o serviço do mongodb no windows

```
net stop MongoDB
```

Desinstalar o serviço no windows

```
"C:\mongodb\bin\mongod.exe" --remove
```

Se você estiver executando o servidor mongodb numa instância do shell ( cmd ou powershell inicie o client mongo.exe e execute os seguintes comandos:

```
use admin
db.shutdownServer()
exit
```

Após isso apenas finalize as janelas do shell onde o servidor e o client estavam em execução.

ATENÇÃO: interromper o servidor com CTRL-C até funciona mas pode danificar suas coleções.

fonte: https://docs.mongodb.org/manual/
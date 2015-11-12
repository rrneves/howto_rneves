mongodb - instalação windows

1) Pré requisitos: Windows Server 2008 R2, Windows 7 ou superior, versões de 32 ou 64bits, sempre que possível utilize a versão 64.  Apesar de eventualmente funcionar no server 2003, consulte a documentação, é desaconselhável na medidade que que este SO não tem mais suporte ou atualização.

2) Para determinar a versão SO onde será instalado o servidor execute os seguintes comandos no prompt do DOS ou no powershell

wmic os get caption
wmic os get osarchitecture

3) Faça o download da versão adequada do mongodb para o seu caso no endereço: https://www.mongodb.org/downloads?_ga=1.37022885.48052022.1445543724#production

   Você pode fazer o download do versão compactada ou instalador windows, não faz diferença qual delas vai utilizar na medida em que o mongodb é autocontido, ou seja tudo será instalado em uma única pasta sem dependências externas do Sistema Operacional.
   
4) O padrão de instalação assume que o software e a pasta de dados ficam no disco principal do seu computador: o drive c:, como esse tipo de instalação pode não ser interessante, seja por questões de tempo de acesso ou espaço disponível. 

   c:\mongodb\bin  - programas
   c:\data\db      - dados
   
   A título de execício vamos documentar a instalação de programa e dados num disco secundário D:, para a instalação padrão basta substituir a drive de d: para c: ou omitir a informação.
   
   d:\mongodb\bin       - programas
   d:\mongodb\data\db   - dados
   d:\mongodb\data\log  - arquivos de log
   
5) Crie a estrutura de pastas no local escolhido e execute o instalador:

   msiexec.exe /q /i mongodb-win32-x86_64-2008plus-ssl-3.0.7-signed.msi INSTALLLOCATION="D:\mongodb" ADDLOCAL="all"
   
   caso tenha feito o download compactado descompacte e mova os arquivos para a pasta d:\mongodb

   Para maiores iformações das opções de instalação consulte: https://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows
   
   Programs isntalados na pasta bin:
   
   Server	        mongod.exe
   Router	        mongos.exe
   Client	        mongo.exe
   Monitoramento        mongostat.exe, mongotop.exe
   ImportExportação	mongodump.exe, mongorestore.exe, mongoexport.exe, mongoimport.exe
   Miscellanea  	bsondump.exe, mongofiles.exe, mongooplog.exe, mongoperf.exe

6) Voce pode subir o servidor como um serviço do windows ou no prompt do cmd ou no powershell e neste caso a janela o prompt deverá ficar aberta durante a utilização.


Crie um arquivo mongodb.cfg em d:\mongodb\bin, com o seguinte conteudo:

systemLog:
    destination: file
    path:        d:\mongodb\data\log\mongod.log

storage:
    dbPath:      d:\data\db

net:
   bindIp:       127.0.0.1
   port:         27017
   
ATENÇÃO: Não utilize tab e sim espaço para identação. Este são parâmetros básicos do mongodb que você pode querer alterar por segunrança ou comodidade em sua rede local.

Esta configuração diz ao servidor para aceitar conexões apenas no localhost e na porta padrão, para permitir acesso a partir de outras estações de trabalho altere o bind, caso utilize outra porta não esquecça de libera-la no firewall e infoma-la ao carregar o client.

 
6A) Executando o servidor no terminal, abra o powersell e digite:

d:\mongodb\bin\mongod -f d:\mongodb\bin\mongo.cfg

lembre-se que você ode economizar digitação colocando o caminho dos executáveis na variável de ambinete PATH do windows, isso não se aplica para o arquvio de configuração, então voce pode optar se posicionar na pasta d:\mongodb\bin antes de subir o servidor.

6B) Executando o servidro como serviço no windows

para instalar o servico execute o terminal ( cmd ou powershell como administrador e execute o seguinte comando:

"D:\mongodb\bin\mongod.exe" --config "D:\mongodb\mongod.cfg" --install

Iniciar o servidor:

net start MongoDB

Para o servidor

net stop MongoDB

Desinstalar o serviço no windows

"D:\mongodb\bin\mongod.exe" --remove

fonte: https://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows/
##Como limpar o spool do windows

Você mandou uma impressão errada, cancelou, mas o Windows continua a imprimir aqueles caracteres malucos? 

Você reiniciou o computador, desligou a impressora e isso não resolveu ? 

Tudo bem, todos nós passamos por isso, vez ou outra. 

Para limpar a fila de impressão desses arquivos e voltar a operação normal siga os passos abaixo:

Abra uma janela do MS-Dos, como administrador e execute os comandos abaixo:

```
net stop spooler <Enter>
cd c:\windows\system32\spool\PRINTERS <Enter>
del /f /s *.shd <Enter>
del /f /s *.spl<Enter>
net start spooler <Enter>
exit <Enter>
```

Você também pode montar esse comandos em um arquivo .BAT e automatizar o processo.



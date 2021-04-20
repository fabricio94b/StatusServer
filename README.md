# StatusServer
__Parte 1 - Baixando Script__ 

```cd /root && wget https://raw.githubusercontent.com/fabricio94b/StatusServer/main/onlineapp.sh && chmod +x onlineapp.sh```


__Parte 2: Instalando Apache2 e Cron__

```apt install apache2 && apt install cron```

Ps:Se der erro na instalação do apache pode ser por causa da porta 80 rodando no sever,só parar e dar reboot na máquina,e instalar de novo;

__Parte 3: Configurando portas e pastas no apache:__

```nano /etc/apache2/ports.conf```

__Troque a porta 80 ou qualquer outra que tiver pra qualquer outra porta,exemplo:__

__Listen 80 » Listen 8888__

__Salve o arquivo (Ctrl + O e Ctrl + X)__

```service apache2 restart```

__Criar a pasta:__

```cd /var/www/html && mkdir server```

__Parte 4: Rodando Script pra testar__

```cd /root && ./onlineapp.sh```

__Agora entre na IP+PORTA do seu server no diretório /server/online e veja se retornou algum número,exemplo:__

http://191.96.224.142:8888/server/online

__Parte 5: Atualizando pelo cron__

__Vamos trabalhar com a atualização dos users online no server a cada 1 min__

```crontab -e```

__Add no final do arquivo:__

```*/1 * * * * cd  /root/ && ./onlineapp.sh```

__Salve e feche o arquivo__

```service cron reload```

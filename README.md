# StatusServer
Parte 1 - Baixando Script 

cd /root && wget http://downloads.onehostbr.xyz/files/online-script/onlineapp.sh && chmod +x onlineapp.sh


Parte 2: Instalando Apache2 e Cron

apt install apache2 && apt install cron

Ps:Se der erro na instalação do apache pode ser por causa da porta 80 rodando no sever,só parar e dar reboot na máquina,e instalar de novo;

Parte 3: Configurando portas e pastas no apache:

nano /etc/apache2/ports.conf

Troque a porta 80 ou qualquer outra que tiver pra qualquer outra porta,exemplo:

Listen 80 » Listen 8888

Salve o arquivo (Ctrl + O e Ctrl + X)

service apache2 restart

Criar a pasta:

cd /var/www/html && mkdir server

Parte 4: Rodando Script pra testar

cd /root && ./onlineapp.sh

Agora entre na IP+PORTA do seu server no diretório /server/online e veja se retornou algum número,exemplo:

http://191.96.224.142:8888/server/online

Parte 5: Atualizando pelo cron

Vamos trabalhar com a atualização dos users online no server a cada 1 min

crontab -e

Add no final do arquivo:

*/1 * * * * cd  /root/ && ./onlineapp.sh

Salve e feche o arquivo

service cron reload

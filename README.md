# wordpres-medway-challenge


### 0 - Login

<code>ssh -i medway medway@your_server_IP_address</code>

### 1 - Instalar Apache

O servidor da web Apache é atualmente o servidor da web mais popular do mundo, o que o torna uma ótima opção padrão para hospedar um site.

Podemos instalar o Apache facilmente usando o gerenciador de pacotes do CentOS yum,. Um gerenciador de pacotes nos permite instalar a maioria dos softwares sem dor de um repositório mantido pelo CentOS. Você pode aprender mais sobre como usaryum aqui.

Para nossos propósitos, podemos começar digitando estes comandos:

<code>sudo yum install httpd</code>

Como estamos usando um sudocomando, essas operações são executadas com privilégios de root. Ele pedirá sua senha de usuário normal para verificar suas intenções.

Depois disso, seu servidor web é instalado.

Depois de instalado, você pode iniciar o Apache em seu VPS:

<code>sudo systemctl start httpd.service</code>

Você pode fazer uma verificação pontual imediatamente para verificar se tudo correu conforme o planejado, visitando o endereço IP público do seu servidor em seu navegador da web (consulte a observação no próximo título para descobrir qual é o seu endereço IP público se você não tiver essa informação já):

<code>http://your_server_IP_address/</code>

Você verá a página da web padrão do CentOS 7 Apache, que existe para fins informativos e de teste. Deve ser parecido com isto:

<img src="https://storage.googleapis.com/imgs.medway.com.br/2020/08/4658d20d-screen-shot-2020-08-17-at-17.40.29.png">

Se você vir esta página, seu servidor da web agora está instalado corretamente.

A última coisa que você desejará fazer é habilitar o Apache para iniciar na inicialização. Use o seguinte comando para fazer isso:

<code>sudo systemctl enable httpd.service</code>

### 2 - Instalar o MySQL (MariaDB)

Agora que nosso servidor da web está instalado e funcionando, é hora de instalar o MariaDB, um substituto imediato do MySQL. MariaDB é um fork desenvolvido pela comunidade do sistema de gerenciamento de banco de dados relacional MySQL. Basicamente, ele irá organizar e fornecer acesso a bancos de dados onde nosso site pode armazenar informações.

Novamente, podemos usar yumpara adquirir e instalar nosso software. Desta vez, também instalaremos alguns outros pacotes "auxiliares" que nos ajudarão a fazer com que nossos componentes se comuniquem uns com os outros:

<code>sudo yum install mariadb-server mariadb</code>

Quando a instalação estiver concluída, precisamos iniciar MariaDB com o seguinte comando:

<code>sudo systemctl start mariadb</code>

Agora que nosso banco de dados MySQL está em execução, queremos executar um script de segurança simples que removerá alguns padrões perigosos e bloqueará um pouco o acesso ao nosso sistema de banco de dados. Inicie o script interativo executando:

<code>sudo mysql_secure_installation</code>

O prompt pedirá sua senha root atual. Como você acabou de instalar o MySQL, provavelmente não terá um, então deixe em branco pressionando enter. Em seguida, o prompt perguntará se você deseja definir uma senha de root. Vá em frente e entre Ye siga as instruções:

<code>
  Enter current password for root (enter for none): <br>
  OK, successfully used password, moving on...
</code>
 
<code>
  Setting the root password ensures that nobody can log into the MariaDB <br />
  root user without the proper authorization.
</code>

<code>
  New password: password <br />
  Re-enter new password: password <br />
  Password updated successfully! <br />
  Reloading privilege tables.. <br />
   ... Success!
</code>

 
 Para o resto das perguntas, você deve simplesmente pressionar a tecla “ENTER” em cada prompt para aceitar os valores padrão. Isso removerá alguns usuários e bancos de dados de amostra, desabilitará logins de root remotos e carregará essas novas regras para que o MySQL respeite imediatamente as alterações que fizemos.

A última coisa que você vai querer fazer é habilitar o MariaDB para iniciar na inicialização. Use o seguinte comando para fazer isso:

<code>sudo systemctl enable mariadb.service</code>

Neste ponto, seu sistema de banco de dados está configurado e podemos seguir em frente.

### 3 - Instalar o PHP

PHP é o componente de nossa configuração que processará o código para exibir conteúdo dinâmico. Ele pode executar scripts, conectar-se aos nossos bancos de dados MySQL para obter informações e entregar o conteúdo processado ao nosso servidor web para exibição.

Podemos mais uma vez alavancar o yumsistema para instalar nossos componentes. Vamos incluir o pacote php-mysql também:

<code>sudo yum install php php-mysql</code>

Isso deve instalar o PHP sem problemas. Precisamos reiniciar o servidor web Apache para que ele funcione com PHP. Você pode fazer isso digitando:

<code>sudo systemctl restart httpd.service</code>

### 4 - Abaixe e configurar Wordpress no servidor

<a href="https://br.wordpress.org/download/">Clique aqui</a>

### 5 - Abaixe e instale o template

<a href="http://html5blank.com/">Clique aqui</a>

### 4 - Criar Landpage

<img src="https://storage.googleapis.com/imgs.medway.com.br/2020/08/6351018a-screencapture-cr-medway-br-2020-08-17-14_59_44.jpg">

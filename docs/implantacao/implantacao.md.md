Implanta��o!

Nota O cap�tulo seguinte pode ser �s vezes um pouco dif�cil de passar. Persista e termine-o; Implanta��o � uma parte importante do processo de desenvolvimento de website. Este cap�tulo est� localizado no meio do tutorial para que seu tutor possa lhe ajudar com o processo ligeiramente complexo de colocar seu site online. Isto significa que voc� ainda pode terminar o tutorial por conta pr�pria se voc� continuar em outro momento.

At� agora nosso site s� estava dispon�vel no seu computador, agora voc� vai aprender como publicar ele na internet! A implanta��o � o processo de publica��o do seu aplicativo na Internet de tal forma que as pessoas possam, finalmente, ver seu aplicativo :).

Como voc� aprendeu, um website precisa estar localizado num servidor. Existem muitos provedores, mas iremos utilizar o que tem um processo de deploy relativamente simples: PythonAnywhere. PythonAnywhere � gratuito para aplica��es pequenas que n�o possuem muitos visitantes, ent�o ser� suficiente para voc� por enquanto.

O outro servi�o externo que usaremos � GitHub, que � um servi�o de hospedagem de c�digo. Existem outros, mas quase todos os programadores possuem uma conta no GitHub atualmente e agora voc� tamb�m!

Usaremos o GitHub como um trampolim para transportar nosso c�digo para o PythonAnywhere.

Git

Git � "sistema de controle de vers�o" usado por muitos programadores - um software que controla mudan�as nos arquivos ao longo do tempo para que voc� possa recuperar vers�es espec�ficas depois. Um pouco como "controlar mudan�as" no Microsoft Word, mas muito mais poderoso.

Instalando o Git

Windows

Voc� pode baixar Git em git-scm.com. Voc� pode apertar "next next next" em todos os passos exceto um; no quinto passo chamado "Adjusting your PATH environment", escolha "Run Git and associated Unix tools from the Windows command-line" (a op��o de baixo). Al�m disso, o padr�o est� �timo. Checkout estilo Windows, commit Unix-style linhas de confirma��o est� bom.

MacOS

Baixar Git git-scm.com e siga as instru��es.

Linux

Se ele j� n�o estiver instalado, Git deve estar dispon�vel atrav�s de seu gerenciador de pacotes, ent�o tente:

sudo apt-get install git
# or
sudo yum install git
Come�ando nosso reposit�rio no Git

Git controla as altera��es para um determinado conjunto de arquivos no que chamamos de reposit�rio de c�digo (ou "repo"). Vamos come�ar um para nosso projeto. Abra o console e execute esses comandos, no diret�rio djangogirls:

Nota: Verifique o seu diret�rio de trabalho atual com um pwd (OSX/Linux) ou o comando cd (Windows) antes de inicializar o reposit�rio. Voc� deve estar na pasta djangogirls.

$ git init
Initialized empty Git repository in ~/djangogirls/.git/
$ git config user.name "Your Name"
$ git config user.email you@example.com
Inicializar o reposit�rio git � algo que s� precisamos fazer uma vez por projeto (e voc� n�o ter� que re-introduzir o nome de usu�rio e e-mail nunca mais)

Git ir� controlar as altera��es para todos os arquivos e pastas neste diret�rio, mas existem alguns arquivos que queremos ignorar. Fazemos isso atrav�s da cria��o de um arquivo chamado .gitignore no diret�rio base. Abra seu editor e crie um novo arquivo com o seguinte conte�do:

*.pyc
__pycache__
myvenv
db.sqlite3
static/
.DS_Store
E salve como .gitignore na pasta de n�vel superior "djangogirls".

Nota: O ponto no in�cio do nome do arquivo � importante! Se voc� est� tendo alguma dificuldade em cri�-la (Macs n�o gostam de criar arquivos que come�am com um ponto atrav�s do Finder, por exemplo), use o recurso "Save As" no seu editor que sempre funciona.

� uma boa id�ia para usar um comando de git status antes de git add ou sempre que voc� n�o tiver certeza de que ser� feito, para evitar surpresas (por exemplo, ser�o adicionados arquivos errados ou commitados). O comando git status retorna informa��es sobre todos os arquivos controlado/modificado/encenado, status de ramo e muito mais. O output deve ser semelhante a:

$ git status
On branch master

Initial commit

Untracked files:
  (use "git add <file>..." to include in what will be committed)

.gitignore
blog/
manage.py
mysite/

nothing added to commit but untracked files present (use "git add" to track)
E finalmente n�s salvamos nossas altera��es, V� para o seu console e execute estes comandos:

$ git add --all .
$ git commit -m "My Django Girls app, first commit"
 [...]
 13 files changed, 200 insertions(+)
 create mode 100644 .gitignore
 [...]
 create mode 100644 mysite/wsgi.py
Empurrando o nosso c�digo para GitHub

V� para GitHub.com e cadastre uma nova e gratuita conta de usu�rio. Em seguida, crie um novo reposit�rio, e d� o nome "my-first-blog". Deixe o "initialise with a README" desmarcado, deixe a op��o .gitignore em branco (j� fizemos isso manualmente) e a licen�a como None.



Nota O nome my-first-blog � importante --voc� poderia escolher outra coisa, mas vamos us�-lo muitas vezes nas instru��es abaixo e voc� teria que substitu�-lo cada vez. � provavelmente mais f�cil ficar com o nome my-first-blog.

Na tela seguinte, voc� ser� mostrada a clone URL do seu repo. Escolha a vers�o "HTTPS",copie, e vamos col�-lo no terminal em breve:



Agora precisamos ligar o reposit�rio Git no seu computador com o no GitHub.

$ git remote add origin https://github.com/<your-github-username>/my-first-blog.git
$ git push -u origin master
Digite seu GitHub username e senha, e voc� deve ver algo como isto:

Username for 'https://github.com': hjwp
Password for 'https://hjwp@github.com':
Counting objects: 6, done.
Writing objects: 100% (6/6), 200 bytes | 0 bytes/s, done.
Total 3 (delta 0), reused 0 (delta 0)
To https://github.com/hjwp/my-first-blog.git
 * [new branch]      master -> master
Branch master set up to track remote branch master from origin.
Seu c�digo agora est� no GitHub. V� e confira! Voc� saber� que est� em boa companhia - Django, o Django Girls Tutorial e muitos outros grandes projetos de software de fonte aberta tamb�m hospedam seu c�digo no GitHub :)

Cria��o de nosso blog em PythonAnywhere

Em seguida, � hora de se inscrever para uma conta gratuita de "Beginner" na PythonAnywhere.

www.pythonanywhere.com
Nota: ao escolher seu nome de utilizador aqui, tenha em mente que a URL do seu blog ter� o formul�rio yourusername.pythonanywhere.com, ent�o escolha seu nickname ou o nome do que � o blog.

Pulling our code down on PythonAnywhere

Quando voc� se inscreve para PythonAnywhere, voc� � levado ao seu painel de controle ou p�gina "Consoles". Escolha a op��o iniciar o console "Bash"--que � a vers�o PythonAnywhere de um console, como aquela no seu PC

Nota: PythonAnywhere � baseado em Linux, assim se voc� estiver no Windows o console vai parecer um pouco diferente do que est� no seu computador.

Vamos puxar nosso c�digo de GitHub em PythonAnywhere atrav�s da cria��o de um "clone" do repo. Digite o seguinte para o console na PythonAnywhere:

$ git clone https://github.com/<your-github-username>/my-first-blog.git
Isto puxar� uma c�pia do seu c�digo para PythonAnywhere. Confira digitando:

$ tree my-first-blog
my-first-blog/
+-- blog
�   +-- __init__.py
�   +-- admin.py
�   +-- migrations
�   �   +-- 0001_initial.py
�   �   +-- __init__.py
�   +-- models.py
�   +-- tests.py
�   +-- views.py
+-- manage.py
+-- mysite
    +-- __init__.py
    +-- settings.py
    +-- urls.py
    +-- wsgi.py
Criando um virtualenv na PythonAnywhere

Assim como fez em seu pr�prio computador, voc� pode criar um virtualenv na PythonAnywhere. No console Bash, digite:

20:20 ~ $ cd my-first-blog

20:20 ~ $ virtualenv --python=python3.4 myvenv
Running virtualenv with interpreter /usr/bin/python3.4
[...]
Installing setuptools, pip...done.

20:20 ~ $ source myvenv/bin/activate

(mvenv)20:20 ~ $  pip install django~=1.10.0
Collecting django
[...]
Successfully installed django-1.8.5 whitenoise-2.0
Coleta de arquivos est�ticos.

Voc� estava imaginando o que � "whitenoise"? � uma ferramenta para servir os chamados "arquivos est�ticos". Arquivos est�ticos funcionam de forma diferente nos servidores em compara��o com nosso pr�prio computador, e precisamos de uma ferramenta como o "whitenoise" para atend�-los.

Vamos descobrir um pouco mais sobre arquivos est�ticos mais tarde no tutorial, quando vamos editar o CSS para o nosso site.

Por enquanto s� precisamos executar um comando extra chamado "collectstatic" no servidor. Isso diz pro Django reunir todos os arquivos est�ticos que ele precisa no servidor. Em sua maioria, estes s�o os arquivos est�ticos que fazem o site do admin bonito no momento.

20:20 ~ $ python manage.py collectstatic

You have requested to collect static files at the destination
location as specified in your settings:

    /home/edith/my-first-blog/static

This will overwrite existing files!
Are you sure you want to do this?

Type 'yes' to continue, or 'no' to cancel: yes
Digite "yes" (Sim) e vai embora! Voc� n�o adora fazer computadores imprimir p�ginas e p�ginas de texto? Sempre fa�o pequenos ru�dos para acompanh�-lo. Brp, brp brp...

Copying '/home/edith/.virtualenvs/mvenv/lib/python3.4/site-packages/django/contrib/admin/static/admin/js/actions.min.js'
Copying '/home/edith/.virtualenvs/mvenv/lib/python3.4/site-packages/django/contrib/admin/static/admin/js/inlines.min.js'
[...]
Copying '/home/edith/.virtualenvs/mvenv/lib/python3.4/site-packages/django/contrib/admin/static/admin/css/changelists.css'
Copying '/home/edith/.virtualenvs/mvenv/lib/python3.4/site-packages/django/contrib/admin/static/admin/css/base.css'
62 static files copied to '/home/edith/my-first-blog/static'.
Criando o banco de dados em PythonAnywhere

Aqui est� outra coisa que � diferente entre seu computador e o servidor -- ele usa um banco de dados diferente. Ent�o as contas de usu�rio e mensagens podem ser diferentes no servidor e no seu computador.

Ent�o n�s vamos inicializar o banco de dados no servidor tal como fizemos no seu pr�prio computador, com migrate e createsuperuser:

(mvenv)20:20 ~ $ python manage.py migrate
Operations to perform:
[...]
  Applying sessions.0001_initial... OK


(mvenv)20:20 ~ $ python manage.py createsuperuser
Publica��o do nosso blog como um aplicativo web

Agora nosso c�digo est� na PythonAnywhere, nossa virtualenv est� pronta, os arquivos est�ticos est�o recolhidos e o banco de dados est� inicializado, estamos prontos para public�-lo como um aplicativo da web.

Clique em voltar para o PythonAnywhere dashboard clicando no seu logotipo e clique na guia Web e v� em Add a new web app.

Na caixa de di�logo, ap�s a confirma��o de seu nome de dom�nio, escolha manual configuration (NB n�o a op��o "Django"). Em seguida, escolha Python 3.4 e clique em Next para concluir o assistente.

Nota certifique-se voc� escolheu a op��o "Manual configuration", n�o a "Django". N�s somos demais para o padr�o de configura��o Django da PythonAnywhere ;-)

Definindo o virtualenv

Voc� ser� levado para a tela de configura��o de PythonAnywhere para seu webapp que � onde voc� precisar� de ir quando quiser fazer altera��es para o aplicativo no servidor.



Na se��o "Virtualenv", clique no texto vermelho que diz "Enter the path to a virtualenv" e digite: /home/<your-username>/my-first-blog/myvenv/

Nota: substitua seu pr�prio nome de usu�rio conforme apropriado. Se voc� cometer um erro, PythonAnywhere ir� mostrar um pequeno aviso.

Configurando o arquivo WSGI

Django funciona usando o WSGI protocol, um padr�o para servir sites usando Python, que oferece suporte a PythonAnywhere. A maneira que configuramos PythonAnywhere para reconhecer nosso blog Django � editando um arquivo de configura��o do WSGI.

Clique no link "WSGI configuration file" (na se��o "Code" perto do topo da p�gina - -ele vai ser nomeado algo como /var/www/<your-username>_pythonanywhere_com_wsgi.py), e voc� ser� levado para um editor.

Exclua todo o conte�do atual e substitua com algo parecido com isto:

import os
import sys

path = '/home/<your-username>/my-first-blog'  # use your own username here
if path not in sys.path:
    sys.path.append(path)

os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'

from django.core.wsgi import get_wsgi_application
from whitenoise.django import DjangoWhiteNoise
application = DjangoWhiteNoise(get_wsgi_application())
Nota n�o se esque�a de substituir em seu pr�prio nome de usu�rio onde diz <your-username>

O que esse arquivo faz � dizer PythonAnywhere onde mora a nossa aplica��o web e qual o nome do arquivo de configura��es Django. Ele tamb�m define a ferramenta de arquivos est�ticos "whitenoise".

Aperte Save e ent�o volte para a guia Web.

J� terminamos! Aperte o bot�o grande verde de Reloade voc� ser� capaz de ir ver os seu aplicativo. Voc� encontrar� um link para ele no topo da p�gina.

Dicas de debugging

Se voc� vir um erro quando voc� tenta visitar o seu site, o primeiro lugar para procurar alguma informa��o de debugging � no seu error log -- voc� encontrar� um link para isso na guia web PythonAnywhere. Ver se h� mensagens de erro l�. As mais recentes est�o na parte inferior. Problemas comuns incluem

esquecer um dos passos que fizemos no console: criando o virtualenv, ativ�-lo, instalando o Django, collectstatic, inicializando o banco de dados
cometer um erro no caminho do virtualenv na guia web -- haver� geralmente uma pequena mensagem de erro vermelho l�, se h� um problema
cometer um erro no arquivo de configura��o WSGI..--voc� usou o caminho para a pasta do my-first-blog certinho?
O treinador est� aqui para ajudar!

Voc� est� live!

A p�gina padr�o para seu site deve dizer "Bem-vindo ao Django", como acontece no seu PC local. Tente adicionar /admin/ para o final da URL, e voc� ser� levado ao site admin. Fazer login com o nome de usu�rio e senha, e voc� ver� que voc� pode adicionar novas mensagens no servidor.

D� em voc� mesma um enorme tapinha nas costas - implanta��es de servidor s�o uma das partes mais dif�ceis do desenvolvimento web, e muitas vezes leva as pessoas v�rios dias antes de fazer funcionar. Mas voc� tem seu site publicado, na internet, assim!
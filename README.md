# Tutorial Django 02 – Criando Uma Simples Aplicação Web (Hello World)

Neste tutorial, você aprenderá a criar uma aplicação básica usando o Framework Django. Ou seja, ela irá imprimir na sua página da web “**Hello World**”. Para isto, siga os passos abaixo.

**Observação Importante: faça isso somente depois de fazer o Tutorial 01, que trata da instalação do Python e Visual Studio Code.**

## **Passo 1: Configure seu ambiente de desenvolvimento**

Sempre que você estiver iniciando um projeto de desenvolvimento web, é uma boa ideia configurá-lo primeiro.

1.1) Abra o Terminal no VS Code. Primeiro digite (CTRL+Shift+P) e use a opção “**View: Toggle Terminal**” ou “**Ver: Alternar Terminal**”.

1.2) Digite na linha de comando do Terminal:

```
cd Django_Tutoriais
mkdir Tutorial_02
cd Tutorial_02
```

1.3) Uma vez dentro do diretório (“**Tutorial_02**”), é uma boa ideia criar um ambiente virtual. Cada ambiente tem seu próprio conjunto de pacotes Python instalado. Outra vantagem disso é que permite utilizar versões diferentes de pacotes em projetos distintos. Existem muitas maneiras diferentes de configurar ambientes virtuais, mas aqui você vai usar o “**venv**”. Para criar um ambiente isolado, digite o comando a seguir:

```
python3 -m venv virtenv
```

Caso esteja usando o **Windows**:

```
py -m venv virtenv
```

1.4) Agora você precisa ativar o ambiente virtual criado no item anterior, executando o comando abaixo:

**Linux/Mac**

```
source virtenv/bin/activate
```

**Windows**

```
.\virtenv\Scripts\activate.bat
```

Ou

```
.\virtenv\Scripts\Activate.ps1
```

Você saberá que seu ambiente virtual foi ativado, porque o _prompt_ do console no Terminal mudará. Deve ser assim:

```
(virtenv) $
```

1.5) Agora que você criou um ambiente virtual, é hora de instalar o **Django**. Digite na linha de comando:

```
(virtenv) $ pip install django
```

##**Passo 2: Criando seu projeto em Django**

2.1) Certifique-se de que você está dentro do diretório “**Tutorial_02**” e o ambiente virtual ativado. Agora, digite o comando abaixo para criar um projeto.

```
(virtenv) $ django-admin startproject website .
```

**Observação: ao criar um novo projeto Django chamado “website” certifique-se de incluir o ponto (.) no final do comando para que ele seja instalado no diretório atual.**

O comando acima irá criar uma pasta chamada “**website**” contendo alguns arquivos. No painel esquerdo do **VS Code**, você verá uma estrutura de diretório que se parece com a figura abaixo.

![pasta website](../img_readme/pasta_website.png)

Explicando cada arquivo da pasta “**website**”:

**website/__init__.py**

_Arquivo que diz ao Python quais pacotes usar para este projeto. Ele começa vazio._

**website/asgi.py**

_Arquivo que representa um ponto de integração para servidores web compatíveis com ASGI (_**_Asynchronous Server Gateway Interface_**_) usado para servir seu projeto. Ele serve para fazer o “deploy” da sua aplicação._

**website/settings.py**

_É um arquivo_ **_muito_** **_importante_** _porque contém as configurações do projeto, tais como configurações do Banco de Dados, aplicativos instalados, configuração de arquivos estáticos e muito mais._

**website/urls.py**

_Aqui vamos dizer ao Django_ **_quem_** _responde a_ **_qual_** _URL. Também chamado de_  `URLConf`.

**website/wsgi.py**

_Aqui configuramos a interface entre o servidor de aplicação e nossa aplicação Django (WSGI - Web Server Gateway Interface). Também serve para fazer o “deploy” da aplicação._

E por último, temos o arquivo abaixo que está na pasta “**Django_Tutoriais**”:

**manage.py**

_Arquivo gerado automaticamente pelo Django que expõe comandos importantes para manutenção da nossa aplicação. Ele permite a você interagir com esse projeto Django de várias maneiras._

## **Passo 3: Testando seu servidor Django**

3.1) Depois que sua estrutura de arquivos estiver configurada, você pode iniciar o servidor de desenvolvimento que já vem embutido no Django. Para verificar se a configuração foi bem-sucedida, execute o seguinte comando no console do Terminal:

```
python manage.py runserver
```

3.2) Observe no console do Terminal as mensagens da figura abaixo:

![console terminal](../img_readme/console_terminal.png)

Ignore os avisos sobre migrações não aplicadas por enquanto. Isto porque não estamos usando um Banco de Dados neste tutorial.

Ao posicionar o mouse no link “**http://127.0.0.1:8000/**” você verá a seguinte mensagem:

![acesso localhost](../img_readme/acesso_localhost.png)

No **Windows** irá aparecer “**Seguir o link (ctrl + click)**”. Ao efetuar esta operação, você será direcionado para uma aba do seu browser, e, se tudo estiver correto, você verá uma página da web como a da figura abaixo.

![tela django](../img_readme/tela_django.png)

3.3) Parabéns, você acabou de criar um projeto, nossa configuração está correta e você o testou no servidor de desenvolvimento. Agora o Django está pronto para começarmos a desenvolver.

## **Passo 4: Criando uma aplicação em Django**

**Projetos vs Apps**

Em Django, um projeto pode ter uma ou várias aplicações, que são chamadas de “apps”. Cada uma dessas “apps” possui sua própria arquitetura, seus arquivos de *models*, de *views* e de *templates*. Isto significa que, as ‘apps’ podem representar aplicações isoladas, porém em um mesmo projeto.

Como exemplo, pense que você está criando uma aplicação para um blog. Ele pode possuir, uma aplicação de administração (para cadastrar os posts) e uma página da web que faz a leitura desses posts. Estas duas aplicações (“apps”) podem estar dentro de um mesmo projeto, porém de forma isoladas.

De acordo com a documentação do Django, uma “**app**” é:

> “Uma aplicação Web que faz alguma coisa, por exemplo - um blog, um Banco de Dados de registros públicos ou um aplicativo de pesquisa. Já um projeto é uma coleção de configurações e “apps” para um website em particular.”

Para esta parte do tutorial, criaremos uma “**app**” chamado “**hello_world**”.

4.1) Para criar uma “**app**”, execute o seguinte comando:

```
python manage.py startapp hello_world
```

Este comando irá criar um diretório chamado “**hello_word**” com vários arquivos. Veja a estrutura na figura abaixo.

![pasta hello_world](../img_readme/pasta_hello_world.png)


Explicando alguns arquivos que estão dentro da pasta “**hello_world**”:

**__init__.py**

*Diz ao Python para tratar o diretório como um pacote.*

**admin.py**

*Contém configurações para as páginas de administração do Django.*

**apps.py**

*Contém ajustes para configuração do aplicativo.*

**models.py**

*Contém uma série de classes que o Django usa para converter tabelas de Banco de Dados. Na verdade, um dos recursos mais poderosos do Django é seu “Mapeador Objeto-Relacional” (Object-Relational Mapper - ORM), o qual permite que você interaja com seu Banco de Dados (BD), como faria usando SQL. Em outras palavras, ele é apenas uma forma “_pythonica_” de criar SQL para consultar e manipular seu BD e obter resultados de uma forma também “_pythonica_”. Esta “forma ou maneira” nada mais é do que uma engenharia muito inteligente que aproveita algumas das partes mais complexas do Python para tornar a vida dos desenvolvedores mais fácil.*

**tests.py**

*Contém classes de teste.*

**views.py**

*Contém classes e métodos que controlam quais dados serão exibidos nos templates HTML.*

4.2) Agora que você criou a “app”, temos que “instalá-la” no seu projeto. Abra o arquivo (“**website/settings.py**”) e adicione a seguinte linha de código destacada em INSTALLED_APPS: (**Não se esqueça de colocar a vírgula após a _string_**).

![fig installed_apps](../img_readme/installed_apps.png)

Essa linha de código indica que seu projeto agora sabe que o aplicativo que você acabou de criar existe.

Surge uma pergunta: de onde obtivemos a referência a “**hello_world**”?

Resposta: quando criamos uma nova “app”, no **Passo 4.1**, o Django gerou um arquivo chamado “**apps.py**” na pasta “**hello_world**”. E dentro desse arquivo, ele criou uma classe chamada `HelloWorldConfig`. Essa classe nos permite fazer referência ao aplicativo (i.e. ao “**app**”) para o projeto. O conteúdo do arquivo “**hello_world/apps.py**” está abaixo.

```python
from django.apps import AppConfig
class HelloWorldConfig(AppConfig):
	default_auto_field = 'django.db.models.BigAutoField'
	name = 'hello_world'
```

A próxima etapa é criar uma ”**View**“ para que você possa exibir algo para o usuário.

**Passo 5: Criando uma View**

Suponha que você esteja criando uma “**app**” chamada “**hello_world**” sem um framework. Para isto, basta digitar “**Hello World**” em um arquivo de texto, e salvá-lo como “**hello.html**” e fazer o “_upload_” dele em um diretório de um servidor da web em algum lugar.

Observe que neste processo que você especificou duas informações importantes sobre a página da web:

1.  seu conteúdo (a string “**Hello World**”)
2.  seu URL (por exemplo, http://www.example.com/hello.html)

Com o Django, você também faz essas duas coisas, porém de uma maneira diferente. A função da “**View**” é produzir o conteúdo da página que está no arquivo “**views.py**” e o URL é especificada no arquivo “**urls.py**”.

As Views no Django são uma coleção de métodos ou classes dentro do arquivo “views.py” no diretório do seu aplicativo. Cada método ou classe trata com a lógica que é processada cada vez que uma URL diferente é visitada.

5.1) Abra o arquivo “**views.py**” no diretório (“**hello_world/views.py**”). Já existe uma linha de código lá que importa o método “**render()**”.

```python
from django.shortcuts import render
```

Agora adicione o seguinte código a este arquivo (em destaque):

```python
from django.http import HttpResponse
def index(request):
	return HttpResponse("<h1>Hello World!</h1>")
```

Primeiro, importamos a classe `HttpResponse` do módulo `django.http`. Em seguida, criamos uma função que recebe uma solicitação (*request*) como parâmetro e retorna um objeto HttpResponse, ou seja, a string `<h1>Hello World!</h1>`. Observe que cada função de uma “View” deve ter pelo menos um parâmetro por convenção chamado solicitação (i.e. *request*).

5.2) Para ver essa “**View**” em nosso navegador, precisamos mapeá-la em nossas configurações de URL. Para isto, abra o arquivo “**website/urls.py**”. O seu conteúdo deve ser assim.

```python
from django.contrib import admin
from django.urls import path

urlpatterns = [
	path('admin/', admin.site.urls),
]
```

Agora precisamos dizer ao Django explicitamente que precisamos ativar uma “**View**” para uma URL específica. Altere o conteúdo do arquivo acima para:

```python
from django.contrib import admin
from django.urls import path

# views importadas
from hello_world import views

urlpatterns = [
	path('admin/', admin.site.urls),
	# URL configurada
	path('', views.index, name="homepage")
]
```

Observe a linha com o comando `from hello_world import views`. Ela diz ao Django para importar o arquivo “**views.py**” da pasta “**hello_world**”. Em outras palavras, importamos as “**Views**” do diretório “**hello_world**”.

Em seguida, na lista “**urlpatterns**”, adicionamos o caminho (rota) para a “view” que é a nossa página inicial (homepage). Com a _string_ em branco denotada por “ “, mapeamos este URL para nossa função “index” que está no arquivo “views.py”. E, por último, o nome do argumento opcional que atribuímos como “homepage”. Isso significa que cada solicitação para a página inicial deve retornar a _string_ `<h1>Hello World!</h1>`.

5.3) Agora, ao reiniciar o servidor no Terminal (`python manage.py runserver`), visite “**http://127.0.0.1:8000**”. Você deverá a seguinte página da web:

![first web app](../img_readme/first_web_app.png)

5.4) Parabéns. Você criou sua primeira aplicação web em Django.
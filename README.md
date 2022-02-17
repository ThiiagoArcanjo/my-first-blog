# my-first-blog 

### Diretório criado para aprendizagem seguindo o tutorial das DjangoGirls: 
https://tutorial.djangogirls.org/pt/

# Resumão

1 →   Criar uma pasta para o projeto.

2 →  Criar um ambiente virtual na pasta criada para projeto → python3 -m venv myvenv

3 →  Iniciar o ambiente virtual → source myvenv/bin/activate. O comando deve ser dado dentro da pasta do projeto.

4 → Verificar se a ultima versão do pip esta instalada → python -m pip install --upgrade pip

5 → Instalar Django no Linux: Na pasta do projeto criar um arquivo de texto chamado requirements.txt e dentro do arquivo colocar Django~=3.2.10 (versão do django) salvar e depois executar o seguinte comando   pip install -r requirements.txt

6 → Criar o projeto na pasta → django-admin startproject mysite .   PS: Não se esqueça do ponto final.

7 → Fazer mudanças no arquivo settings.py: 
	
    7.1 →  Mudar região → TIME_ZONE = 'America/Sao_Paulo'  
	7.2 → Mudar linguagem → LANGUAGE_CODE = 'pt-BR'
	7.3 → Adicionar o caminho dos arquivos estáticos → STATIC_URL = '/static/'   STATIC_ROOT = os.path.join(BASE_DIR, 'static')
	7.4 → adicionar possível domínio online ALLOWED_HOSTS = ['127.0.0.1', '.pythonanywhere.com']

8 → Configurar base de dados → Já configurada, porém para criar o banco de dados são necessários os seguintes comandos: python manage.py migrate ^^” Gera um arquivo db.sqlite3 no seu projeto.

9 → Iniciar o servidor web → (Na pasta do projeto) → python manage.py runserver

10 → Criar a aplicação → python manage.py startapp blog Ps: Com o ambiente virtual ativado.

11 → Dizer ao Django que ele deve usar a aplicação que criamos: mysite/setting.py/  na seção instaleds apps adicione → 'blog',

12 → Criar o modelo na models.py

13 →  Criar o arquivo de construção das tabelas → python manage.py makemigrations blog

	13.1 → Aplicar o arquivo criado → python manage.py migrate blog

14 → Importar post em admin from .models import Post e adicionar post ao admin admin.site.register(Post)

15 → Criar usuário e senha para o Django admin → python manage.py createsuperuser (Com ambiente virtual ativo) PS: Caso precise mudar a senha → python manage.py changepassword nomedousuarioquedesejamxer

16 → Deploy → Instalar git → sudo apt install git, iniciar o diretório com git, configurar git ignore,  git status, git add –all . para adicionar tudo(não esquecer o ponto), git commit -m “”, git branch -m “main” para mudar a branch principal, criar origem do diretório no gitHub e adicionar a mesma no git(git remote add origin) e git push -u origin main para colocar no github.
	
    16.1 → PythonAnyWhere → Criar uma conta gratuita -> beginner(iniciante). Ir na opção conta, escolher api token e depois criar um new api token. Ir na dashboard e new console bash. Instalar o pythonanywhere -> $ pip3.6 install --user pythonanywhere. Configurar a aplicação a partir do github -> pa_autoconfigure_django.py https://github.com/<your-github-username>/my-first-blog.git . Criar novo banco de dados para o usuário online -> python manage.py createsuperuser.  Podemos visualizar as pastas com ls ou acessar o nosso blog.

17 →  URL’s → Adicionar URL do blog, adicionando include e a URL →path('', include('blog.urls')),

18 → Criar um novo arquivo de urls em blog/urls.py, importar o path e views e adicionar a URL → path('', views.lista_post, name='lista_post'),

19 → No arquivo views.py  criar a  view post_list e passar o templete a ser mostrado.

20 → Personalizar um pouco o template

21 → QuerySets → python manage.py shell 

22 → Adicionar modelo post na view, adicionar timezone a view,  criar uma lista de posts a partir da data de publicação;

23 → Listar post por publicação no template principal

24 → Personalizar o template com css e bootstrap

25 → Criar pasta de arquivos static/css/blog.css

26 → Carregar arquivos estáticos na página da lista {% load static %} e adicionando link real <link rel="stylesheet" href="{% static 'css/blog.css' %}">

27 → Adicionar fonts em post_list → <link href="//fonts.googleapis.com/css?family=Lobster&subset=latin,latin-ext" rel="stylesheet" type="text/css">

28 → Estilizar tabelas e CSS.

29 → Criar arquivo base html para ser reaproveitado em todas as páginas, colocando →  {% block content %} {% endblock %}  no local onde será inserido o conteúdo da outra página.

30 → Adicionar a página  no modelo base:
	
    30.1 → Extende-se o modelo {% extends 'blog/base.html' %} Primeira linha do arquivo 
	30.2 → Colocar oque é para ser exibido no modelo base entre {% block content %} e {% endblock %}

31 → Adionar o post_details com link no post_list → <a href="{% url 'post_detalhes' pk=post.pk %}">

	31.1 →  Criar url para o link(em blog/urls.py)→ path('post/<int:pk>/', views.post_detail, name='post_detail'),
	31.2 → Adicionar view post_detail
	31.3 → Adicionar  Arquivo post_detail.html


32 → Deploy da aplicação → Ps para carregar css e outros arquivos estáticos no servidor é preciso usar esse comando → python manage.py collectstatic

33 → Adicionar um formulário em blog/forms.py, importando form e modelo post, criando a classe PostForm, passando um modelo de formulário, criando class meta e passando os campos do modelo que serão mostrados.
34 → Adicionar link no HTML base.
35 → Adicionar URL → path('post/new/', views.post_new, name='post_new'),
36 → Criar view, importanto PostForm, instanciando na view e passando para o template.
37 → Criar template post edit usando → {% csrf_token %} e {{ form.as_p }} 
38 → Adicionar lógica para inserção do post na view
39 → Adicionar link para edição de posts, adicionando url, adicionando view post_edit e reaproveitando post_edit
40 → Adicionar área restrita
41 →  Adicionar exclusão de post
42 → Fazer o ultimo deploy do projeto
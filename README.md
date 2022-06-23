# Flask-Hello-World
Aplicação Flask

1. Instalando Python 3 e venv

python3 -V

A partir do Python 3.6, a maneira recomendada de criar um ambiente virtual é usar o módulo venv . Para instalar o pacote python3-venv que fornece o módulo venv , execute o seguinte comando:

sudo apt install python3-venv

Após a instalação do módulo, crie um ambiente virtual para nosso aplicativo Flask.

2. Criando um ambiente virtual

Comece navegando para o diretório em que você gostaria de armazenar seus ambientes virtuais Python 3. Pode ser seu diretório pessoal ou qualquer outro diretório em que o usuário tenha permissões de leitura e gravação.

Crie um novo diretório para o seu aplicativo Flask e navegue até ele:

mkdir my_flask_app
cd my_flask_app

python3 -m venv venv

O comando acima cria um diretório chamado venv , que contém uma cópia do binário Python, o gerenciador de pacotes Pip, a biblioteca Python padrão e outros arquivos de suporte. Você pode usar qualquer nome que desejar para o ambiente virtual.

Para começar a usar esse ambiente virtual, é necessário ativá-lo executando o script de activate :

source venv/bin/activate

Uma vez ativado, o diretório bin do ambiente virtual será adicionado no início da variável $PATH . O prompt do seu shell também será alterado e mostrará o nome do ambiente virtual que você está usando no momento. No nosso caso, isso é venv :

3. Instalando o Flask

Agora que o ambiente virtual está ativado, você pode usar o gerenciador de pacotes Python pip para instalar o Flask:

pip install Flask No ambiente virtual, você pode usar o comando pip vez de pip3 e python vez de python3 .

Verifique a instalação com o seguinte comando, que imprimirá a versão do Flask:

python -m flask --version

4. Criando um aplicativo

Neste guia, criaremos um aplicativo simples Hello World que exibirá apenas o texto "Hello World!".

Primeiro fiz a instalação do Pycharm

sudo snap install [pycharm-professional|pycharm-community] --classic


Logo após a instalação crie um arquivo python:

hello.py


Vamos analisar o código linha por linha.
 
from flask import Flask

app = Flask(__name__)


@app.route("/")
def index():
    return ('Hello World!')


if __name__ == "__main__":
    app.run()


Na primeira linha, estamos importando a classe Flask. Em seguida, criamos uma instância da classe Flask. Em seguida, usamos o decorador route() para registrar a função hello_world na rota / . Quando essa rota é solicitada, hello_world é chamado e a mensagem "Hello World!" É retornada ao cliente.

Salve o arquivo como hello.py e volte para a janela do seu terminal.

5. Testando o servidor de desenvolvimento

Usaremos o comando flask para executar o aplicativo, mas antes disso, precisamos informar ao Flask como carregar o aplicativo, especificando a variável de ambiente FLASK_APP :

export FLASK_APP=hello
flask run

O comando acima iniciará o servidor interno de desenvolvimento.

A saída será semelhante à seguinte:

* Serving Flask app "hello" * Environment: production WARNING: Do not use the development server in a production environment. Use a production WSGI server instead. * Debug mode: off * Running on http://127.0.0.1:5000/ (Press CTRL+C to quit) Se você instalou o Flask em uma máquina virtual e deseja acessar o servidor de desenvolvimento do Flask, poderá disponibilizá-lo publicamente anexando --host=0.0.0.0 ao comando flask run.

Abra http://127.0.0.1:5000 no seu navegador da web e você receberá a mensagem "Hello World!"

Depois de concluir seu trabalho, desative o ambiente digitando deactivate e você retornará ao seu shell normal.

deactivate

Para executar esse processo na porta 80,faça a modificação no app.run()

Exemplo a baixo:

from flask import Flask

app = Flask(__name__)


@app.route("/")
def index():
    return ('Hello World!')


if __name__ == "__main__":
    app.run(debug=True, port=8080)








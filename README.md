# Sistema de Delivery Local - Banco de Dados
Turma: 4º Período de Sistemas de Informação
Equipe: Marcus Vinicius, Ricardo Henrique, Ytalo Emanuel, Ronaldo Lima

## Minha parte: Integração do MySQL através do VS Code
Responsável: Marcus Vinicius de Sousa Reis

### O que eu fiz
Fiz a integração do banco de dados MySQL com o Python, usando o VS Code.
O banco db_delivery_local foi criado pelo colega no arquivo db_delivery_01.sql.
Eu fiz a parte de conectar esse banco no Python e testar a integração.

## Passo a passo completo - Comandos da Integração

### 1. Criar o banco no MySQL Workbench
No MySQL Workbench: File > Open SQL Script > Abrir db_delivery_01.sql > Clicar no raio para rodar. Isso cria o banco db_delivery_local.

### 2. Abrir o projeto no VS Code
cd "C:\Users\vinic\Documents\projetos-backend"
code .

### 3. Instalar dependências
pip install flask
pip install mysql-connector-python
pip install -r requirements.txt

Conteúdo do requirements.txt:
flask
mysql-connector-python

### 4. Configuração da conexão no app_integracao.py
def conectar():
    return mysql.connector.connect(host='localhost', user='root', password='Sh@zam123', database='db_delivery_local')

### 5. Rodar a integração no terminal do VS Code
python app_integracao.py
Tem que aparecer: Running on http://127.0.0.1:5000

### 6. Testar no navegador
http://127.0.0.1:5000/
http://127.0.0.1:5000/pedidos
http://127.0.0.1:5000/produtos
http://127.0.0.1:5000/pedidos/cliente/1
http://127.0.0.1:5000/pedidos/1/total
http://127.0.0.1:5000/historico
http://127.0.0.1:5000/relatorio/mais-vendidos
obs: só poderá rodas os links se fizer a ativação no vscode com o comando ( python app_integracao.py )
Resultado: {"status": "Integracao OK", "msg": "Python conectado no db_delivery_local!"}

### 7. Testar PUT e POST (Trigger e Transação)
curl -X PUT http://127.0.0.1:5000/pedidos/1/status -H "Content-Type: application/json" -d "{\"status\": \"Entregue\"}"
curl -X POST http://127.0.0.1:5000/pedidos -H "Content-Type: application/json" -d "{\"id_cliente\": 1, \"id_restaurante\": 1, \"itens\": [{\"id_produto\": 1, \"quantidade\": 2}]}"

### 8. Parar o servidor
No terminal do VS Code: Ctrl + C


## Arquivos da minha parte
integracao-backend-python/app_integracao.py
integracao-backend-python/requirements.txt
integracao-backend-python/README.md

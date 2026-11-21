# Sistema de Delivery Local - Banco de Dados
Turma: 4º Período de Sistemas de Informação
Equipe: Marcus Vinicius, Ricardo Henrique, Ytalo Emanuel, Ronaldo Lima

### Passo a passo completo - Comandos da Integração

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

IMPORTANTE: Deixa o terminal aberto rodando. Se fechar o VS Code, o site cai e aparece ERR_CONNECTION_REFUSED.

## Como entrar nos links - LEIA ISSO ANTES DE TESTAR

Os links só funcionam se o servidor estiver rodando. Não adianta abrir o link com o VS Code fechado.

Passo 1: Abre o VS Code e abre o terminal (Ctrl + aspas)
Passo 2: Roda: python app_integracao.py
Passo 3: Espera aparecer: Running on http://127.0.0.1:5000
Passo 4: DEIXA O TERMINAL ABERTO. Não fecha o VS Code.
Passo 5: Agora sim abre o Chrome e cola o link.
Passo 6: Se aparecer ERR_CONNECTION_REFUSED ou "Não é possível aceder a este site", é porque o servidor parou. Volta no VS Code, roda python app_integracao.py de novo e aperta F5 no navegador.
Passo 7: Para parar o servidor no final, aperta Ctrl + C no terminal do VS Code.

### Links para testar (com o servidor rodando)
http://127.0.0.1:5000/
http://127.0.0.1:5000/pedidos
http://127.0.0.1:5000/produtos
http://127.0.0.1:5000/pedidos/cliente/1
http://127.0.0.1:5000/pedidos/1/total
http://127.0.0.1:5000/historico
http://127.0.0.1:5000/relatorio/mais-vendidos

Resultado do teste principal: {"status": "Integracao OK", "msg": "Python conectado no db_delivery_local!"}

### Testar PUT e POST (Trigger e Transação)
curl -X PUT http://127.0.0.1:5000/pedidos/1/status -H "Content-Type: application/json" -d "{\"status\": \"Entregue\"}"
curl -X POST http://127.0.0.1:5000/pedidos -H "Content-Type: application/json" -d "{\"id_cliente\": 1, \"id_restaurante\": 1, \"itens\": [{\"id_produto\": 1, \"quantidade\": 2}]}"

## O que a integração usa do banco do colega
VIEW vw_pedidos_completos - Rota /pedidos
VIEW vw_produtos_restaurantes - Rota /produtos
PROCEDURE consultar_pedidos_cliente - Rota /pedidos/cliente/1
FUNCTION calcular_total_pedido - Rota /pedidos/1/total
TRIGGER trg_historico_pedidos - Rota PUT /pedidos/1/status
Transação com COMMIT / ROLLBACK - Rota POST /pedidos
JOIN produtos mais vendidos - Rota /relatorio/mais-vendidos

## Arquivos da minha parte
integracao-backend-python/app_integracao.py
integracao-backend-python/requirements.txt
integracao-backend-python/README.md

# Sistema de Delivery Local - Banco de Dados
Turma: 4º Período de Sistemas de Informação
Equipe: Marcus Vinicius, Ricardo Henrique, Ytalo Emanuel e Ronaldo Lima

## Item 1 ao 5 - Criação da DB, povoamento, PK/FK, JOIN, script comentado e PDF

Banco: `db_delivery_local`
Arquivo base: `db_delivery_01.sql`

### O que o banco tem
- Tabelas: Clientes, Restaurantes, Produtos, Pedidos, Itens_Pedido, Entregadores, Historico_Pedidos
- PK e FK em todas as tabelas
- Views: vw_pedidos_completos, vw_produtos_restaurantes
- Procedure: consultar_pedidos_cliente
- Function: calcular_total_pedido
- Trigger: trg_historico_pedidos
- Transações com COMMIT / ROLLBACK
- Consultas avançadas com JOIN

---

## Integração Backend Python - Marcus Vinicius

Pasta: `integracao-backend-python/`

### Como rodar
```bash
pip install -r requirements.txt
python app_integracao.py

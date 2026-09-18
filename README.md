# 📦 Automação de Controle de Qualidade Pós-Venda | n8n

Fluxo de automação desenvolvido no **n8n** para monitorar e coletar feedbacks sobre a qualidade dos produtos vendidos pela loja, garantindo um acompanhamento pós-venda eficiente e orientado a dados.

---

## 🎯 Objetivo

Registrar os dados de compras realizadas e automatizar o envio de pesquisas de satisfação e qualidade aos clientes, centralizando as respostas coletadas para análise contínua da equipe.

* **Responsável / Área Beneficiada:** Equipe de Qualidade de Vendas

---

## 🛠️ Tecnologias & Ferramentas

* **[n8n](https://n8n.io/):** Orquestração e fluxo de automação.
* **[Supabase](https://supabase.com/):** Banco de dados relacional (PostgreSQL) para armazenamento de pedidos e respostas.
* **[Gmail](https://workspace.google.com/products/gmail/):** Disparo e recebimento de e-mails transacionais e de confirmação.

---

## 🔄 Fluxo de Trabalho (Workflow)

```mermaid
graph TD
    A[Venda realizada na loja] --> B[(Salvar dados no Supabase)]
    B --> C{Aguardar 14 dias}
    C --> D[Verificar regras & disparar pesquisa via Gmail]
    D --> E[Cliente responde formulário]
    E --> F[(Salvar feedback no Supabase)]
    F --> G[Enviar e-mail de confirmação ao cliente]
## 📌 Regras Importantes

### 🚫 Restrições
* **E-mails Inválidos:** Ignorar registros sem e-mail cadastrado ou com formato inválido.
* **Opt-out / Anti-spam:** Ignorar clientes que optaram por não receber e-mails/comunicações da loja.

### ✅ Validações
* **Validação de Contato:** Validar a integridade do e-mail antes de realizar o disparo.
* **Status de Pós-Venda:** Validar se o cliente não solicitou troca ou devolução do produto adquirido.
* **Confirmação de Persistência:** Validar se o banco de dados recebeu e salvou as informações corretamente antes de disparar o e-mail de confirmação.

### ⚠️ Exceções
* **Itens Não Avaliáveis:** Não enviar perguntas sobre produtos entregues como brinde ou amostras grátis.

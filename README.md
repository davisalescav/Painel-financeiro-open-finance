# 💰 Painel Financeiro Automático com Open Finance (n8n + Pluggy)

Workflow em **n8n** que busca todo dia o extrato bancário pela API da **Pluggy (Open Finance)** e monta automaticamente um **painel financeiro no Google Sheets**, com transações organizadas, layout e formatação prontos.

## ✨ O que ele faz

- ⏰ Roda **todo dia às 7h**
- 🔐 Autentica na API da Pluggy
- 🏦 Busca as contas conectadas e as transações dos últimos dias
- 🧹 Organiza cada transação em colunas: data, descrição, valor, categoria, tipo (Entrada/Saída) e conta
- 📄 **Cria a planilha sozinho** no Google Drive se ela ainda não existir
- 🎨 Monta o layout do painel e aplica a formatação (cores, cabeçalhos, formatos de moeda e data)

## 🔄 Fluxo

```
Todo dia às 7h → Configurações → Procurar planilha → (Criar planilha, se não existir)
   → Autenticar na Pluggy → Buscar contas → Buscar transações
   → Organizar colunas → Salvar na planilha → Montar layout → Estilizar planilha
```

## 📊 Colunas da aba "Transações"

| id | data | descricao | valor | categoria | tipo | conta |
|---|---|---|---|---|---|---|

## 🚀 Como usar

1. Crie uma conta na [Pluggy](https://pluggy.ai) e conecte seu banco (o **Meu Pluggy** é gratuito para uso pessoal).
2. Importe `workflow/painel-financeiro.json` no n8n (menu **⋯ → Import from file**).
3. Crie as credenciais:
   - **Google Sheets OAuth2**: nos nós de planilha e de requisição ao Google
   - **Custom Auth** com o `clientId` e o `clientSecret` da Pluggy: no nó *Autenticar na Pluggy*
4. No nó **Configurações**, troque `SEU_ITEM_ID_PLUGGY` pelo Item ID da sua conexão e ajuste o nome da planilha e do banco.
5. Execute uma vez manualmente e depois ative o workflow.

## 🔒 Segurança

Nenhuma chave fica no JSON: `clientId` e `clientSecret` ficam apenas nas credenciais do n8n. Não faça commit de credenciais.

## 🛠️ Tecnologias

n8n · Pluggy API (Open Finance) · Google Sheets API · Google Drive API · JavaScript

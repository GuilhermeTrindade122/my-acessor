# Assessor.AI

**Um assistente conversacional para finanças, agenda e dúvidas sobre a aplicação.**

Projeto em Python que combina modelos Gemini, ferramentas de acesso ao PostgreSQL e recuperação de informações de um FAQ em PDF. Um roteador identifica o assunto da conversa e encaminha a solicitação ao fluxo correspondente.

## Como funciona

1. O usuário envia uma mensagem pelo terminal.
2. O roteador identifica a intenção: finanças, agenda ou FAQ.
3. O fluxo selecionado consulta ferramentas ou o documento de referência.
4. A resposta retorna ao usuário com histórico de conversa em memória.

## Componentes

- [`main.py`](main.py) — roteamento, prompts, agentes especialistas e interface de terminal.
- [`pg_tools.py`](pg_tools.py) — ferramentas para consultar e registrar dados no PostgreSQL.
- [`faq_tool.py`](faq_tool.py) — carregamento do FAQ, embeddings e busca com FAISS.
- [`FAQ_assessor_v1.1.pdf`](FAQ_assessor_v1.1.pdf) — documento de referência do fluxo de perguntas frequentes.

## Stack

Python · LangChain · Gemini · PostgreSQL · FAISS · python-dotenv

## Preparação do ambiente

O projeto depende de uma chave Gemini, de uma instância PostgreSQL com as tabelas esperadas pelas ferramentas e de bibliotecas compatíveis com as APIs de LangChain utilizadas no código.

As variáveis são lidas de um arquivo `.env`: `GEMINI_API_KEY` e os parâmetros de conexão `host`, `database`, `user`, `password` e `port`.

O arquivo [`requirements.txt`](requirements.txt) contém a base de dependências. Os imports também exigem componentes como `langchain-community`, `psycopg2`, um leitor PDF e FAISS. O repositório ainda não inclui um script de criação do banco ou um ambiente com versões integralmente fixadas; essas etapas precisam ser preparadas antes da execução.

Com as dependências e o banco configurados:

```bash
python main.py
```

Para encerrar a conversa, digite `sair` ou `fim`.

## Escopo do projeto

Protótipo de estudo de agentes com ferramentas, especialização por domínio e consulta a documentos. O histórico é mantido em memória durante a execução.

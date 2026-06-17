# 🤖 Chocolatech RH Assistant

Assistente virtual corporativo desenvolvido para responder dúvidas de colaboradores sobre políticas internas, benefícios, férias, banco de horas e processos de RH.

O projeto utiliza IA Generativa integrada ao Telegram e uma base de conhecimento armazenada em banco de dados MySQL.

## Objetivo
Reduzir a demanda operacional do RH, fornecendo respostas rápidas e padronizadas aos colaboradores através de um canal já utilizado pela empresa.

| Situação Atual (AS IS)          | Situação Proposta (TO BE)  |
| ------------------------------- | -------------------------- |
| RH responde dúvidas manualmente | Atendimento automatizado   |
| Dependência de especialistas    | Conhecimento centralizado  |
| Tempo elevado de resposta       | Respostas imediatas        |
| Informações dispersas           | Base única de conhecimento |

## Tecnologias

* n8n
* Telegram Bot API
* MySQL
* Cohere
* SQL
* Engenharia de prompt
* RAG

## Arquitetura da Solução

<img width="584" height="395" alt="image" src="https://github.com/user-attachments/assets/c31159bb-f494-4c97-874f-0784e336b4a1" />


```
┌─────────────┐
│ Colaborador │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ Telegram    │
└──────┬──────┘
       │
       ▼
┌─────────────┐
│ n8n Agent   │
└──────┬──────┘
       │
 ┌─────┼─────────────┐
 ▼     ▼             ▼
MySQL  Vector Store  Memory
 │         │
 └────┬────┘
      ▼
   Cohere
      │
      ▼
Resposta ao usuário
```

## Modelo RAG

```
Pergunta:
"Quantos dias de férias eu tenho?"

        │
        ▼

AI Agent recebe pergunta

        │
        ▼

Busca contexto em:
- Vector Store (políticas RH)
- MySQL (saldo do funcionário)

        │
        ▼

Cohere recebe:
Pergunta + Contexto

        │
        ▼

Gera resposta

        │
        ▼

Telegram envia ao usuário
```

## Fluxo

1. Usuário envia uma pergunta pelo Telegram.
2. O n8n recebe a mensagem.
3. O fluxo consulta a base de conhecimento no MySQL.
4. O contexto encontrado é enviado para o Cohere.
5. A IA gera uma resposta baseada apenas nos dados corporativos.
6. A resposta é devolvida ao usuário via Telegram.

<img width="904" height="526" alt="image" src="https://github.com/user-attachments/assets/c79dcd31-1e35-43a1-a557-f510b69d4e6e" />

## 🧑‍💻 Autor
</p>
<p align="center">
Desenvolvido com 💙 por <strong>Iridiana Campos</strong>
</p>
<p align="center">

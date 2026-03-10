# 📘 Envio de Cadastros - Encontro Digital

## 🕒 Frequência

- **Diariamente**, às **03:00 da manhã (GMT-3)**.
- São enviados **todos os cadastros criados ou atualizados no dia anterior**.

---

## 📨 Formato da Requisição

- **Método:** `POST`
- **Content-Type:** `application/json`

### Exemplo de Payload:

```json
{
  "event": "cadastro_export",
  "data": [
    {
      "_id": "60d21b4667d0d8992e610c85",
      "project_id": "projeto123",
      "event_id": "evento456",
      "user_hash": "abc123xyz",
      "reference": "credenciado",
      "name": "João da Silva",
      "email": "joao@email.com",
      "phone": "+5511999999999",
      "city": "São Paulo",
      "state": "SP",
      "position": "Gerente de Projetos",
      "document_type": "cpf",
      "document_number": "12345678900",
      "birth_date_text": "15/06/1985",
      "category_id": "cat123",
      "badge_name": "João Silva",
      "term": "Aceito os termos de privacidade e uso desta plataforma",
      "term_2": "Aceito receber comunicados da Fundmed e suas apoiadas",
      "createdAt": "2025-06-15T10:00:00Z",
      "updatedAt": "2025-06-15T18:00:00Z"
    }
  ]
}
```

---

## 📋 Campos Enviados

| Campo               | Tipo       | Descrição |
|-------------------- |---------- |---------- |
| `_id`               | string     | ID único do cadastro |
| `project_id`        | string     | Identificador do projeto |
| `event_id`          | string     | Identificador do evento |
| `user_hash`         | string     | Hash único do usuário na plataforma |
| `reference`         | string     | Indicação se o usuário é credenciado (ex.: `"credenciado"` ou outro valor definido pelo sistema) |
| `name`              | string     | Nome completo do participante |
| `badge_name`        | string     | Nome que aparecerá no crachá |
| `email`             | string     | E-mail do participante |
| `phone`             | string     | Telefone (formato internacional ou nacional) |
| `city`              | string     | Município do participante |
| `state`             | string     | Estado (sigla UF) |
| `position`          | string     | Cargo ou função |
| `document_type`     | string     | Tipo de documento (exemplo: `"cpf"`, `"cnpj"`) |
| `document_number`   | string     | Número do documento |
| `birth_date_text`   | string (formato `DD/MM/YYYY`) | Data de nascimento |
| `category_id`       | string     | ID da categoria associada ao participante |
| `term`              | string     | Termo de aceite |
| `term_2`            | string     | Aceite de comunicações |
| `createdAt`         | string (ISO 8601 DateTime) | Data e hora de criação do cadastro |
| `updatedAt`         | string (ISO 8601 DateTime) | Data e hora da última atualização do cadastro |

---

## ✅ Resposta Esperada

O endpoint do cliente deve responder com:

```json
{
  "status": "received"
}
```

Com retorno HTTP **200 OK**.

---

## 📌 Observações Finais

- **Os campos podem sofrer alterações ou adições futuras.**
- **Recomenda-se que o cliente implemente o parser de forma flexível para novos campos.**

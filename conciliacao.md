
# 📘 Envio de Conciliação Financeira - Encontro Digital

## 🕒 Frequência

- **Semanalmente**, às **03:00 da manhã (GMT-3)**, sempre **às quintas-feiras**.
- Inclui as movimentações financeiras referentes ao período de **segunda a domingo da semana anterior**.

---

## 📨 Formato da Requisição

- **Método:** `POST`
- **Content-Type:** `application/json`

### Sobre os valores numéricos:

- **Todos os valores monetários são enviados como inteiros (integer)**, representando **centavos**.

### Valores possíveis para enums:

| Campo               | Valores possíveis |
|------------------- |------------------ |
| `payment_method_id` | `"Cartão de Crédito"`, `"Boleto"`, `"Pix"`, `"Cortesia"`, `"Gratuito"` |
| `payment_status_id` | `"Aguardando"`, `"Pago"`, `"Cancelado"`, `"Estornado"` |
| `operation`         | `"Crédito"`, `"Saque"`, `"Estorno"` |

---

## ✅ Exemplo de Payload

```json
{
  "event": "financeiro_export",
  "period": {
    "start_date": "2025-06-09",
    "end_date": "2025-06-15"
  },
  "data": [
    {
      "reference_number": "REF123",
      "project": "projeto123",
      "date": "2025-06-15",
      "operation_type": "Venda",
      "payment_method_id": "Pix",
      "payment_status_id": "Pago",
      "total": 15000,
      "installment": 1,
      "tax": 500,
      "transaction_tax": 300,
      "fees": 200,
      "total_tax": 1000,
      "antecipation_gap": 150,
      "operation_fee": 200,
      "administration_tax": 100,
      "sacado": -14000,
      "total_recipe": 14000,
      "total_expense": 0,
      "saldo": 14000,
      "product": "Ingresso VIP",
      "client_id": "00c6564e-6faa-4235-bce6-10c4304bb2fe"
      "client_name": "João da Silva",
      "client_document": "36814232022",
      "sale_hash": "abc123xyz",
      "installment_value": 15000,
      "transaction_id": "trans789",
      "operation": "Crédito",
      "operation_type_raw": "sale",
      "observation": "Pagamento confirmado"
    }
  ]
}
```

---

## 📋 Campos Enviados

| Campo                 | Tipo        | Descrição |
|---------------------- |----------- |---------- |
| `reference_number`   | string      | Número de referência da transação |
| `project`            | string      | Identificador do projeto |
| `date`               | string (YYYY-MM-DD) | Data da transação |
| `operation_type`     | string      | Tipo de operação (ex.: Venda, Saque) |
| `payment_method_id`  | string      | Meio de pagamento |
| `payment_status_id`  | string      | Status do pagamento |
| `total`              | integer     | Valor total da transação (em centavos) |
| `installment`        | integer     | Número de parcelas |
| `tax`                | integer     | Taxa de venda (em centavos) |
| `transaction_tax`    | integer     | Taxa de transação (em centavos) |
| `fees`               | integer     | Juros (em centavos) |
| `total_tax`          | integer     | Custo total da venda (em centavos) |
| `antecipation_gap`   | integer     | Diferença de antecipação (em centavos) |
| `operation_fee`      | integer     | Taxa de saque (em centavos) |
| `administration_tax` | integer     | Taxa administrativa (em centavos) |
| `sacado`             | integer     | Valor sacado ou estornado (em centavos, pode ser negativo) |
| `total_recipe`       | integer     | Entrada líquida (em centavos) |
| `total_expense`      | integer     | Saída líquida (em centavos) |
| `saldo`              | integer     | Saldo final (em centavos) |
| `client_id`          | string      | Chave de identificação do cliente |
| `client_name`        | string      | Nome do comprador |
| `client_document`    | string      | Documento do comprador |
| `sale_hash`          | string      | Chave de identificação da venda |
| `installment_value`  | integer     | Valor de cada parcela (em centavos) |
| `transaction_id`     | string      | ID da transação |
| `operation`          | string      | Tipo da operação (ex.: Crédito, Saque, Estorno) |
| `operation_type_raw` | string      | Tipo de operação em formato técnico |
| `observation`        | string      | Observações adicionais |

---

## ✅ Exemplo de Resposta Esperada

```json
{
  "status": "received"
}
```

O endpoint do cliente deve garantir retorno **HTTP 200 OK**.

---

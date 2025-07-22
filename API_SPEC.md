# API Specification

## Base URL
```
http://localhost:3000/api/v1
```

## Authentication
All endpoints require authentication via Bearer token or API key.

```http
Authorization: Bearer <jwt_token>
```

---

## Endpoints

### 1. Create Wallet

**POST** `/wallets`

Creates a new Bittensor wallet with encrypted private key storage.

#### Request Body
```json
{
  "password": "string",      // Required: Password for key encryption
  "name": "string"           // Optional: Wallet nickname
}
```

#### Response
```json
{
  "success": true,
  "data": {
    "wallet_id": "uuid",
    "public_address": "5Gw...",  // SS58 format
    "created_at": "2024-01-01T00:00:00Z"
  }
}
```

#### Error Responses
- `400`: Invalid password requirements
- `500`: Key generation failure

---

### 2. Get Wallet Balance

**GET** `/wallets/:id/balance`

Retrieves the current TAO balance for the specified wallet.

#### Parameters
- `id` (path): Wallet UUID

#### Response
```json
{
  "success": true,
  "data": {
    "wallet_id": "uuid",
    "balance": "1000.500000000",  // TAO amount as string
    "currency": "TAO",
    "last_updated": "2024-01-01T00:00:00Z"
  }
}
```

#### Error Responses
- `404`: Wallet not found
- `503`: Bittensor network unavailable

---

### 3. Transfer TAO

**POST** `/wallets/:id/transfer`

Initiates a TAO transfer from the specified wallet.

#### Parameters
- `id` (path): Sender wallet UUID

#### Request Body
```json
{
  "recipient_address": "5Fw...",  // SS58 format
  "amount": "100.000000000",      // TAO amount as string
  "password": "string"            // Wallet password for signing
}
```

#### Response
```json
{
  "success": true,
  "data": {
    "transaction_id": "uuid",
    "from_address": "5Gw...",
    "to_address": "5Fw...",
    "amount": "100.000000000",
    "fee": "0.001000000",
    "status": "pending",
    "created_at": "2024-01-01T00:00:00Z"
  }
}
```

#### Error Responses
- `400`: Invalid recipient address or insufficient balance
- `401`: Incorrect password
- `404`: Wallet not found

---

### 4. Get Transaction History (Bonus)

**GET** `/wallets/:id/history`

Retrieves paginated transaction history for the wallet.

#### Parameters
- `id` (path): Wallet UUID
- `page` (query): Page number (default: 1)
- `limit` (query): Results per page (default: 20, max: 100)
- `type` (query): Filter by transaction type (sent, received, all)

#### Response
```json
{
  "success": true,
  "data": {
    "transactions": [
      {
        "transaction_id": "uuid",
        "type": "sent",
        "from_address": "5Gw...",
        "to_address": "5Fw...", 
        "amount": "100.000000000",
        "fee": "0.001000000",
        "status": "completed",
        "block_hash": "0x...",
        "timestamp": "2024-01-01T00:00:00Z"
      }
    ],
    "pagination": {
      "current_page": 1,
      "total_pages": 5,
      "total_items": 94,
      "items_per_page": 20
    }
  }
}
```

---

## Error Response Format

All error responses follow this structure:

```json
{
  "success": false,
  "error": {
    "code": "VALIDATION_ERROR",
    "message": "Invalid request parameters",
    "details": {
      "field": "amount",
      "reason": "Must be a positive number"
    }
  },
  "timestamp": "2024-01-01T00:00:00Z"
}
```

## Rate Limiting

- Wallet creation: 5 requests per hour per IP
- Balance checks: 100 requests per minute per user
- Transfers: 10 requests per minute per wallet

## Status Codes

- `200`: Success
- `201`: Created
- `400`: Bad Request
- `401`: Unauthorized
- `403`: Forbidden
- `404`: Not Found
- `429`: Too Many Requests
- `500`: Internal Server Error
- `503`: Service Unavailable 
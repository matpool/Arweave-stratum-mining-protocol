# Arweave Stratum mining protocol
## login

Miner send `login` request after connection successfully established for authorization on pool.

#### Example request:
```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "method": "login",
  "params": {
    "login": "account.miner",
    "pass": "x",
    "agent": "node/v2.0.0.1"
  }
}
```

#### Example success reply:
```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "error": null,
  "result": {
    "height": 234234,
    "status": "OK",
  }
}
```

#### Example error reply:
```json
{
  "id": 1,
  "jsonrpc": "2.0",
  "error": {
    "code": -1,
    "message": "Invalid payment address provided"
  }
}
```

## job
Pool send new job to miner. Miner should switch to new job as fast as possible.

#### Example notification:
```json
{
  "jsonrpc": "2.0",
  "method": "job",
  "params": {
    "job_id": "q7PLUPL25UV0z5Ij14IyMk8htXbj",
    "bds": "070780e6b9d60586ba419a0c224e3c6c3e134cc45c4fa04d8ee2d91c2595463c57e",
    "target": "b88d0600",
    "timestamp": 7656576474,
    "height": 223344,
  }
}
```

## submit
Miner send `submit` request after share was found.

#### Example request:
```json
{
  "id": 2,
  "jsonrpc": "2.0",
  "method": "submit",
  "params": {
    "job_id": "4BiGm3/RgGQzgkTI/xV0smdA+EGZ",
    "nonce": "d0030040",
    "hash": "e1364b8782719d7683e2ccd3d8f724bc59dfa780a9e960e7c0e0046acdb40100"
  }
}
```

#### Example success reply:
```json
{
  "id": 2,
  "jsonrpc": "2.0",
  "error": null,
  "result": {
    "status": "OK"
  }
}
```

#### Example error reply:
```json
{
  "id": 2,
  "jsonrpc": "2.0",
  "error": {
    "code": -1,
    "message": "Low difficulty share"
  }
}
```

## keepalived
Non standard but widely supported protocol extension. Miner send `keepalived` to prevent connection timeout.
#### Example request:
```json
{
  "id": 2,
  "method": "keepalived",
  "params": {
    "id": "1be0b7b6-b15a-47be-a17d-46b2911cf7d0"
  }
}
```

#### Example success reply:
```json
{
  "id": 2,
  "jsonrpc": "2.0",
  "error": null,
  "result": {
    "status": "KEEPALIVED"
  }
}
```

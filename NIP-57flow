```mermaid
sequenceDiagram
    participant ノード
    participant ウォレット
    participant Nostrクライアント
    participant LNURLサーバ
    participant Zapperノード

    Nostrクライアント->>LNURLサーバ: LUD06 GET request

    LNURLサーバ->>Nostrクライアント: LUD06 JSON response
    Note left of LNURLサーバ: allowsNostr : true <br/>nostrPubkey : Zapper Pubkey
    
    Nostrクライアント->>LNURLサーバ: LUD06 GET request(call back) 
    Note right of Nostrクライアント: ※callbackにzapリクエスト(kind:9734)を含む
    
    LNURLサーバ->>Zapperノード: API request invoice
    
    Zapperノード->>LNURLサーバ: API response
    Note left of Zapperノード: zapインボイス
    
    LNURLサーバ->>Nostrクライアント: LUD06 JSON response
    Note left of LNURLサーバ: zapインボイス

    Nostrクライアント->>ウォレット: (コピペなど)
    Note left of Nostrクライアント: zapインボイス

    ウォレット->>ノード: API pay invoice
    Note left of ウォレット: zapインボイス

    ノード->>Zapperノード: 送金
    
    Zapperノード->>Nostrクライアント: broadcast event
    Note left of Zapperノード: zapノート(kind:9735)

```

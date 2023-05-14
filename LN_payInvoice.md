Aliceが支払人<br>
Dinaが受取人<br>
Dinaはインボイスを発行してAliceに渡す<br>
Aliceはインボイスを使ってDinaへ送金

```mermaid
sequenceDiagram
    participant Aliceのウォレット
    participant ノードA
    participant ノードB
    participant ノードC
    participant ノードD
    participant Dinaのウォレット

    autonumber
    Dinaのウォレット->>ノードD: API request invoice
    ノードD->>Dinaのウォレット: API response
    Dinaのウォレット-->>Aliceのウォレット: (インボイスを渡す。渡す方法は任意)

    Aliceのウォレット->>ノードA: API pay invoice

    ノードA->>ノードB: HTLC転送
    ノードB->>ノードC: HTLC転送
    ノードC->>ノードD: HTLC転送
    ノードD->>ノードC: シークレット送信
    ノードC->>ノードB: シークレット送信
    ノードB->>ノードA: シークレット送信

```
※通常ノードDからのシークレット(別称プリイメジ)送信は迅速に行われるが、HODLインボイスだと意図的に抑制する。<br>
ノードDにおいてHODLインボイス決済APIが操作されるまでシークレット送信しないという仕組み。HODLインボイスを解析しても通常インボイスとは見分けが付かない。

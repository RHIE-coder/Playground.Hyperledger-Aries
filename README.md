# Hyperledger Aries

`Need to know Hyperledger Indy before learn Hyperledger Aries`

[github : `aries`](https://github.com/hyperledger/aries)<br>

![](./mdsrc/1.jpg)

 - Aries = Agent

![](./mdsrc/2.png)



<br>
<hr>
<br>

# [ What is Hyperledger Aries ]

<br><br>

## _프로젝트 개요_

`indy-node`를 통해 DID 및 신원 인증 관련 데이터를 블록체인에 저장하고 `indy-sdk`를 통해 클라이언트단과 블록체인 네트워크와 통신하였다.

Hyperledger Aries는 클라이언트 간의 데이터 전송에 관련된 표준과 프레임워크를 개발하는 프로젝트이다.

프로젝트 개발 프로세스는 다음과 같다.

 - `aries-rfcs` ACCEPT --> Aries Framework 개발

 - `aries-rfcs` ACCEPT --> Aries Cloud/Static Agent 개발


[github : `aries-rfcs`](https://github.com/hyperledger/aries-rfcs)<br>

<br><br>

## _Why Aries_

![](./mdsrc/3.jpg)

When it first began, the Hyperledger Indy project included code for all three of the lower layers—for the Indy SSI ledger at layer 1; for SSI agents, wallets and DID-to-DID communications at layer 2, and for ZKP-based credential exchange at layer 3.

This was very powerful, but also somewhat overwhelming for new developers. And it gave the impression that layers 2 and 3 were tied to the Hyperledger Indy permissioned blockchain code at layer 1.

Separating out layer 2 and 3 code into a new independent project brings clarity to the fact that the goal of this four-layer stack is universal interoperability among all SSI ledgers, agents, wallets, verifiable credentials, and governance frameworks. This includes new DID networks such as the Bitcoin-based ION network announced by Microsoft at Consensus, the Ethereum network, the Veres One network, or any other modern blockchain capable of supporting DIDs and the other cryptographic primitives necessary for the DID Communications protocol at layer 2.

![](./mdsrc/4.jpg)

<br><br>

## _Aries 구조_

![](./mdsrc/6.png)

![](./mdsrc/5.png)

All Aries agent deployments have two logical components: a `framework` and a `controller`.

![](./mdsrc/7.png)

### - Framework

The framework contains the standard capabilities that enable an Aries agent to interact with its surroundings—ledgers, storage and other agents. A framework is an artifact of an Aries project that you don’t have to create or maintain, you just embed in your solution. The framework knows how to initiate connections, respond to requests, send messages and more. However, a framework needs to be told when to initiate a connection. It doesn’t know what response should be sent to a given request. It just sits there until it’s told what to do.

### - Controller

The controller is the component that, well, controls, an instance of an Aries framework’s behavior—the business rules for that particular instance of an agent. The controller is the part of a deployment that you build to create an Aries agent that handles your use case for responding to requests from other agents, and for initiating requests.

<br><br>


## _대표 Framework_ : `aries-cloudagent-python`

[github : `aries-cloudagent-python`](https://github.com/hyperledger/aries-cloudagent-python)<br>

![](./mdsrc/8.png)

## _Indy + Aries 플랫폼_

![](./mdsrc/9.jpg)


EXAMPLE USAGE

### - faber-local.py

```py
PYTHONPATH=.. ../bin/aca-py start \
   --endpoint http://127.0.0.1:8020 \
   --label faber.agent \
   --inbound-transport http 0.0.0.0 8020 \
   --outbound-transport http \
   --admin 0.0.0.0 8021 \
   --admin-insecure-mode \
   --wallet-type indy \
   --wallet-name faber.agent916333 \
   --wallet-key faber.agent916333 \
   --preserve-exchange-records \
   --auto-provision \
   --genesis-url http://localhost:9000/genesis \
   --trace-target log \
   --trace-tag acapy.events \
   --trace-label faber.agent.trace \
   --auto-ping-connection \
   --auto-respond-messages \
   --auto-accept-invites \
   --auto-accept-requests \
   --auto-respond-credential-proposal \
   --auto-respond-credential-offer \
   --auto-respond-credential-request \
   --auto-store-credential
```

### - alice-local.py

```py
PYTHONPATH=.. ../bin/aca-py start \
   --endpoint http://127.0.0.1:8030 \
   --label alice.agent \
   --inbound-transport http 0.0.0.0 8030 \
   --outbound-transport http \
   --admin 0.0.0.0 8031 \
   --admin-insecure-mode \
   --wallet-type indy \
   --wallet-name alice.agent420695 \
   --wallet-key alice.agent420695 \
   --preserve-exchange-records \
   --auto-provision \
   --genesis-url http://localhost:9000/genesis \
   --trace-target log \
   --trace-tag acapy.events \
   --trace-label alice.agent.trace \
   --auto-ping-connection \
   --auto-respond-messages \
   --auto-accept-invites \
   --auto-accept-requests \
   --auto-respond-credential-proposal \
   --auto-respond-credential-offer \
   --auto-respond-credential-request \
   --auto-store-credential
```

###### MY TEST

가상환경
```
python3 -m venv tutorial-env
source ~/myenv/bin/activate
pip install --upgrade pip
```

```
pip install aries_cloudagent
pip install aiohttp
```
명령어
```py
./aca-py start \
   --endpoint http://127.0.0.1:8040 \
   --label alice.agent \
   --inbound-transport http 0.0.0.0 8040 \
   --outbound-transport http \
   --admin 0.0.0.0 8041 \
   --admin-insecure-mode \
   --wallet-type indy \
   --wallet-name alice.agent420695 \
   --wallet-key alice.agent420695 \
   --preserve-exchange-records \
   --auto-provision \
   --genesis-url http://localhost:9000/genesis \
   --trace-target log \
   --trace-tag acapy.events \
   --trace-label alice.agent.trace \
   --auto-ping-connection \
   --auto-respond-messages \
   --auto-accept-invites \
   --auto-accept-requests \
   --auto-respond-credential-proposal \
   --auto-respond-credential-offer \
   --auto-respond-credential-request \
   --auto-store-credential
```

<br><br><br><br><hr><br><br><br><br>

# [DEMO : Aries OpenAPI DEMO]

[HERE](./getting_started_memo/01.OpenAPI.md)

## _If Want to Stop Containers_

```cmd
docker stop faber
docker stop alice
```
<br><br>

## _build VON network locally_

Comming Soon


<br><br><br><br><hr><br><br><br><br>

# [Explore]

## _Aries_

[aries](https://github.com/hyperledger/aries)<br>
[aries-rfcs](https://github.com/hyperledger/aries-rfcs)<br>

## _Aries SDK_

[aries-sdk-javascript](https://github.com/hyperledger/aries-sdk-javascript)<br>
[aries-sdk-android](https://github.com/hyperledger/aries-sdk-android)<br>
[aries-sdk-java](https://github.com/hyperledger/aries-sdk-java)<br>
[aries-sdk-ruby](https://github.com/hyperledger/aries-sdk-ruby)<br>

## _Aries Framework_

[aries-cloudagent-python](https://github.com/hyperledger/aries-cloudagent-python)<br>


The Aries Cloud Agent Python currently only supports Hyperledger Indy-based verifiable credentials and public ledger. Longer term (as we'll see later in this guide) protocols will be extended or added to support other verifiable credential implementations and public ledgers.

[aries-framework-dotnet](https://github.com/hyperledger/aries-framework-dotnet)<br>
[aries-framework-javascript](https://github.com/hyperledger/<br>aries-framework-javascript)<br>
[aries-framework-javascript-ext](https://github.com/hyperledger/<br>aries-framework-javascript-ext)<br>
[aries-framework-go](https://github.com/hyperledger/aries-framework-go)<br>
[aries-framework-go-ext](https://github.com/hyperledger/aries-framework-go-ext)<br>

## _vcx_

[aries-vcx](https://github.com/hyperledger/aries-vcx)<br>

## _more..._

[GITHUB EXPLORER](https://github.com/orgs/hyperledger/repositories?language=&q=aries&sort=&type=)


<br><br><br><br><hr><br><br><br><br>

# [ Issue & On-going ]


<br><br><br><br><hr><br><br><br><br>

# [ Thinking ]



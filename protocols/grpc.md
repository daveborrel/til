# gRPC

```
Card card = new Card()
Result result = paymentService.processPayment(card)
```

The processPayment isn't actually in the code, under the hood, its a network call to somewhere else. This is an example of RPC.

Remote Procedure Call (RPC) - A software communication protocol that allows one program to request a service from another program on a different computer and network.

gRPC - a popular implementation of RPC.

Why is it popular?
- uses a protocol buffer
- the `.proto` file allows server and clients to choose their own programming languages
- much faster than JSON

Example Run Through

Order Service --> gRPC Client --> HTTP/2 --> gRPC Server --> Payment Service
Payment Service --> gRPC Server --> HTTP/2 --> gRPC Client --> Order Service

Main Use Cases
- gRPC excels in connecting services within microservices

### Sources

[RPC - Martin Kleppman](https://www.youtube.com/watch?v=S2osKiqQG9s&ab_channel=MartinKleppmann)
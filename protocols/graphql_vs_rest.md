# GraphQL vs REST

REST is the predominant architecture for APIs. However, GraphQL has been growing in popularity since 2015.

Althought REST has its benefits, some drawbacks include:
- Over-fetching and under-fetching, Rigid Structure, Less efficient for complex queries.

## GraphQL 
Avoid repeated requests by allowing clients to find everything that they need in a single endpoint. This is possible because the GraphQL queries can traverse relatred objects and their fields.

Operation
```
{
  hero {
    name
  }
}
```

Response
```
{
  "data": {
    "hero": {
      "name": "R2-D2"
    }
  }
}
```

We can think of the following use cases for each type

**REST** - Web services and APIs, Microservices, CRUD, Mobile Applications

**GraphQL** - Applications with complex, interrelated data, real time applications, rapidly evolving FE requirements, aggregation of data from multiple microservices.

### Sources
[GraphQL Website](https://graphql.org/)
[LUC: graphql vs rest](https://blog.levelupcoding.com/p/luc-69-graphql-vs-rest-navigating-the-evolving-landscape-of-api-design)
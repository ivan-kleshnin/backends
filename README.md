# High-level backend development is an open-problem

There are multiple approaches to develop a backend/API to your Web or Mobile app nowadays.
My goal here is to structure and categorize them to hopefully get a more precise picture
on what is going on here.

In 2020 there's no obvious way to approach API building. Like in 2012 it was still believed by many
that REST can be implemented "correctly" to "solve all our problems". It couldn't be further
from the truth but there was hope at least. Not anymore. Twitter, Facebook, Netflix, Google and many
other teams tried-and-discarded the very idea of REST layers/hierarchy as something worthy.

One of the key ideas of REST (documentation should be somehow tied to data) was viable but approached 
from an entirely wrong angle. Bloating your HTTP with unrequested links and metadata, from the present, 
looks almost insane. This was solved by GraphQL (among other key points) in kinda the opposite way to what was originally proposed
by Roy Fielding. It's easy to judge with a hindsight, of course, but the point is: GraphQL is a drop-in REST replacemend with mostly pros and no cons.

So what next? Many original questions on how to approach API remain and new ones keep emerging. 
"The perfect API" now looks less achievable then ever, despite all the collective effort of scientists, engineers, programmers and all the other.

### 🔭 1. Custom GraphQL API

Examples: Apollo-Server. 

TODO describe PROS and CONS

### 🔭 2. Runtime GraphQL Query &rarr; Relational Query

Examples: JoinMonster, SQLMancer.

TODO describe PROS and CONS

### 🔭 3. Runtime GraphQL Query &rarr; Graph Query

Can be runtime or pregenerated.

Examples: [Neo4J-GraphQL-JS](https://github.com/neo4j-graphql/neo4j-graphql-js) (GraphQL &rarr; Cypher)

TODO describe PROS and CONS
 
### 🔭 4. Relational DB &rarr; GraphQL API

Can be runtime or pregenerated.

Examples: PostGraphile, SubZero, [Super-Graph](https://github.com/dosco/super-graph)

TODO describe PROS and CONS

### 🔭 5. Graph DB &rarr; GraphQL API

(not aware of any)

### 🔭 6. Relational DB &larr; Custom Code &rarr; GraphQL API

Examples: Prisma (ecosystem)

TODO describe PROS and CONS

### 🔭 7. Relational DB &larr; Custom Data via UI &rarr; GraphQL API

Examples: [GraphCMS](https://graphcms.com/).

TODO describe PROS and CONS

### 🔭 8. Relational DB &larr; GraphQL Types &rarr; GraphQL API

Mostly pregenerated.

Examples: Hasura

TODO describe PROS and CONS

### 🔭 9. Graph DB &larr; GraphQL Types &rarr; GraphQL API

Examples: FaunaDB.

TODO describe PROS and CONS

### 🔭 10. GraphQL-speaking DBs

Examples: [Dgraph](https://dgraph.io/).

TODO describe PROS and CONS

---

[graphql]: https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/graphql/graphql.png

# High-level backend development is an open problem

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

TODO: redefine pros and cons per vendor, not per category. Many of pros and cons are vendor-specific.

### 🔮 0. Previous state of the art in REST

#### Examples

👉 [Firebase](https://firebase.google.com/?hl=ru)<br/>
Used to be considered expensive, now is fine in comparison ;) Realtime out of the box.<br/>
Limited filtering and data-modelling capabilities.

#### Pros & Cons

&plusmn; Automatic REST API<br/> 
&minus; Performance (too many queries)<br/> 
&minus; Ergonomics (no static typing => no precise docs, nothing like GraphiQL, etc)<br/> 
&minus; N+1 problem: Dataloader helps with Child &rarr; Parent, fails in Parent &rarr; Child (filtering is pushed from DB to App)<br/> 

### 🔮 1. Custom GraphQL API

#### Examples

👉 [Apollo-Server](https://www.apollographql.com/docs/apollo-server/) + [Dataloader](https://github.com/graphql/dataloader)<br/>
Pretty good and intuitive tools.

#### Pros & Cons

&plusmn; Custom GraphQL API (magic vs boilerplate)<br/>
&minus; Custom Migrations<br/>
&minus; GraphQL to SQL is too complex to inline in your business logic<br/>
&minus; N+1 problem: Dataloader helps with Child &rarr; Parent, fails in Parent &rarr; Child (filtering is pushed from DB to App)<br/>
&plus; Single API layer<br/>
&plus; Deployment freedom<br/>

### 🔮 2. Runtime GraphQL Query &rarr; Relational Query

#### Examples

👉 [Join-Monster](https://github.com/join-monster/join-monster)<br/> 
Seems abandoned. Only basic sorting! Slow, according to feedback. :|

👉 [SQLMancer](https://github.com/danielrearden/sqlmancer)<br/>
Draft state. Going for a full rewrite a.t.m :|

#### Pros & Cons

&plusmn; Custom GraphQL API (magic vs boilerplate)<br/>
&minus; Custom Migrations<br/>
&plus; no N+1 and derivative problems<br/>
&plus; Single API layer<br/>
&plus; Deployment freedom<br/>
&minus; Performance (runtime query parsing is expensive)<br/> 
&minus; Performance (potential drops for join-heavy cases)<br/> 

### 🔮 3. Runtime GraphQL Query &rarr; Graph Query

#### Examples 

👉 [Neo4J-GraphQL-JS](https://github.com/neo4j-graphql/neo4j-graphql-js) (GraphQL &rarr; Cypher)<br/>
Draft state.

#### Pros & Cons

&plusmn; Custom GraphQL API (magic vs boilerplate)<br/>
&minus; Custom Migrations<br/> 
&plus; No N+1 and derivative problems<br/>
&plus; Single API layer<br/>
&plus; Deployment freedom<br/>
&minus; Performance (runtime query parsing is expensive)<br/> 
&plus; Performance (no joins, graphs!)<br/> 
 
### 🔮 4. Relational DB &rarr; GraphQL API

#### Examples

👉 [PostGraphile](https://www.graphile.org/postgraphile/)<br/>
Interesting project, many unique ideas. Small team – slow progress.

👉 [subZero](https://subzero.cloud/)<br/>
Kinda like cloud-only PostGraphile. Doesn't look like in active development.

👉 [Super-Graph](https://github.com/dosco/super-graph)<br/>
Basic API generator. Written in Go (can be &plusmn;).

#### Pros & Cons

&plusmn; Automagic GraphQL API (magic vs boilerplate)<br/>
&plus; Takes care of Migrations<br/>
&plus; No N+1 and derivative problems<br/>
&minus; API can't be derived from tables in general. Requires an extra API layer and many meta-data hints in DB.<br/>
&plus; Deployment freedom<br/>
&minus; Performance (runtime query parsing is expensive)<br/> 
&minus; Performance (potential drops for join-heavy cases)<br/> 

### 🔮 5. Graph DB &rarr; GraphQL API

#### Examples

Not aware of any

#### Pros & Cons

???

### 🔮 6. Relational DB &larr; Custom Code &rarr; GraphQL API

#### Examples

👉 [Prisma + ecosystem](https://www.prisma.io/)<br/>
I have little idea what Prisma-2 is and what is provides. They are constantly changing their focus so I lost the track and interest :(
Got $$$ investments, spent them on site design probably :shrug:

#### Pros & Cons

TODO describe

### 🔮 7. Relational DB &larr; Custom Data via UI &rarr; GraphQL API

#### Examples

👉 [GraphCMS](https://graphcms.com/).<br/>
Good UI. Kinda buggy. Pretty expensive at the moment.<br/>

&plusmn; Automagic GraphQL API (magic vs boilerplate)<br/>
&plus; Takes care of Migrations<br/> 
&plusmn; Performance (potential drops for join-heavy queries)<br/>
&plus; Single API layer in simple cases<br/>
&minus; Extra API layer in other cases<br/>

### 🔮 8. Relational DB &larr; GraphQL Types &rarr; GraphQL API

#### Examples

👉 [Hasura](https://hasura.io/)<br/>
Interesting project. Seem to know their stuff. Got $$$ investments, reinvested in development (unlike Prisma)<br/>
Gains traction recently. Good docs in comparison, many examples, established a community.<br/>

&plusmn; Automagic GraphQL API (magic vs boilerplate)<br/>
&plus; Takes care of Migrations<br/> 
&plus; Single API layer in simple cases<br/>
&plusmn; Performance (potential drops for join-heavy queries)<br/>
&plus; Autogenerated CMS<br/>
&minus; Extra API layer in other cases<br/>
&plus; Deployment freedom<br/>
&minus; Pretty expensive at the moment<br/>

### 🔮 9. Graph DB &larr; GraphQL Types &rarr; GraphQL API

#### Examples

👉 [FaunaDB](https://fauna.com/)<br/>
Looks promising. Very limited filtering and sorting capabilities.<br/>
Supports two languages: FQL (main) and GraphQL (basic, beta).<br/> 
Promise to add even more languages (instead of focusing) :shrug:<br/> 

#### Pros & Cons

&plusmn; Automagic GraphQL API (magic vs boilerplate)<br/>
&plus; Takes care of Migrations<br/> 
&plus; Distributed transactions<br/>
&plus; Performance (single GQL query = single DB query)<br/>
&plus; Single API layer in simple cases<br/>
&minus; Extra API layer in other cases<br/>
&minus; Extra language to learn (FQL)<br/>

### 🔮 10. GraphQL-speaking DBs

#### Examples

👉 [Dgraph](https://dgraph.io/)<br/>
Looks promising. Sparse docs. Supports two languages: GraphQL&plusmn; vs GraphQL.<br/>
The question of which-to-use-when is not addressed in docs :shrug:

#### Pros & Cons

&plusmn; Automagic GraphQL API (magic vs boilerplate)<br/>
&plus; Distributed transactions<br/>
&plus; Performance (single GQL query = single DB query)<br/>
&plus; Single API layer in simple cases<br/>
&minus; Extra API layer in other cases<br/>
&minus; Potential performance loss for cross API roundtrips (e.g. Dgraph permission resolving)<br/>

---

^ the above are my subjective opinions.

[graphql]: https://raw.githubusercontent.com/github/explore/80688e429a7d4ef2fca1e82350fe8e3517d3494d/topics/graphql/graphql.png

---

## Updates

- [Supabase](https://supabase.com) is a Firebase rival. RESTp & GraphQL API & SDK. TypeScript support is [WIP](https://github.com/supabase/supabase-js/issues/170). File uploads. No aggregation queries.
- [NHost](https://nhost.io/) is built on top of Hasura, Hasura-Auth and S3. No self-hosting option. Does not support URQL [a.t.m](https://issuehint.com/issue/nhost/nhost/271)
- [AppWrite](https://appwrite.io/) is another Firebase rival. Does not support GraphQL [a.t.m](https://github.com/appwrite/appwrite/discussions/1280)

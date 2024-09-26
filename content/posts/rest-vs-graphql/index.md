---
title: "Rest VS GraphQL"
date: 2024-07-06T00:00:00+06:00
description: Research on the differences between GraphQL and Rest API.
menu:
  sidebar:
    name: Rest VS GraphQL
    identifier: rest-vs-graphql
    weight: 10
hero: REST-vs-GraphQL.png
tags: ["Research", "Markdown"]
categories: ["Research"]
---

## GraphQL vs REST
GraphQL is an open source query language for APIs. It's architecture is subversive compared to the more commonplace REST architecture.

Originally developed by Facebook in 2012, then released as an open source project in 2015. "By 2027, more than 60% of enterprises will use GraphQL in production, up from less than 30% in 2024", according to the following [Gartner Report](https://www.apollographql.com/resources/gartner-when-to-use-graphql-to-accelerate-api-delivery?utm_source=the+new+stack&utm_medium=referral&utm_content=inline-mention&utm_campaign=tns+platform)
###### Disclaimer
The following article is not all encompassing. It's main purpose is to be used as an introductory lesson to these concepts. It's also my first article, so cheers! Any suggested edits can be sent to my email!

##### High-Level Overview
1. Query is sent from the client
2. This query is passed to a "Query Parser", which aptly named, parses the query
3. The query parser then checks against the "Schema" to ensure the query is valid
4. Once the query is validated, it gets passed to a "Resolver Function"
5. These resolvers are responsible for populating the response with the corresponding data that is requested in the query
##### Query Type Basics
In GraphQL there are "Queries" and "Mutations"
- Think of a Query as a standard read only operation (IE: GET request in REST terms)
- Think of a Mutation as an operation used for updating data (IE: POST request in REST terms)
#### GraphQL APIs vs REST APIs
REST APIs often struggle with providing more data than is required (over-fetching) or too little data (under-fetching)

Whereas GraphQL is designed to allow clients to request only the required amount of data

Observe the sample REST request below:
```
curl http://example.com/rest/v1/users
```

This request would return all users and their data. Depending on the functionality this could be considered a bit overkill if we only wanted to grab a specific user and only certain data

Observe the sample GraphQL query below:
```
query {
	users {
		id
		full_name
		email
	}
}
```

This request would return all users, but only their "id", "full_name", and "email"

This improves client and server performance, since REST requires users to fetch an entire data structure
##### Other Differences
There are many other differences between REST and GraphQL. For sake of brevity, here is a short list
- GraphQL serves all API on a single endpoint (IE: `/graphql`). Meaning any query made will be sent to this endpoint
- GraphQL queries can be sent as GET parameters or POST parameters
- Commonly GraphQL API only return "200 OK" responses, but this is up to the developer to implement
#### References
- [Gartner Report](https://www.apollographql.com/resources/gartner-when-to-use-graphql-to-accelerate-api-delivery?utm_source=the+new+stack&utm_medium=referral&utm_content=inline-mention&utm_campaign=tns+platform)
- [Black Hat GraphQL](https://penguinrandomhouselibrary.com/book/?isbn=9781718502840)
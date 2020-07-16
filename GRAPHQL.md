# Graphql
[https://graphql.org/](https://graphql.org/)
A query language for your API

GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.

### SCHEMA TWO TYPES
[https://graphql.org/learn/schema/](https://graphql.org/learn/schema/)

```sh
schema {
  query: Query
  mutation: Mutation
}
```

### SCALARS are String, boolean, Int,  Float, ID
```sh
* Int: A signed 32‐bit integer.
* Float: A signed double-precision floating-point value.
* String: A UTF‐8 character sequence.
* Boolean: true or false.
* ID: The ID scalar type represents a unique identifier, often used to refetch an object or as the key for a cache. The ID type is serialized in the same way as a String; however, defining it as an ID signifies that it is not intended to be human‐readable.
```

### VOCABULARY
```sh
* Character is a GraphQL Object Type, meaning it's a type with some fields. Most of the types in your schema will be object types.
* name and appearsIn are fields on the Character type. That means that name and appearsIn are the only fields that can appear in any part of a GraphQL query that operates on the Character type.
* String is one of the built-in scalar types - these are types that resolve to a single scalar object, and can't have sub-selections in the query. We'll go over scalar types more later.
* String! means that the field is non-nullable, meaning that the GraphQL service promises to always give you a value when you query this field. In the type language, we'll represent those with an exclamation mark.
* [Episode!]! represents an array of Episode objects. Since it is also non-nullable, you can always expect an array (with zero or more items) when you query the appearsIn field. And since Episode! is also non-nullable, you can always expect every item of the array to be an Episode object.
```

### NON-NULL in json
```sh
myField: null // valid
myField: [] // valid
myField: ['a', 'b'] // valid
myField: ['a', null, 'b'] // error
```

```sh
myField: [String]!

This means that the list itself cannot be null, but it can contain null values:
myField: null // error
myField: [] // valid
myField: ['a', 'b'] // valid
myField: ['a', null, 'b'] // valid
```
## QUERY
```sh
Basic query
 {
  getApplicants {
    data {
      id
      firstName
      lastName
      jobTitle {
        name
      }
    }
  }
}
```

### OrderBy
[https://hasura.io/docs/1.0/graphql/manual/queries/sorting.html](https://hasura.io/docs/1.0/graphql/manual/queries/sorting.html)
In example below, orderBy should be an array type and inside with an array of objects
```sh
query getApplicantsDetail {
  getApplicants(
    orderBy: [
      {
        field: JOB_TITLE,
        order: DESC
      }
    ]
    first: 20
  ) {
    data {
      id
      firstName
      lastName
      jobTitle {
        name
      }
    }
  }
}
```

### QUERY SPECIFIC APPLICANT
```sh
{
  getApplicant(id: 5) {
    id
    firstName
    lastName
    jobTitle {
      name
    }
  }
}
```

### QUERY MULTIPLE SPECIFIC APPLICANT
```sh
query getApplicantsDetail {
  getApplicant(id: 5) {
    id
    firstName
    lastName
    jobTitle {
      name
    }
  }

  getApplicant(id: 20) {
    id
    firstName
    lastName
    jobTitle {
      name
    }
  }
}
```

### SEARCH APPLICANTS
```sh
query searchApplicants($search: String) { search // argument, String scalar data type
  getApplicants( /
    orderBy:{ field: JOB_TITLE, order: DESC } // field/order: enum value
    first: 20 // first 20 items in the list
  ) {
    data {
      id
      firstName
      lastName
      jobTitle {
        name
      }
    }
  }
}
```

## MUTATION

###Add Post
```sh
mutation addPosts($post: PostInput) {
  addPost(post: $post) {
    id
    title
    content
  }
}```

### Register for account
```sh
mutation register {
  register(email: "belle@gmail.com", password: "botyok143")
}```

### Authentication
```sh
mutation authenticate {
  authenticate(email: "belle@gmail.com", password: "botyok143")
}```

### Get post with id 12
```sh
query getPost {
  post(id: 12) {
    id
    title
    content
    comments {
      content
    }
  }
}```

### Add Comment
```sh
mutation addComment {
  addComment(postId: 12, content: "Belle") {
    id
    postId
  }
}```

### Add Address
```sh
mutation address {
  upsertAddress(addressDetails: {
    address1: "Mandaue, Cebu",
    address2: "Lahug, Cebu City",
    city: "Cebu City",
    state: "Cebu",
    postalCode: "0000",
    country: "Philippines"
  }) {
    id
    address1
    address2
    city
    state
    postalCode
    country
  }
}```

### Update Address with id 374
```sh
mutation address {
  upsertAddress(id: 374, addressDetails: {
    address1: "Manila",
    address2: "Lahug, Cebu City",
    city: "Cebu City",
    state: "Cebu",
    postalCode: "0000",
    country: "Philippines"
  }) {
    id
    address1
    address2
    city
    state
    postalCode
    country
  }
}```

### To query variables
```sh
{
  "post":{
    	"title": "Hello!",
      "content": "belle belle"
  }
}```

### Authorization format
```sh
{
  "Authorization": "1ye6v27w7j8"
}```

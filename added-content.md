## Working with Types



- **Type by Inference**
- **Type Annotation**

Let's dig into each of these features and talk a bit more about each one.

### Type by Inference

TypeScript uses type inference to assume the type of a variable in a program,
based on the data type it was assigned at it's initial declaration. If we try to
change the data type, type inference will log a complaint.

```ts
let helloWorld = 'Hello, World!'

helloWorld = 2
// => Type 'number' is not assignable to type 'string'.
```

Let's say we want to create an object where the properties `firstName`,
`lastName`, and `occupation` are all strings, but the `id` property is a number.

```ts
const userObj = {
  id: 1,
  firstName: 'Audre',
  lastName: 'Lorde',
  occupation: 'Poet',
}

// {id: number, firstName: string, lastName: string, occupation: string}
```

Thanks to type inference, explicitly shaping an object like this will give us
the correct types but what if we want to do things a bit more dynamically?

### Defining Types

Sometimes inferring the types we're using in our code isn't always as explicit
and straight forward as the example above. TypeScript always knows the shapes of
our types - what methods and properties our variables do/don't contain. We can
use this concept of _shaping_, and define our types to fit the specific needs of
our programs by using _type annotations_. Type annotations ensure that we only
ever assign certain types to our variables, let's take a look.

```ts
// We can use an interface declaration to describe our object's shape:

interface User {
  id: number;
  firstName: string;
  lastName: string;
  occupation: string;
}

// Then we can use type annotations to ensure our object fits to this shape.

const userObj : User = {
  id: 1,
  firstName: 'Audre',
  lastName: 'Lorde',
  occupation: 'Poet',
}
```

If we had defined our `userObj` like the following TypeScript would have logged
a complaint:

```ts
const userObj : User = {
  id: 1,
  name: 'Audre Lorde',
  occupation: 'Poet',
}

// => Type '{ id: number; name: string; occupation: string; }' is not assignable to type 'User'.
// Object literal may only specify known properties, and 'name' does not exist
// in type 'User'.
```

We'll get more into this later, but for now just remember that type annotations
are super helpful!
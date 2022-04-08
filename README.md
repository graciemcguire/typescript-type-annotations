# Understanding Types

## Learning Goals

- Understand type inference
- Understand type annotations
- Work with `any` types

## Introduction

Working with Types is really the essence of TypeScript. In this lesson we will
focus on the different ways TypeScript will assume our types for us, and how we
can use type annotations to declare our own types not only on variables, but
with functions as well.

## Type Inference

In TypeScript, everything is _born_ with a type, and if we don't explicitly
declare what that type is, TypeScript will use type inference to assume the type
based on the data type it was assigned to at the initial declaration. If we try
to change the data type, type script will log a complaint.

> Note: In this lesson, the commented out lines in our code blocks are used to
> demonstrate what is shown when we hover our cursor over our variables. As you
> learned in the last lesson, a huge benefit of the TypeScript compiler is how
> it shows us syntax errors upon compiling, so we can fix them before run
> time... Even before compiling however, TypeScript will show us our types and
> simple syntax errors with squiggly error lines, with details explained just by
> hovering our cursor over the variables!

```ts
let numberEleven = "eleven";
// let numberEleven: string

numberEleven = 11;
// Type 'number' is not assignable to type 'string'.
// let number: string
```

Uh oh, that doesn't look good. By running our compiler (`tsc`), we can see more
details about these complaints in our terminal:

```ts
> tsc
index.ts: - error TS2322: Type 'number' is not assignable to type 'string'.

numberEleven = 11
~~~~~~~~~~~~

Found 1 error.
```

This error says, we can't assign the type `number` to our variable that's
already assigned a type `string`. If we accidentally made our initial variable a
string, we can simply just change that to be the numeral. This is especially
true because we've used the variable declaration `let`. What if we were to
switch that `let` for a `const`, and declare `numberEleven` as a constant?

```ts
const numberEleven = "eleven";
// const numberEleven: "eleven"

numberEleven = 11;
// Cannot assign to 'numberEleven' because it is a constant.
```

Yikes! By declaring a constant TypeScript is no longer reading our type
assignment has changed from `let numberEleven: string` to
`const numberEleven: 'eleven'`! This is called a _literal type_. We will get
more into some helpful uses of literal types later when we talk about _type
narrowing_, but for now feel free to read up on [Literal Types][] in the
TypeScript docs, and just remember that while declaring literal types can be
extremely helpful, if we're planning on doing so, it's generally best practice
to do so with _type annotation_, instead of inference.

## Type Annotations

As projects grow, variable types can get pretty unpredictable, so having them be
inferred or literally defined can get a bit difficult. Type annotations allow us
to tell our code what types our variables should or will be. We add type
annotations by adding a colon after a variable name but before it's assigned a
value.

```ts
let numberEleven: string = 'eleven'
// let numberEleven: string

let numericNumberEleven: number = 11
// let numericNumberEleven: number

let luckyNumberEleven: boolean = true
// let luckyNumberEleven: boolean

let eleven
// let eleven: any

let elevenStringOrNum: any = 'string!'
// let elevenStringOrNum: any

let elevenStringOrNum: any = 11
// let elevenStringOrNum: any
```

As you can see, we can annotate any primitive type to a variable, but we can
also assign them the `any` type if we need some flexibility!

### any Types

`any` types are akin to regular JavaScript variables. We can assign an any type
variable to a string then to a number then to a boolean and back to a string
without any errors. They particularly come in handy as a first step when
migrating an already established JavaScript file into TypeScript, or when we're
testing data and are unsure of how our data will come back to us.

## Conclusion

In this lesson we discussed the spectrum of types. From the strictest of the
strict, literal types won't allow us to change our variable types ever, to the
most easy going any types that let us change our types whenever we please! More
importantly though was understanding type inference, and detailing how to create
type annotations.

## Resources

- [Type Inference](https://en.wikipedia.org/wiki/Type_inference)
- [Literal Types](https://www.typescriptlang.org/docs/handbook/literal-types.html)
- [Type Annotation](https://www.typescriptlang.org/docs/handbook/typescript-tooling-in-5-minutes.html#type-annotations)
- [any Types](https://www.typescriptlang.org/docs/handbook/declaration-files/do-s-and-don-ts.html#any)

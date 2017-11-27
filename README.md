# validate-typescript
Extensible schema based validator that supports typescript typing.

This package strives meet the following criteria:

- lightweight
- inline
- strongly typed
- simple
- extensible
- convertable

TODO: Add hyperlinks

# Getting Started

## Example

TODO: getting started, simple example

# Validators

The following examples of `validate-typescript` schemas, illustrate the different validation methods.

**Note:** the comment `// type: TypeName` following the validator explicitly specifies the resultant typescript type inferred by the typescipt transpiler. This relates back to the *strongly typed* criteria.

## Type Validators

Expects an exact type match.

```ts
let schema = {
    myNumber: Type(Number),      // type: Number
    myString: Type(String),      // type: String
    myCustom: Type(CustomClass), // type: CustomClass
    // etc...
}
```

## Literal Validators

Expects an exact type and value match.

```ts
let schema = {
    number49:    49,              // type: number
    myCountry:   'South Africa',  // type: string
    dontDefine:  undefined,       // type: undefined
    allwaysNull: null,            // type: null
    // etc...
}
```

## Custom (Extension) Validators

Expects custom convertions and assertions to be valid.

```ts
let schema = {
    myEmail:  Email(),      // type: string
    sqlId:    ID(),         // type: number
    comeText: RegEx(/abc/), // type: string
    // etc...
}
```

## Nested Object Validators

TODO: description

```ts
let schema = {
    subObject: {
        a: ID(),
        b: Type(Date)
        c: {
            d: RegEx(/.+@gmail.com/)
        }
    } // type: { a: number, b: Date, c: { d: string } }
}
```

## Array Validators

TODO: description

```ts
let schema = {
    // array validation
    emailArray: [Email()]             // type: string[]
    idArray: [ID()]                   // type: number[]

    // array with multiple options validation
    arrayOfEmailOrId: [Email(), ID()] // type: (string | number)[]
}
```

## Options Validators

TODO: description

```ts
let schema = {
    // options validation
    options: Options([Type(Number), Type(String)]) // type: number | string

    // optional validation (i.e. not required)
    optional: Optional(ID())                       // type: number | undefined
    alsoOptional: Options([ID(), undefined])       // type: number | undefined

    // nullable validation
    maybeNull: Nullable(Type(String)),             // type: String | null
    alsoMaybeNull: Options([Type(String, null)]),  // type: String | null

    // array options
    arrayOptions: Options([[Email()], [ID()]])     // type: string[] | number[]
}
```

## Any or All Validators

TODO: description

```ts
let schema = {

    // validate any options
    anyOptions: Options([Type(Number), Type(String)], ValidationOptions.any)     // type: number | string
    alsoAny: Any([Type(Number), Type(String)])                                   // type: number | string

    // validate all options
    allOptions: Options([RegEx(/.+@gmail.com/), Email()], ValidationOptions.all) // type: number | string
    alsoAll: Any([RegEx(/.+@gmail.com/), Email()])                               // type: number | string
}
```
## Validation

- validate method

TODO: complete

## Assertions

TODO: complete

## Converters

TODO: complete

## Errors

TODO: complete

## Custom Validators

- Alias
- Validator

TODO: complete

## Recommendations

TODO: complete
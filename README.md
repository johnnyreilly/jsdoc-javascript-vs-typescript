# JSDoc JavaScript vs TypeScript

There's a debate to be had about whether using JavaScript or TypeScript leads to better outcomes when building a project. The introduction of using JSDoc annotations to type a JavaScript codebase introduces a new dynamic to this discussion.  This post will investigate what that looks like, and come to an (opinionated) conclusion.

If you'd talked to me in 2018 it would have been a solid "recommend TypeScript, steer away from JavaScript". The rationale is simple: I'm exceedingly convinced of the value that static typing provides in terms of productivity / avoiding bugs in production.

TypeScript has long had a good static typing story. JavaScript is dynamically typed and so historically has not had a good static typing story. Thanks to TypeScript support for JSDoc, these days there's a little more nuance in this discussion.

## What is JSDoc JavaScript?

JSDoc itself actually dates way back to 1999.  According to the [Wikipedia entry](https://en.wikipedia.org/wiki/JSDoc):

> JSDoc is a markup language used to annotate JavaScript source code files. Using comments containing JSDoc, programmers can add documentation describing the application programming interface of the code they're creating. 

The TypeScript team have taken JSDoc support and run with it. You can now use a [variant of JSDoc annotations](https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html) to provide type information in JavaScript files.

What does this look like? Well, to take a simple example, a TypeScript statement like so:

```ts
let myString: string; 
```

Could become the equivalent JavaScript statement with a JSDoc annotation:

```ts
/** @type {string} */
let myString; 
```

This is type enhanced JavaScript which the TypeScript compiler can understand and type check.

## Why use JSDoc JavaScript?

Why would you use JSDoc JavaScript instead of TypeScript? Well there's a number of possible use cases. 

Perhaps you're writing simple node scripts and you'd like a little type safety to avoid mistakes. Or perhaps you want to dip your project's toe in the waters of static type checking but without fully committing. JSDoc allows for that. Or perhaps your team simply prefers not having a compile step.

That, in fact, was the rationale of the webpack team. A little bit of history: webpack has always been a JavaScript codebase. As the codebase grew and grew, there was often discussion about using static typing. However, having a compilation step wasn't desired.

TypeScript had been quietly adding support for type checking JavaScript with the assistance of JSDoc since way back with the `--checkJs` compiler option in [TypeScript 2.3](https://www.typescriptlang.org/docs/handbook/release-notes/typescript-2-3.html#errors-in-js-files-with---checkjs).

A community member by the name of [Mohsen Azimi](https://twitter.com/mohsen____) experimentally started out using this approach to type check the webpack codebase. [This PR](https://github.com/webpack/webpack/pull/6862) ended up being a test case that helped both improve the type checking of JavaScript by TypeScript, and popularise using JSDoc to type check JavaScript codebases.

These days, JSDoc type checking with TypeScript is extremely powerful. Whilst not quite on par with TypeScript (not all TypeScript syntax is supported in JSDoc) the gap in functionality is pretty small.

It's a completely legitimate choice to build a JavaScript codebase with all the benefits of static typing.

## Why use TypeScript?

So if you were starting a project today, and you'd decided you wanted to make use of static typing, how do you choose?  TypeScript or JavaScript with JSDoc?

Well, unless you've a compelling need to avoid a compilation step, I'm going to suggest that TypeScript may be the better choice for a number of reasons.

Firstly, the tooling support for using TypeScript directly is better than that for JSDoc JavaScript. At the time of writing, things like refactoring tools etc in your editor work more effectively with TypeScript than with JSDoc JavaScript. (Although these are improving as time goes by.)

Secondly, working with JSDoc is distinctly "noisier".  It requires far more keystrokes to achieve the same level of type safety.  Consider the following TypeScript:

```ts
function stringsStringStrings(p1: string, p2?: string, p3?: string, p4 = "test"): string {
  // ...
}
```

As compared to the equivalent JSDoc JavaScript:

```ts
/**
 * @param {string}  p1
 * @param {string=} p2
 * @param {string} [p3]
 * @param {string} [p4="test"]
 * @return {string}
 */
function stringsStringStrings(p1, p2, p3, p4) {
  // ...
}
```

It may be my own familiarity with TypeScript speaking, but I find that the TypeScript is easier to read and comprehend as compared to the JSDoc JavaScript alternative.

The final reason for favouring TypeScript comes down to falling into the ["pit of success"](https://blog.codinghorror.com/falling-into-the-pit-of-success/). You're cutting *against* the grain when it comes to static typing and JavaScript. You can have it, but you have to work that bit harder to ensure that you have statically typed code. On the other hand, you're cutting *with* the grain when it comes to static typing and TypeScript. You have to work hard to opt out of static typing. The TypeScript defaults tend towards static typing, whilst the JavaScript defaults tend away. 

So in a way, I don't feel super strongly whether people use JavaScript or TypeScript. But having static typing will likely be a benefit to new projects. Bottom line, I'm keen that people fall into the "pit of success", so my recommendation for a new project would be TypeScript.
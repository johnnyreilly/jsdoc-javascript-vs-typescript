# jsdoc-javascript-vs-typescript

I've been pondering the JavaScript/TypeScript debate when it comes to languages we think may lead to better outcomes. If you'd talked to me in 2018 it would have been a solid "recommend TypeScript, steer away from JavaScript".

The rationale is simple: I'm exceedingly convinced of the value that static typing provides in terms of productivity / avoiding bugs in production.

TypeScript has long had a good static typing story. JavaScript is dynamically typed and so historically has not had a good static typing story.

These days there's a little more nuance to the picture. These days TypeScript supports static typing in JavaScript via JSDoc style comments:

https://www.typescriptlang.org/docs/handbook/jsdoc-supported-types.html

These allow the JavaScript written to be the JavaScript that ends up being run. No need for compilation. But you can use TypeScript to perform type checking and get that static typing goodness.

So, in a way, I don't mind so much whether people use JS or TS as long as they have static typing. It's arguable that is still this "using JavaScript" is really relying on "using TypeScript"; static typing-wise anyway. That's a fair point and I'd take it.

But I think, on balance, I'd still recommend directly writing TypeScript over JSDoc JavaScript. There's two reasons:

1. I find directly writing TypeScript to be more enjoyable / less noisy / with a better tooling experience.
2. You're cutting against the grain when it comes to static typing and JavaScript. You have to work hard to ensure that you have statically typed code. On the other hand, you're cutting with the grain when it comes to static typing and TypeScript. You have to work hard to opt out of static typing. The TypeScript defaults tend towards static typing, whilst the JavaScript defaults tend away. 

Bottom line, I'm keen that people fall into the "pit of success", so TypeScript. It might not surprise people that this is my present conclusion, but I thought it might be interesting to share my working.

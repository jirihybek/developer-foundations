# TypeScript

Below are workbook questions related to TypeScript. Write down your findings and answers to the questions.

---

## Fundamentals

#### 1. What is TypeScript? How does it differ from JavaScript?

(answer here)

#### 2. What are types? What is their purpose? What problems do they solve?

(answer here)

#### 3. What is transpilation? How does it differ from compilation?

(answer here)

#### 4. What is `tsc`? How do you use it? What does it produce?

(answer here)

#### 5. Can you run TypeScript directly without transpiling first? Compare Node.js vs. Bun vs. Deno.

(answer here)

#### 6. What happens to types at runtime? Does TypeScript provide runtime type checking?

(answer here)

---

## Basic Types

#### 7. What are the basic/primitive types in TypeScript? (`string`, `number`, `boolean`, `null`, `undefined`, `symbol`, `bigint`)

(answer here)

#### 8. What is the `any` type? Why is it considered bad practice to overuse it?

(answer here)

#### 9. What is the `unknown` type? How does it differ from `any`? When should you use it?

(answer here)

#### 10. What is the `never` type? When is it used?

(answer here)

#### 11. What is the `void` type? How does it differ from `undefined`?

(answer here)

#### 12. What are literal types? How can you use them?

(answer here)

#### 13. What are enums? What is the difference between numeric and string enums? What are const enums?

(answer here)

---

## Type Declarations

#### 13. What is the difference between `type` alias and `interface`? When would you use each?

(answer here)

#### 14. How do you define object types? What are optional properties (`?`) and readonly properties?

(answer here)

#### 15. How do you type arrays? What is the difference between `string[]` and `Array<string>`?

(answer here)

#### 16. How do you type functions? (parameter types, return types, function type expressions)

(answer here)

#### 17. What are tuple types? How do they differ from arrays?

(answer here)

---

## Union and Intersection Types

#### 18. What are union types (`|`)? When would you use them?

(answer here)

#### 19. What are intersection types (`&`)? When would you use them?

(answer here)

#### 20. What is type narrowing? What are type guards?

(answer here)

#### 21. What is discriminated union (tagged union)? Why is it useful?

(answer here)

#### 22. What is the `in` operator type guard? What is the `instanceof` type guard?

(answer here)

---

## Generics

#### 23. What are generics (type parameters)? Why are they useful?

(answer here)

#### 24. How do you define a generic function? A generic interface? A generic class?

(answer here)

#### 25. What are generic constraints (`extends`)? How do you limit what types can be used?

(answer here)

#### 26. What is the `keyof` operator? How is it commonly used with generics?

(answer here)

#### 27. What are indexed access types (`Type[Key]`)? How do you use them?

(answer here)

---

## Utility Types

#### 28. What are utility types? Why does TypeScript provide them?

(answer here)

#### 29. Explain these utility types and when you would use them:
- `Partial<T>`
- `Required<T>`
- `Readonly<T>`
- `Pick<T, K>`
- `Omit<T, K>`

(answer here)

#### 30. Explain these utility types and when you would use them:
- `Record<K, V>`
- `Extract<T, U>`
- `Exclude<T, U>`
- `NonNullable<T>`
- `ReturnType<T>`

(answer here)

---

## Advanced Types

#### 31. What are mapped types? How do they work? Give an example.

(answer here)

#### 32. What are conditional types (`T extends U ? X : Y`)? When are they useful?

(answer here)

#### 33. What is the `infer` keyword? How is it used in conditional types?

(answer here)

#### 34. What are template literal types? How can you use them?

(answer here)

#### 35. What is type assertion (`as`)? When is it appropriate to use? What are the risks?

(answer here)

#### 36. What is a const assertion (`as const`)? What does it do?

(answer here)

---

## Type Declarations and Third-Party Libraries

#### 37. What are `.d.ts` files (declaration files)? What is their purpose?

(answer here)

#### 38. What is DefinitelyTyped? What are `@types/*` packages?

(answer here)

#### 39. How do you add types for a JavaScript library that doesn't have them?

(answer here)

#### 40. What is `declare` keyword? When do you use it?

(answer here)

---

## Configuration (tsconfig.json)

#### 41. What is `tsconfig.json`? What is its purpose?

(answer here)

#### 42. What does `strict: true` enable? Why is it recommended?

(answer here)

#### 43. What are some important compiler options and what do they do?
- `target`
- `module`
- `moduleResolution`
- `esModuleInterop`
- `skipLibCheck`
- `outDir`

(answer here)

#### 44. What is the difference between `include`, `exclude`, and `files` in tsconfig?

(answer here)

#### 45. What is `strictNullChecks`? What problems does it help prevent?

(answer here)

---

## Practical TypeScript

#### 46. How do you handle situations where you know more about a type than TypeScript does? (type assertions, non-null assertion `!`)

(answer here)

#### 47. What is the difference between `type` imports and regular imports? What is `import type`?

(answer here)

#### 48. How do you type React components and hooks? (props, useState, useRef, event handlers)

(answer here)

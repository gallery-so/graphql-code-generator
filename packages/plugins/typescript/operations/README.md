## Hello 👋

This is Gallery's fork of [https://github.com/dotansimha/graphql-code-generator](https://github.com/dotansimha/graphql-code-generator). More specifically, a fork of the [`@graphql-codegen/typescript-oeprations`](https://www.graphql-code-generator.com/plugins/typescript/typescript-operations) package.

### What does this fork do?

We simply add the `id` field to any type that has it available to match Relay's expectations. See below 👇.

### Why might you need this?

If you're using Relay, you may already know that Relay will automatically select an `id` field if one is available in the schema. It's quite annoying when the generated types spit out by the codegen plugin don't match what Relay is expecting.

### How to use this package?

1. Remove `@graphql/typescript-operations`
   ```bash
   yarn remove @graphql/typescript-operations
   ```
2. Install `@gallery-so/typescript-operations`
   ```bash
   yarn add @gallery-so/typescript-operations
   ```
3. Update your `codegen.yml` file to include the `autoSelectId` field.

```diff
schema: ./schema.graphql
documents: ./src/**/*.{ts,tsx}
generates:
   ./src/__generated__/operations.ts:
config:
   avoidOptionals: true
+  autoSelectId: true
plugins:
  - typescript
- - typescript-operations
+ - "@gallery-so/typescript-operations"
```

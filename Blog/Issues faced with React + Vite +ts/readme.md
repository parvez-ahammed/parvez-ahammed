# Parsing markdown files


## Project Configuration

```

Vite + React + Typescript + ChakraUI

```


## Install react-markdown
    
```
npm install react-markdown
```

## Create a basic component

```tsx

import { Box } from "@chakra-ui/react";
import ReactMarkdown from "react-markdown";


const MarkdownTest = () => {
  return (
    <Box>
      <ReactMarkdown
        children={`# Test markdown!`}
        skipHtml 
      />
    </Box>
  );
};

export default MarkdownTest;

```

## Change vite-env.d.ts

```ts
declare module "*.md";
```

## Change vite.config.ts

```ts
import { defineConfig } from "vite";
import react from "@vitejs/plugin-react";

// https://vitejs.dev/config/
export default defineConfig({
  plugins: [
    react(),
    // Custom plugin to load markdown files
    {
      name: "markdown-loader",
      transform(code, id) {
        if (id.slice(-3) === ".md") {
          // For .md files, get the raw content
          return `export default ${JSON.stringify(code)};`;
        }
      }
    }
  ]
});
```

## Test usage 

```tsx

import { Box } from "@chakra-ui/react";
import ReactMarkdown from "react-markdown";
import ChakraUIRenderer from "chakra-ui-markdown-renderer";

// Import markdown files
import markdown from 'test.md';

const MarkdownTest = () => {
  return (
    <Box>
      <ReactMarkdown
        // Pass it as children
        children={markdown}
        components={ChakraUIRenderer()} // Skip this if you don't use ChakraUI
        skipHtml // Skip this if you don't use ChakraUI
      />
    </Box>
  );
};

export default MarkdownTest;
```


## Existing issue


```
Cannot find module ... or its corresponding type declarations
```

## Solution

```ts

// Add this before the import of the markdown
// @ts-ignore
```

## Materials followed

[Medium](https://onticdani.medium.com/how-to-load-and-render-markdown-files-into-your-vite-react-app-using-typescript-ba5f79822350)

[Stack overlflow](https://stackoverflow.com/questions/64732623/typescript-cannot-find-module-or-its-corresponding-type-declarations)
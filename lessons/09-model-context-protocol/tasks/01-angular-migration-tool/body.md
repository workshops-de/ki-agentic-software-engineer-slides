# Build an Angular Migration MCP Tool

You already have a working MCP server that can generate components. Now extend it with a tool that runs Angular version migrations — so the AI can execute the full update process for you.

## Your Goal

Add a `run_migration` tool to your MCP server that executes an Angular version migration using the Angular CLI.

The AI should be able to respond to prompts like:

```
Migrate the project to Angular 19
```

## Steps

### 1. Register the tool

Add a new `registerTool` call in `tools/angular-mcp/index.ts`:

```ts
server.registerTool(
  'run_migration',
  {
    title: 'Run Angular Migration',
    description:
      'Executes an Angular version migration using ng update. ' +
      'Use this when the user wants to update Angular to a specific version.',
    inputSchema: {
      version: z.string().describe("Target Angular major version, e.g. '19'"),
    },
  },
  async ({ version }) => {
    // Your implementation here
  }
);
```

### 2. Implement the migration command

Inside the handler, build and execute the Angular update command:

```ts
const cmd = `npx @angular/cli update @angular/core@${version} @angular/cli@${version} --allow-dirty`;
```

- Run the command with `exec(cmd, { cwd: projectRoot })`
- Return a success message including `stdout` on success
- Return a clear error message including `stderr` on failure

### 3. Build and reload

```bash
npm run build.angular-mcp
```

Reload Cursor via **Cmd+Shift+P → Developer: Reload Window**.

### 4. Test it

Ask the AI in Cursor chat:

```
Migrate this project to Angular 19
```

The AI should call your `run_migration` tool and show the output.

## Success Criteria

- [ ] The `run_migration` tool is registered in `index.ts`
- [ ] The tool accepts a `version` parameter
- [ ] The tool executes the correct `ng update` command
- [ ] Errors are caught and returned as readable messages
- [ ] The server builds and Cursor recognizes the new tool

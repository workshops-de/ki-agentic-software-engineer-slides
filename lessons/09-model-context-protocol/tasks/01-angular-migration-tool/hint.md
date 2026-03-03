<details>
<summary>💡 Hint 1: Tool handler skeleton</summary>

Your handler should follow the same pattern as `generate_component`:

```ts
async ({ version }) => {
  const cmd = `npx @angular/cli update @angular/core@${version} @angular/cli@${version} --allow-dirty`;
  try {
    const { stdout } = await exec(cmd, { cwd: projectRoot });
    return { content: [{ type: 'text', text: `✅ Migration complete:\n${stdout}` }] };
  } catch (e) {
    const msg = e instanceof Error ? e.message : String(e);
    return { content: [{ type: 'text', text: `❌ Migration failed: ${msg}` }] };
  }
};
```

</details>

<details>
<summary>💡 Hint 2: The migration command flags</summary>

`--allow-dirty` prevents the migration from failing when the git working tree has uncommitted changes. This is useful during development.

You can also add `--force` if packages have peer dependency conflicts, but use it with caution.

</details>

<details>
<summary>💡 Hint 3: Cursor doesn't see the new tool</summary>

After rebuilding (`npm run build.angular-mcp`), you must reload Cursor's window for it to re-read `mcp.json` and reconnect to the server.

Use **Cmd+Shift+P → Developer: Reload Window**.

</details>

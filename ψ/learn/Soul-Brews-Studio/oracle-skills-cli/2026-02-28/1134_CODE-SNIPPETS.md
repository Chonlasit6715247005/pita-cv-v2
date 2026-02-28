# Oracle Skills CLI Code Snippets

## Main CLI Entry (commander setup)
```typescript
import { program } from 'commander';
import * as p from '@clack/prompts';

program
  .command('install', { isDefault: true })
  .description('Install Oracle skills to agents')
  .option('-g, --global', 'Install to user directory instead of project')
  .option('-a, --agent <agents...>', 'Target specific agents')
  .action(async (options) => {
    p.intro(`🔮 Oracle Skills Installer`);
    // Detection logic here...
    await installSkills(targetAgents, {...options});
  });
```

## Agent Detection Pattern
This snippet is how the CLI knows which IDEs/agents the user has:
```typescript
export function detectInstalledAgents(): string[] {
  return Object.entries(agents)
    .filter(([_, config]) => config.detectInstalled())
    .map(([key, _]) => key);
}
```

## OS/Shell Specific Handling
It allows fallback from Bun shell commands to native Node operations:
```typescript
const shellMode: ShellMode = options.shell ? 'shell'
  : options.noShell ? 'no-shell'
  : 'auto';
```

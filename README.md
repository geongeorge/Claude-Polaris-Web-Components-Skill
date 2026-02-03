# Polaris Web Components Skill for Claude Code

A [Claude Code skill](https://code.claude.com/docs/en/skills) that helps you build Shopify app interfaces using Polaris Web Components and migrate from Polaris React components.

## Features

- **Create UI templates** - Generate complete, working HTML for common Shopify app patterns
- **Migrate from React** - Convert Polaris React components to Web Components with side-by-side examples
- **Component reference** - Quick access to all component APIs and best practices
- **Ready-to-use templates** - Dashboard, settings page, data table, and form templates

## Installation

### Option 1: Personal skill (all projects)

```bash
# Clone to your personal skills directory
git clone https://github.com/geongeorge/Claude-Polaris-Web-Components-Skill.git ~/.claude/skills/polaris-web-components
```

### Option 2: Project skill (this project only)

```bash
# Clone to your project's .claude directory
git clone https://github.com/geongeorge/Claude-Polaris-Web-Components-Skill.git .claude/skills/polaris-web-components
```

### Option 3: Manual installation

1. Create the skill directory:
   ```bash
   mkdir -p ~/.claude/skills/polaris-web-components
   ```

2. Copy the `skills/polaris-web-components` folder contents to the directory

## Usage

### Invoke directly

```
/polaris how do I create a modal?
/polaris migrate this Button component
/polaris create a customer list page
```

### Let Claude invoke automatically

Claude will automatically use this skill when you:
- Ask about Polaris web components (`s-button`, `s-modal`, etc.)
- Request help building Shopify app interfaces
- Ask to migrate React components to web components

### Example prompts

**Creating UI:**
```
Create a dashboard page with stats cards and a recent orders table
```

**Migrating code:**
```
Migrate this React code to web components:
<Button primary onClick={handleSave}>Save</Button>
```

**Component questions:**
```
How do I use the command pattern to control modals?
What's the difference between s-section and s-box?
```

## Skill Contents

```
skills/polaris-web-components/
├── SKILL.md           # Main skill definition
├── reference.md       # Complete component API reference
├── migration.md       # React to Web Components guide
├── templates/         # Ready-to-use UI templates
│   ├── dashboard.html
│   ├── form-page.html
│   ├── page-with-table.html
│   └── settings-page.html
└── examples/          # Component usage examples
    ├── buttons.html
    ├── forms.html
    └── overlays.html
```

## Quick Reference

### Component Naming

All Polaris web components use the `s-` prefix:
- `s-button`, `s-modal`, `s-table`, `s-text-field`, etc.

### Key Patterns

**Command Pattern** (modals, popovers):
```html
<s-button commandFor="modal-id">Open</s-button>
<s-modal id="modal-id" heading="Title">
  <s-button slot="primary-action" commandFor="modal-id" command="--hide">Close</s-button>
</s-modal>
```

**Interest Pattern** (tooltips):
```html
<s-tooltip id="tip">Help text</s-tooltip>
<s-button interestFor="tip">?</s-button>
```

**Slots** (action placement):
```html
<s-page heading="Products">
  <s-button slot="primary-action" variant="primary">Add</s-button>
  <s-button slot="secondary-actions">Import</s-button>
</s-page>
```

### Common Migrations

| React | Web Component |
|-------|---------------|
| `<Button primary>` | `<s-button variant="primary">` |
| `<Button destructive>` | `<s-button variant="primary" tone="critical">` |
| `<Card>` | `<s-section>` |
| `<Page title="...">` | `<s-page heading="...">` |
| `<BlockStack>` | `<s-stack direction="block">` |
| `<InlineStack>` | `<s-stack direction="inline">` |
| `helpText` prop | `details` attribute |
| `url` prop | `href` attribute |

## Documentation

- [reference.md](skills/polaris-web-components/reference.md) - Complete component API
- [migration.md](skills/polaris-web-components/migration.md) - React migration guide
- [Polaris Web Components (Shopify)](https://shopify.dev/docs/api/app-home/polaris-web-components)
- [Polaris Design System](https://polaris.shopify.com)
- [Claude Code Skills](https://code.claude.com/docs/en/skills)

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.

## License

MIT License - See [LICENSE](LICENSE) for details.

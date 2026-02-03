# React to Web Components Migration Guide

Complete guide for migrating from Polaris React components to Polaris Web Components.

---

## Overview

Polaris Web Components use the `s-` prefix and are designed as standard HTML custom elements. Unlike React components that use JSX syntax with props, Web Components use HTML attributes and slots.

### Key Differences

| Aspect | React Components | Web Components |
|--------|-----------------|----------------|
| Syntax | JSX with props | HTML with attributes |
| Naming | PascalCase (`Button`) | kebab-case with `s-` prefix (`s-button`) |
| Children | `children` prop | Default slot |
| Named sections | Props or compound components | Named slots |
| Event Handlers | `onClick`, `onChange` | `onclick`, `onchange` or addEventListener |
| Boolean Props | `disabled={true}` | `disabled` (presence = true) |
| Conditional Rendering | JSX expressions | CSS `display` or `hidden` attribute |
| State Management | `open={state}` | `commandFor`/`command` pattern |

---

## Component Migration Reference

### Button

**React:**
```jsx
<Button>Default</Button>
<Button primary>Primary</Button>
<Button destructive>Delete</Button>
<Button plain>Plain</Button>
<Button loading>Loading</Button>
<Button disabled>Disabled</Button>
<Button onClick={() => save()}>Save</Button>
<Button url="https://shopify.com">Link</Button>
```

**Web Component:**
```html
<s-button>Default</s-button>
<s-button variant="primary">Primary</s-button>
<s-button variant="primary" tone="critical">Delete</s-button>
<s-button variant="tertiary">Plain</s-button>
<s-button loading>Loading</s-button>
<s-button disabled>Disabled</s-button>
<s-button onclick="save()">Save</s-button>
<s-button href="https://shopify.com">Link</s-button>
```

**Key changes:**
- `primary` prop → `variant="primary"`
- `destructive` prop → `variant="primary" tone="critical"`
- `plain` prop → `variant="tertiary"`
- `onClick` → `onclick` or addEventListener
- `url` → `href`

---

### ButtonGroup

**React:**
```jsx
<ButtonGroup>
  <Button>Cancel</Button>
  <Button primary>Save</Button>
</ButtonGroup>
```

**Web Component:**
```html
<s-button-group>
  <s-button slot="secondary-actions">Cancel</s-button>
  <s-button slot="primary-action" variant="primary">Save</s-button>
</s-button-group>
```

**Key changes:**
- Use `slot="primary-action"` and `slot="secondary-actions"` for button placement

---

### Link

**React:**
```jsx
<Link url="https://shopify.com">Visit</Link>
<Link url="/products" external>Products</Link>
```

**Web Component:**
```html
<s-link href="https://shopify.com">Visit</s-link>
<s-link href="/products" target="_blank">Products</s-link>
```

**Key changes:**
- `url` → `href`
- `external` → `target="_blank"`

---

### Card → Section

**React:**
```jsx
<Card>
  <p>Default card</p>
</Card>
<Card sectioned>
  <p>Sectioned card</p>
</Card>
<Card title="Customer">
  <p>Card with title</p>
</Card>
```

**Web Component:**
```html
<s-section>
  <p>Default section</p>
</s-section>
<s-section padding="base">
  <p>Sectioned content</p>
</s-section>
<s-section heading="Customer">
  <p>Section with heading</p>
</s-section>
```

**Key changes:**
- `Card` component → `s-section`
- `title` prop → `heading` attribute
- `sectioned` prop → `padding="base"`

---

### Page

**React:**
```jsx
<Page title="Products">
  <p>Content</p>
</Page>

<Page
  title="Product details"
  primaryAction={{ content: 'Save', onAction: handleSave }}
  secondaryActions={[{ content: 'Delete', destructive: true }]}
>
  <p>Content</p>
</Page>
```

**Web Component:**
```html
<s-page heading="Products">
  <p>Content</p>
</s-page>

<s-page heading="Product details">
  <s-button slot="primary-action" variant="primary" onclick="handleSave()">Save</s-button>
  <s-button slot="secondary-actions" tone="critical">Delete</s-button>
  <p>Content</p>
</s-page>
```

**Key changes:**
- `title` → `heading`
- `primaryAction` object → `slot="primary-action"` button
- `secondaryActions` array → `slot="secondary-actions"` buttons

---

### Layout → Grid

**React:**
```jsx
<Layout>
  <Layout.Section>
    <p>Main content</p>
  </Layout.Section>
  <Layout.Section secondary>
    <p>Sidebar</p>
  </Layout.Section>
</Layout>
```

**Web Component:**
```html
<s-grid gridTemplateColumns="2fr 1fr" gap="base">
  <s-grid-item>
    <p>Main content</p>
  </s-grid-item>
  <s-grid-item>
    <p>Sidebar</p>
  </s-grid-item>
</s-grid>
```

**Key changes:**
- Use CSS Grid syntax for layout control
- More flexible than predefined sections

---

### BlockStack / InlineStack → Stack

**React:**
```jsx
<BlockStack gap="400">
  <p>Item 1</p>
  <p>Item 2</p>
</BlockStack>

<InlineStack gap="400">
  <Button>Button 1</Button>
  <Button>Button 2</Button>
</InlineStack>
```

**Web Component:**
```html
<s-stack direction="block" gap="base">
  <p>Item 1</p>
  <p>Item 2</p>
</s-stack>

<s-stack direction="inline" gap="base">
  <s-button>Button 1</s-button>
  <s-button>Button 2</s-button>
</s-stack>
```

**Key changes:**
- `BlockStack` → `<s-stack direction="block">`
- `InlineStack` → `<s-stack direction="inline">`
- Gap tokens simplified to `base`, `small`, etc.

---

### Badge

**React:**
```jsx
<Badge>Default</Badge>
<Badge status="info">Draft</Badge>
<Badge status="success">Active</Badge>
<Badge status="warning">On hold</Badge>
<Badge status="critical">Error</Badge>
```

**Web Component:**
```html
<s-badge>Default</s-badge>
<s-badge tone="info">Draft</s-badge>
<s-badge tone="success">Active</s-badge>
<s-badge tone="warning">On hold</s-badge>
<s-badge tone="critical">Error</s-badge>
```

**Key changes:**
- `status` → `tone`

---

### Banner

**React:**
```jsx
<Banner title="Order archived" onDismiss={() => {}}>
  <p>This order was archived.</p>
</Banner>
<Banner title="Error" status="critical">
  <p>Something went wrong.</p>
</Banner>
```

**Web Component:**
```html
<s-banner heading="Order archived" dismissible>
  This order was archived.
</s-banner>
<s-banner heading="Error" tone="critical">
  Something went wrong.
</s-banner>
```

**Key changes:**
- `title` → `heading`
- `status` → `tone`
- `onDismiss` → `dismissible` attribute

---

### TextField

**React:**
```jsx
<TextField
  label="Store name"
  value={value}
  onChange={handleChange}
  placeholder="Enter name"
  helpText="Displayed on storefront"
  error="Required field"
/>
```

**Web Component:**
```html
<s-text-field
  label="Store name"
  value="Current value"
  placeholder="Enter name"
  details="Displayed on storefront"
  error="Required field"
/>
```

**Key changes:**
- `helpText` → `details`
- `onChange` → `oninput` or addEventListener('input', ...)

---

### TextField multiline → TextArea

**React:**
```jsx
<TextField
  label="Description"
  value={value}
  onChange={handleChange}
  multiline={4}
/>
```

**Web Component:**
```html
<s-text-area
  label="Description"
  value="Current value"
/>
```

**Key changes:**
- Separate component for multiline input

---

### Select

**React:**
```jsx
<Select
  label="Country"
  options={[
    { label: 'United States', value: 'us' },
    { label: 'Canada', value: 'ca' },
  ]}
  value={selected}
  onChange={handleChange}
/>
```

**Web Component:**
```html
<s-select label="Country">
  <option value="us">United States</option>
  <option value="ca">Canada</option>
</s-select>
```

**Key changes:**
- Use native `<option>` elements instead of `options` prop

---

### Checkbox

**React:**
```jsx
<Checkbox
  label="I agree"
  checked={checked}
  onChange={handleChange}
/>
```

**Web Component:**
```html
<s-checkbox
  label="I agree"
  checked
/>
```

---

### ChoiceList / RadioButton

**React:**
```jsx
<ChoiceList
  title="Company name"
  choices={[
    { label: 'Hidden', value: 'hidden' },
    { label: 'Optional', value: 'optional' },
    { label: 'Required', value: 'required' },
  ]}
  selected={selected}
  onChange={handleChange}
/>

<RadioButton
  label="Option A"
  checked={value === 'a'}
  id="a"
  name="options"
  onChange={handleChange}
/>
```

**Web Component:**
```html
<s-choice-list label="Company name" name="company">
  <s-choice value="hidden">Hidden</s-choice>
  <s-choice value="optional">Optional</s-choice>
  <s-choice value="required">Required</s-choice>
</s-choice-list>
```

**Key changes:**
- `title` → `label`
- `choices` array → `<s-choice>` children
- RadioButton uses same component (single select mode)

---

### SettingToggle → Switch

**React:**
```jsx
<SettingToggle
  action={{
    content: enabled ? 'Disable' : 'Enable',
    onAction: handleToggle,
  }}
  enabled={enabled}
>
  This feature is {enabled ? 'enabled' : 'disabled'}.
</SettingToggle>
```

**Web Component:**
```html
<s-switch
  label="Enable feature"
  details="This feature controls..."
  checked
/>
```

**Key changes:**
- Simpler API with label and details
- `enabled` → `checked`

---

### Modal

**React:**
```jsx
<Modal
  open={active}
  onClose={handleClose}
  title="Confirm"
  primaryAction={{
    content: 'Save',
    onAction: handleSave,
  }}
  secondaryActions={[
    { content: 'Cancel', onAction: handleClose },
  ]}
>
  <Modal.Section>
    <p>Modal content</p>
  </Modal.Section>
</Modal>
```

**Web Component:**
```html
<s-button commandFor="my-modal">Open</s-button>

<s-modal id="my-modal" heading="Confirm">
  <s-paragraph>Modal content</s-paragraph>

  <s-button slot="secondary-actions" commandFor="my-modal" command="--hide">
    Cancel
  </s-button>
  <s-button slot="primary-action" variant="primary" commandFor="my-modal" command="--hide">
    Save
  </s-button>
</s-modal>
```

**Key changes:**
- `open` state → `commandFor`/`command` pattern
- `title` → `heading`
- Action objects → slotted buttons with commands

---

### Popover

**React:**
```jsx
<Popover
  active={popoverActive}
  activator={<Button>Options</Button>}
  onClose={togglePopover}
>
  <ActionList items={[{ content: 'Import' }, { content: 'Export' }]} />
</Popover>
```

**Web Component:**
```html
<s-button commandFor="options-popover">Options</s-button>

<s-popover id="options-popover">
  <s-stack direction="block">
    <s-button variant="tertiary">Import</s-button>
    <s-button variant="tertiary">Export</s-button>
  </s-stack>
</s-popover>
```

**Key changes:**
- `active` state → `commandFor` pattern
- Activator separate from popover content

---

### Tooltip

**React:**
```jsx
<Tooltip content="Helpful info">
  <Button>Hover me</Button>
</Tooltip>
```

**Web Component:**
```html
<s-tooltip id="my-tooltip">Helpful info</s-tooltip>
<s-button interestFor="my-tooltip">Hover me</s-button>
```

**Key changes:**
- `content` prop → tooltip as separate element
- Uses `interestFor` pattern instead of wrapping

---

### Avatar

**React:**
```jsx
<Avatar customer name="John Doe" />
<Avatar customer initials="JD" />
<Avatar source="https://example.com/avatar.jpg" />
```

**Web Component:**
```html
<s-avatar alt="John Doe" initials="JD" />
<s-avatar alt="Jane Smith" src="https://example.com/avatar.jpg" />
```

**Key changes:**
- `name` → `alt`
- `source` → `src`

---

### Icon

**React:**
```jsx
import { HomeMajor, OrdersMajor } from '@shopify/polaris-icons';

<Icon source={HomeMajor} />
<Icon source={OrdersMajor} color="success" />
```

**Web Component:**
```html
<s-icon type="home" />
<s-icon type="order" tone="success" />
```

**Key changes:**
- No imports needed
- `source` → `type` with string value
- `color` → `tone`

---

### Thumbnail

**React:**
```jsx
<Thumbnail
  source="https://example.com/image.jpg"
  alt="Product"
  size="small"
/>
```

**Web Component:**
```html
<s-thumbnail
  src="https://example.com/image.jpg"
  alt="Product"
  size="small"
/>
```

**Key changes:**
- `source` → `src`

---

### DataTable → Table

**React:**
```jsx
<DataTable
  columnContentTypes={['text', 'text', 'numeric']}
  headings={['Name', 'Email', 'Orders']}
  rows={[
    ['John', 'john@example.com', '23'],
    ['Jane', 'jane@example.com', '15'],
  ]}
/>
```

**Web Component:**
```html
<s-table>
  <s-table-header-row>
    <s-table-header>Name</s-table-header>
    <s-table-header>Email</s-table-header>
    <s-table-header format="numeric">Orders</s-table-header>
  </s-table-header-row>
  <s-table-body>
    <s-table-row>
      <s-table-cell>John</s-table-cell>
      <s-table-cell>john@example.com</s-table-cell>
      <s-table-cell>23</s-table-cell>
    </s-table-row>
    <s-table-row>
      <s-table-cell>Jane</s-table-cell>
      <s-table-cell>jane@example.com</s-table-cell>
      <s-table-cell>15</s-table-cell>
    </s-table-row>
  </s-table-body>
</s-table>
```

**Key changes:**
- Declarative HTML structure
- `columnContentTypes` → `format="numeric"` on headers

---

### List

**React:**
```jsx
<List>
  <List.Item>First</List.Item>
  <List.Item>Second</List.Item>
</List>
<List type="number">
  <List.Item>First</List.Item>
  <List.Item>Second</List.Item>
</List>
```

**Web Component:**
```html
<s-unordered-list>
  <li>First</li>
  <li>Second</li>
</s-unordered-list>

<s-ordered-list>
  <li>First</li>
  <li>Second</li>
</s-ordered-list>
```

**Key changes:**
- Separate components for ordered/unordered
- Use native `<li>` elements

---

### ActionList → Menu

**React:**
```jsx
<ActionList
  items={[
    { content: 'Import', onAction: handleImport },
    { content: 'Export', onAction: handleExport },
    { content: 'Delete', destructive: true, onAction: handleDelete },
  ]}
/>
```

**Web Component:**
```html
<s-menu id="actions-menu" accessibilityLabel="Actions">
  <s-button icon="incoming">Import</s-button>
  <s-button icon="outgoing">Export</s-button>
  <s-button icon="delete" tone="critical">Delete</s-button>
</s-menu>
```

**Key changes:**
- `items` array → button children
- `destructive` → `tone="critical"`

---

## Quick Reference Table

| React Component | Web Component | Key Changes |
|-----------------|---------------|-------------|
| `Button` | `s-button` | `primary`→`variant`, `destructive`→`tone`, `url`→`href` |
| `ButtonGroup` | `s-button-group` | Use slots for actions |
| `Link` | `s-link` | `url`→`href`, `external`→`target` |
| `Card` | `s-section` | Different component |
| `Page` | `s-page` | `title`→`heading`, use slots for actions |
| `Layout` | `s-grid` | CSS Grid syntax |
| `BlockStack` | `s-stack direction="block"` | Unified component |
| `InlineStack` | `s-stack direction="inline"` | Unified component |
| `Badge` | `s-badge` | `status`→`tone` |
| `Banner` | `s-banner` | `title`→`heading`, `status`→`tone` |
| `TextField` | `s-text-field` | `helpText`→`details` |
| `TextField multiline` | `s-text-area` | Separate component |
| `Select` | `s-select` | Use `<option>` children |
| `Checkbox` | `s-checkbox` | Same API |
| `ChoiceList` | `s-choice-list` | Use `<s-choice>` children |
| `RadioButton` | `s-choice-list` | Single-select mode |
| `SettingToggle` | `s-switch` | Simpler API |
| `Modal` | `s-modal` | Command pattern |
| `Popover` | `s-popover` | Command pattern |
| `Tooltip` | `s-tooltip` | Interest pattern |
| `Avatar` | `s-avatar` | `source`→`src` |
| `Icon` | `s-icon` | `source`→`type` |
| `Thumbnail` | `s-thumbnail` | `source`→`src` |
| `DataTable` | `s-table` | Declarative HTML |
| `List` | `s-unordered-list` / `s-ordered-list` | Separate components |
| `ActionList` | `s-menu` | Button children |

---

## References

- [Polaris Web Components Documentation](https://shopify.dev/docs/api/app-home/polaris-web-components)
- [Polaris React Components](https://polaris-react.shopify.com/components)

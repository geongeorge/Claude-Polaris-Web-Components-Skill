# Polaris React to Web Components Migration Guide

This guide provides comprehensive instructions for migrating from Polaris React components to Polaris Web Components. It includes component mappings, syntax differences, and practical examples to help you transition your Shopify app interfaces.

---

## Overview

Polaris Web Components use the `s-` prefix and are designed as standard HTML custom elements. Unlike React components that use JSX syntax with props, Web Components use HTML attributes and slots for configuration.

### Key Differences

| Aspect | React Components | Web Components |
|--------|-----------------|----------------|
| Syntax | JSX with props | HTML with attributes |
| Naming | PascalCase (e.g., `Button`) | kebab-case with `s-` prefix (e.g., `s-button`) |
| Children | `children` prop | Default slot |
| Event Handlers | `onClick`, `onChange` | `onclick`, `onchange` or `addEventListener` |
| Boolean Props | `disabled={true}` | `disabled` (presence = true) |
| Conditional Rendering | JSX expressions | CSS `display` or `hidden` attribute |

---

## Component Migration Reference

### Actions

#### Button

**React:**
```jsx
<Button>Add product</Button>
<Button primary>Save</Button>
<Button destructive>Delete</Button>
<Button plain>Cancel</Button>
<Button loading>Processing</Button>
<Button disabled>Unavailable</Button>
<Button onClick={() => console.log('clicked')}>Click me</Button>
<Button url="https://shopify.com">Visit Shopify</Button>
```

**Web Component:**
```html
<s-button>Add product</s-button>
<s-button variant="primary">Save</s-button>
<s-button variant="primary" tone="critical">Delete</s-button>
<s-button variant="tertiary">Cancel</s-button>
<s-button loading>Processing</s-button>
<s-button disabled>Unavailable</s-button>
<s-button onclick="console.log('clicked')">Click me</s-button>
<s-button href="https://shopify.com">Visit Shopify</s-button>
```

#### ButtonGroup

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

#### Link

**React:**
```jsx
<Link url="https://shopify.com">Visit Shopify</Link>
<Link url="/products" external>Products</Link>
```

**Web Component:**
```html
<s-link href="https://shopify.com">Visit Shopify</s-link>
<s-link href="/products" target="_blank">Products</s-link>
```

---

### Layout and Structure

#### Box

**React:**
```jsx
<Box background="bg-fill-info">
  <Placeholder label="Content inside a box" />
</Box>
<Box padding="400" background="bg-surface-secondary">
  Content with padding
</Box>
```

**Web Component:**
```html
<s-box background="info">
  Content inside a box
</s-box>
<s-box padding="base" background="subdued">
  Content with padding
</s-box>
```

#### Card

**React:**
```jsx
<Card>
  <p>Default card content</p>
</Card>
<Card sectioned>
  <p>Sectioned card content</p>
</Card>
```

**Web Component:**
```html
<s-section>
  <p>Default card content</p>
</s-section>
<s-section padding="base">
  <p>Sectioned card content</p>
</s-section>
```

#### Page

**React:**
```jsx
<Page title="Products">
  <p>Page content</p>
</Page>
<Page
  title="Product details"
  primaryAction={{ content: 'Save', onAction: handleSave }}
  secondaryActions={[{ content: 'Delete', destructive: true }]}
>
  <p>Page content</p>
</Page>
```

**Web Component:**
```html
<s-page heading="Products">
  <p>Page content</p>
</s-page>
<s-page heading="Product details">
  <s-button slot="primary-action" variant="primary">Save</s-button>
  <s-button slot="secondary-actions" tone="critical">Delete</s-button>
  <p>Page content</p>
</s-page>
```

#### Layout / Grid

**React:**
```jsx
<Layout>
  <Layout.Section>
    <p>Main content</p>
  </Layout.Section>
  <Layout.Section secondary>
    <p>Sidebar content</p>
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
    <p>Sidebar content</p>
  </s-grid-item>
</s-grid>
```

#### Stack / BlockStack / InlineStack

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

#### Divider

**React:**
```jsx
<Divider />
```

**Web Component:**
```html
<s-divider />
```

---

### Feedback and Status Indicators

#### Badge

**React:**
```jsx
<Badge>Fulfilled</Badge>
<Badge status="info">Draft</Badge>
<Badge status="success">Active</Badge>
<Badge status="warning">On hold</Badge>
<Badge status="critical">Action required</Badge>
```

**Web Component:**
```html
<s-badge>Fulfilled</s-badge>
<s-badge tone="info">Draft</s-badge>
<s-badge tone="success">Active</s-badge>
<s-badge tone="warning">On hold</s-badge>
<s-badge tone="critical">Action required</s-badge>
```

#### Banner

**React:**
```jsx
<Banner title="Order archived" onDismiss={() => {}}>
  <p>This order was archived on March 7, 2017 at 3:12pm EDT.</p>
</Banner>
<Banner title="Error" status="critical">
  <p>There was an error processing your request.</p>
</Banner>
```

**Web Component:**
```html
<s-banner heading="Order archived" dismissible>
  This order was archived on March 7, 2017 at 3:12pm EDT.
</s-banner>
<s-banner heading="Error" tone="critical">
  There was an error processing your request.
</s-banner>
```

#### Spinner

**React:**
```jsx
<Spinner accessibilityLabel="Loading" size="large" />
```

**Web Component:**
```html
<s-spinner accessibilityLabel="Loading" size="large-100" />
```

---

### Forms

#### TextField

**React:**
```jsx
<TextField
  label="Store name"
  value={value}
  onChange={handleChange}
  placeholder="Enter store name"
  helpText="This will be displayed on your storefront"
  error="Store name is required"
/>
```

**Web Component:**
```html
<s-text-field
  label="Store name"
  value="Jaded Pixel"
  placeholder="Enter store name"
  details="This will be displayed on your storefront"
  error="Store name is required"
/>
```

#### TextArea (Multi-line TextField)

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
  value="Product description"
/>
```

#### Select

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

#### Checkbox

**React:**
```jsx
<Checkbox
  label="I agree to the terms"
  checked={checked}
  onChange={handleChange}
/>
```

**Web Component:**
```html
<s-checkbox
  label="I agree to the terms"
  checked
/>
```

#### ChoiceList

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
```

**Web Component:**
```html
<s-choice-list label="Company name" name="company">
  <s-choice value="hidden">Hidden</s-choice>
  <s-choice value="optional">Optional</s-choice>
  <s-choice value="required">Required</s-choice>
</s-choice-list>
```

#### RadioButton

**React:**
```jsx
<RadioButton
  label="Accounts are disabled"
  checked={value === 'disabled'}
  id="disabled"
  name="accounts"
  onChange={handleChange}
/>
```

**Web Component:**
```html
<s-choice-list label="Account status" name="accounts">
  <s-choice value="disabled">Accounts are disabled</s-choice>
  <s-choice value="enabled">Accounts are enabled</s-choice>
</s-choice-list>
```

#### DropZone

**React:**
```jsx
<DropZone onDrop={handleDrop} accept="image/*">
  <DropZone.FileUpload />
</DropZone>
```

**Web Component:**
```html
<s-drop-zone
  label="Upload"
  accept=".jpg,.png,.gif"
  multiple
/>
```

#### Switch (Setting Toggle)

**React:**
```jsx
<SettingToggle
  action={{
    content: enabled ? 'Disable' : 'Enable',
    onAction: handleToggle,
  }}
  enabled={enabled}
>
  This setting is {enabled ? 'enabled' : 'disabled'}.
</SettingToggle>
```

**Web Component:**
```html
<s-switch
  label="Enable feature"
  details="This setting controls the feature"
  checked
/>
```

---

### Images and Icons

#### Avatar

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

#### Icon

**React:**
```jsx
import { HomeMajor, OrdersMajor, ProductsMajor } from '@shopify/polaris-icons';

<Icon source={HomeMajor} />
<Icon source={OrdersMajor} color="success" />
<Icon source={ProductsMajor} />
```

**Web Component:**
```html
<s-icon type="home" />
<s-icon type="order" tone="success" />
<s-icon type="product" />
```

#### Thumbnail

**React:**
```jsx
<Thumbnail
  source="https://example.com/image.jpg"
  alt="Product image"
  size="small"
/>
```

**Web Component:**
```html
<s-thumbnail
  src="https://example.com/image.jpg"
  alt="Product image"
  size="small"
/>
```

---

### Overlays

#### Modal

**React:**
```jsx
<Modal
  open={active}
  onClose={handleClose}
  title="Reach more shoppers"
  primaryAction={{
    content: 'Add Instagram',
    onAction: handleAdd,
  }}
  secondaryActions={[
    {
      content: 'Learn more',
      onAction: handleLearnMore,
    },
  ]}
>
  <Modal.Section>
    <p>Use Instagram to reach more shoppers.</p>
  </Modal.Section>
</Modal>
```

**Web Component:**
```html
<s-button commandFor="instagram-modal">Open Modal</s-button>
<s-modal id="instagram-modal" heading="Reach more shoppers">
  <s-paragraph>Use Instagram to reach more shoppers.</s-paragraph>
  <s-button slot="secondary-actions" commandFor="instagram-modal" command="--hide">
    Learn more
  </s-button>
  <s-button slot="primary-action" variant="primary" commandFor="instagram-modal" command="--hide">
    Add Instagram
  </s-button>
</s-modal>
```

#### Popover

**React:**
```jsx
<Popover
  active={popoverActive}
  activator={activator}
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

#### Tooltip

**React:**
```jsx
<Tooltip content="This order has shipping labels.">
  <Link>Order #1001</Link>
</Tooltip>
```

**Web Component:**
```html
<s-tooltip id="order-tooltip">This order has shipping labels.</s-tooltip>
<s-link interestFor="order-tooltip" href="/orders/1001">Order #1001</s-link>
```

---

### Typography

#### Text

**React:**
```jsx
<Text as="p">Your store is ready to use.</Text>
<Text as="span" fontWeight="bold">Important</Text>
<Text as="p" variant="headingMd">Heading</Text>
```

**Web Component:**
```html
<s-paragraph>Your store is ready to use.</s-paragraph>
<s-text type="strong">Important</s-text>
<s-heading>Heading</s-heading>
```

#### Heading

**React:**
```jsx
<Heading>Online store dashboard</Heading>
```

**Web Component:**
```html
<s-heading>Online store dashboard</s-heading>
```

---

### Tables

#### DataTable / IndexTable

**React:**
```jsx
<DataTable
  columnContentTypes={['text', 'text', 'numeric', 'text']}
  headings={['Name', 'Email', 'Orders', 'Phone']}
  rows={[
    ['John Smith', 'john@example.com', '23', '123-456-7890'],
    ['Jane Johnson', 'jane@example.com', '15', '234-567-8901'],
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
    <s-table-header>Phone</s-table-header>
  </s-table-header-row>
  <s-table-body>
    <s-table-row>
      <s-table-cell>John Smith</s-table-cell>
      <s-table-cell>john@example.com</s-table-cell>
      <s-table-cell>23</s-table-cell>
      <s-table-cell>123-456-7890</s-table-cell>
    </s-table-row>
    <s-table-row>
      <s-table-cell>Jane Johnson</s-table-cell>
      <s-table-cell>jane@example.com</s-table-cell>
      <s-table-cell>15</s-table-cell>
      <s-table-cell>234-567-8901</s-table-cell>
    </s-table-row>
  </s-table-body>
</s-table>
```

---

### Lists

#### List

**React:**
```jsx
<List>
  <List.Item>First item</List.Item>
  <List.Item>Second item</List.Item>
  <List.Item>Third item</List.Item>
</List>
<List type="number">
  <List.Item>First item</List.Item>
  <List.Item>Second item</List.Item>
</List>
```

**Web Component:**
```html
<s-unordered-list>
  <li>First item</li>
  <li>Second item</li>
  <li>Third item</li>
</s-unordered-list>
<s-ordered-list>
  <li>First item</li>
  <li>Second item</li>
</s-ordered-list>
```

#### ActionList (Menu)

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

---

## Event Handling

### React Event Handlers

```jsx
<Button onClick={() => console.log('clicked')}>Click me</Button>
<TextField onChange={(value) => setValue(value)} />
```

### Web Component Event Handlers

**Inline:**
```html
<s-button onclick="console.log('clicked')">Click me</s-button>
```

**JavaScript:**
```html
<s-button id="my-button">Click me</s-button>
<s-text-field id="my-field" label="Name"></s-text-field>

<script>
  document.getElementById('my-button').addEventListener('click', () => {
    console.log('clicked');
  });
  
  document.getElementById('my-field').addEventListener('input', (event) => {
    console.log('Value:', event.currentTarget.value);
  });
</script>
```

**React with Web Components:**
```jsx
<s-button onClick={() => console.log('clicked')}>Click me</s-button>
<s-text-field
  label="Name"
  onInput={(event) => setValue(event.currentTarget.value)}
/>
```

---

## Command Pattern for Overlays

Web Components use the `commandFor` and `command` attributes to control overlays like modals and popovers.

### Opening and Closing Modals

```html
<!-- Button to open modal -->
<s-button commandFor="my-modal">Open Modal</s-button>

<!-- Modal with close buttons -->
<s-modal id="my-modal" heading="My Modal">
  <s-paragraph>Modal content here.</s-paragraph>
  
  <!-- Close button using command -->
  <s-button slot="secondary-actions" commandFor="my-modal" command="--hide">
    Cancel
  </s-button>
  <s-button slot="primary-action" variant="primary" commandFor="my-modal" command="--hide">
    Save
  </s-button>
</s-modal>
```

### Command Values

| Command | Description |
|---------|-------------|
| `--auto` | Default action for the target component |
| `--show` | Shows the target component |
| `--hide` | Hides the target component |
| `--toggle` | Toggles the target component visibility |

---

## Quick Reference Table

| React Component | Web Component | Notes |
|-----------------|---------------|-------|
| `<Button>` | `<s-button>` | Use `variant` instead of `primary`/`plain` |
| `<ButtonGroup>` | `<s-button-group>` | Use slots for primary/secondary actions |
| `<Link>` | `<s-link>` | Use `href` instead of `url` |
| `<Box>` | `<s-box>` | Similar props, different naming |
| `<Card>` | `<s-section>` | Card replaced by Section |
| `<Page>` | `<s-page>` | Use `heading` instead of `title` |
| `<Layout>` | `<s-grid>` | Use CSS Grid syntax |
| `<BlockStack>` | `<s-stack direction="block">` | — |
| `<InlineStack>` | `<s-stack direction="inline">` | — |
| `<Divider>` | `<s-divider>` | — |
| `<Badge>` | `<s-badge>` | Use `tone` instead of `status` |
| `<Banner>` | `<s-banner>` | Use `heading` instead of `title` |
| `<Spinner>` | `<s-spinner>` | — |
| `<TextField>` | `<s-text-field>` | Use `details` instead of `helpText` |
| `<TextField multiline>` | `<s-text-area>` | Separate component |
| `<Select>` | `<s-select>` | Use native `<option>` elements |
| `<Checkbox>` | `<s-checkbox>` | — |
| `<ChoiceList>` | `<s-choice-list>` | Use `<s-choice>` children |
| `<RadioButton>` | `<s-choice-list>` | Use single-select ChoiceList |
| `<DropZone>` | `<s-drop-zone>` | — |
| `<SettingToggle>` | `<s-switch>` | — |
| `<Avatar>` | `<s-avatar>` | Use `src` instead of `source` |
| `<Icon>` | `<s-icon>` | Use `type` instead of `source` |
| `<Thumbnail>` | `<s-thumbnail>` | Use `src` instead of `source` |
| `<Modal>` | `<s-modal>` | Use `commandFor` pattern |
| `<Popover>` | `<s-popover>` | Use `commandFor` pattern |
| `<Tooltip>` | `<s-tooltip>` | Use `interestFor` pattern |
| `<Text>` | `<s-text>` / `<s-paragraph>` | Use appropriate component |
| `<Heading>` | `<s-heading>` | — |
| `<DataTable>` | `<s-table>` | Use table sub-components |
| `<List>` | `<s-unordered-list>` / `<s-ordered-list>` | — |
| `<ActionList>` | `<s-menu>` | — |

---

## References

- [Polaris Web Components Documentation](https://shopify.dev/docs/api/app-home/polaris-web-components)
- [Polaris React Components](https://polaris-react.shopify.com/components)

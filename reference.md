# Polaris Web Components Reference

Complete API reference for all Shopify Polaris Web Components.

---

## Actions

### s-button

Triggers actions or events. Can function as links.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `variant` | `'auto' \| 'primary' \| 'secondary' \| 'tertiary'` | `'auto'` | Visual appearance |
| `tone` | `'critical' \| 'auto' \| 'neutral'` | `'auto'` | Button tone |
| `icon` | `string` | — | Icon type to display |
| `loading` | `boolean` | `false` | Shows loading indicator |
| `disabled` | `boolean` | `false` | Disables the button |
| `href` | `string` | — | URL to link to |
| `target` | `'auto' \| '_blank' \| '_self'` | `'auto'` | Link target |
| `type` | `'button' \| 'reset' \| 'submit'` | `'button'` | Button behavior |
| `commandFor` | `string` | — | ID of element to control |
| `command` | `'--auto' \| '--show' \| '--hide' \| '--toggle'` | `'--auto'` | Action for controlled element |
| `inlineSize` | `'auto' \| 'fill' \| 'fit-content'` | `'auto'` | Button width |
| `accessibilityLabel` | `string` | — | Label for assistive tech |

```html
<s-button variant="primary">Save</s-button>
<s-button variant="secondary">Cancel</s-button>
<s-button variant="tertiary" icon="delete" tone="critical">Delete</s-button>
<s-button loading>Processing</s-button>
<s-button href="https://shopify.com" target="_blank">Visit</s-button>
```

### s-button-group

Displays multiple buttons in a layout.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `gap` | `'base' \| 'none'` | `'base'` | Gap between elements |
| `accessibilityLabel` | `string` | — | Label for screen readers |

**Slots:** `primary-action`, `secondary-actions`

```html
<s-button-group>
  <s-button slot="secondary-actions">Cancel</s-button>
  <s-button slot="primary-action" variant="primary">Save</s-button>
</s-button-group>
```

### s-link

Interactive text navigation.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `href` | `string` | — | URL to link to |
| `target` | `string` | — | Link target |
| `tone` | `string` | — | Link tone |
| `commandFor` | `string` | — | ID of element to control |
| `command` | `string` | `'--auto'` | Action for controlled element |
| `accessibilityLabel` | `string` | — | Label for assistive tech |

```html
<s-link href="https://shopify.com">Visit Shopify</s-link>
<s-link href="/products" target="_blank">Products</s-link>
```

### s-menu

Displays a list of actions.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | Label for assistive tech |

```html
<s-button commandFor="actions-menu">Actions</s-button>
<s-menu id="actions-menu" accessibilityLabel="Customer actions">
  <s-button icon="merge">Merge</s-button>
  <s-button icon="delete" tone="critical">Delete</s-button>
</s-menu>
```

---

## Feedback & Status

### s-badge

Status and completion indicators.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `tone` | `'info' \| 'success' \| 'warning' \| 'critical' \| 'auto' \| 'neutral' \| 'caution'` | `'auto'` | Badge tone |
| `color` | `'base' \| 'strong'` | `'base'` | Color intensity |
| `size` | `'base' \| 'large' \| 'large-100'` | `'base'` | Badge size |
| `icon` | `string` | — | Icon type |

```html
<s-badge>Fulfilled</s-badge>
<s-badge tone="info">Draft</s-badge>
<s-badge tone="success">Active</s-badge>
<s-badge tone="caution">Open</s-badge>
<s-badge tone="warning">On hold</s-badge>
<s-badge tone="critical">Action required</s-badge>
```

### s-banner

Highlights important information.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `heading` | `string` | `''` | Banner title |
| `tone` | `'info' \| 'success' \| 'warning' \| 'critical' \| 'auto'` | `'auto'` | Banner tone |
| `dismissible` | `boolean` | `false` | Shows close button |
| `hidden` | `boolean` | `false` | Hides the banner |

```html
<s-banner heading="Order archived" tone="info" dismissible>
  This order was archived on March 7, 2017.
</s-banner>
<s-banner heading="Error" tone="critical">
  There was an error processing your request.
</s-banner>
```

### s-spinner

Loading indicator.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `size` | `string` | — | Spinner size |
| `accessibilityLabel` | `string` | — | Label for assistive tech |

```html
<s-spinner accessibilityLabel="Loading" size="large-100" />
```

---

## Forms

### s-text-field

Single-line text input.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `label` | `string` | — | Field label |
| `value` | `string` | — | Current value |
| `placeholder` | `string` | — | Placeholder text |
| `details` | `string` | — | Help text (replaces React's helpText) |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the field |
| `required` | `boolean` | `false` | Marks as required |
| `readOnly` | `boolean` | `false` | Makes read-only |
| `prefix` | `string` | `''` | Value before input |
| `suffix` | `string` | `''` | Value after input |
| `icon` | `string` | `''` | Icon type |
| `maxLength` | `number` | `Infinity` | Max characters |
| `minLength` | `number` | `0` | Min characters |
| `autocomplete` | `string` | `'on'` | Autofill hint |
| `labelAccessibilityVisibility` | `'visible' \| 'exclusive'` | `'visible'` | Label visibility |

```html
<s-text-field
  label="Store name"
  value="Jaded Pixel"
  placeholder="Enter store name"
  details="This will be displayed on your storefront"
  required
/>
<s-text-field label="Price" prefix="$" suffix="USD" />
```

### s-text-area

Multi-line text input.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `label` | `string` | — | Field label |
| `value` | `string` | — | Current value |
| `placeholder` | `string` | — | Placeholder text |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the field |
| `required` | `boolean` | `false` | Marks as required |

```html
<s-text-area label="Description" placeholder="Enter product description" />
```

### s-select

Dropdown selection.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `label` | `string` | — | Field label |
| `value` | `string` | — | Selected value |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables the field |
| `required` | `boolean` | `false` | Marks as required |

```html
<s-select label="Country">
  <option value="us">United States</option>
  <option value="ca">Canada</option>
  <option value="uk">United Kingdom</option>
</s-select>
```

### s-checkbox

Checkbox selection.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `label` | `string` | — | Checkbox label |
| `checked` | `boolean` | `false` | Whether checked |
| `defaultChecked` | `boolean` | `false` | Default state |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables checkbox |
| `required` | `boolean` | `false` | Marks as required |
| `value` | `string` | — | Value when checked |
| `accessibilityLabel` | `string` | — | Label for assistive tech |

```html
<s-checkbox label="I agree to the terms and conditions" />
<s-checkbox label="Subscribe to newsletter" checked />
```

### s-choice-list

Radio buttons or checkbox groups.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `label` | `string` | — | Field label |
| `multiple` | `boolean` | `false` | Allows multiple selections (checkboxes vs radio) |
| `values` | `string[]` | — | Selected values |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables all choices |
| `details` | `string` | — | Help text |
| `labelAccessibilityVisibility` | `'visible' \| 'exclusive'` | `'visible'` | Label visibility |

```html
<!-- Radio buttons (single select) -->
<s-choice-list label="Company name" name="company">
  <s-choice value="hidden">Hidden</s-choice>
  <s-choice value="optional">Optional</s-choice>
  <s-choice value="required">Required</s-choice>
</s-choice-list>

<!-- Checkboxes (multiple select) -->
<s-choice-list label="Features" name="features" multiple>
  <s-choice value="analytics">Analytics</s-choice>
  <s-choice value="reports">Reports</s-choice>
</s-choice-list>
```

### s-switch

Toggle on/off.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `label` | `string` | — | Switch label |
| `checked` | `boolean` | `false` | Whether on |
| `defaultChecked` | `boolean` | `false` | Default state |
| `details` | `string` | — | Help text |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables switch |
| `required` | `boolean` | `false` | Marks as required |
| `accessibilityLabel` | `string` | — | Label for assistive tech |

```html
<s-switch label="Enable feature" details="Toggle to enable this feature" />
<s-switch label="Notifications" checked />
```

### s-drop-zone

File upload via drag-and-drop.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `label` | `string` | — | Field label |
| `accept` | `string` | `''` | Accepted file types |
| `multiple` | `boolean` | `false` | Allows multiple files |
| `error` | `string` | — | Error message |
| `disabled` | `boolean` | `false` | Disables drop zone |
| `required` | `boolean` | `false` | Marks as required |
| `files` | `File[]` | `[]` | Selected files (read-only) |
| `accessibilityLabel` | `string` | — | Label for assistive tech |

```html
<s-drop-zone
  label="Upload images"
  accept=".jpg,.png,.gif"
  multiple
  accessibilityLabel="Upload image files"
/>
```

### Other Form Components

```html
<s-date-field label="Start date" />
<s-date-picker />
<s-color-field label="Background color" />
<s-color-picker />
<s-number-field label="Quantity" value="1" />
<s-money-field label="Price" currency="USD" />
<s-email-field label="Email address" />
<s-password-field label="Password" />
<s-url-field label="Website URL" />
<s-search-field placeholder="Search products" />
```

---

## Layout & Structure

### s-page

Main app container.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `heading` | `string` | — | Page heading |

**Slots:** `primary-action`, `secondary-actions`

```html
<s-page heading="Products">
  <s-button slot="primary-action" variant="primary">Add product</s-button>
  <s-button slot="secondary-actions">Import</s-button>
  <s-button slot="secondary-actions">Export</s-button>

  <!-- Page content -->
</s-page>
```

### s-section

Thematic content grouping (replaces Card).

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `heading` | `string` | — | Section heading |
| `padding` | `'base' \| 'none'` | `'base'` | Padding |

```html
<s-section heading="Customer information">
  <s-text-field label="Name" />
  <s-text-field label="Email" />
</s-section>
```

### s-box

Generic flexible container.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `padding` | `PaddingKeyword` | `'none'` | Padding |
| `paddingBlock` | `PaddingKeyword` | `''` | Block padding |
| `paddingInline` | `PaddingKeyword` | `''` | Inline padding |
| `background` | `BackgroundColorKeyword` | `'transparent'` | Background color |
| `border` | `BorderShorthand` | `'none'` | Border shorthand |
| `borderRadius` | `BoxBorderRadii` | `'none'` | Border radius |
| `display` | `'auto' \| 'none'` | `'auto'` | Display type |
| `blockSize` | `SizeUnitsOrAuto` | `'auto'` | Block size |
| `inlineSize` | `SizeUnitsOrAuto` | `'auto'` | Inline size |
| `overflow` | `'visible' \| 'hidden'` | `'visible'` | Overflow |
| `accessibilityRole` | `AccessibilityRole` | `'generic'` | Semantic role |

```html
<s-box padding="base">Content</s-box>
<s-box padding="base" background="subdued" border="base" borderRadius="base">
  Styled content
</s-box>
```

### s-stack

Horizontal or vertical element organization.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `direction` | `'block' \| 'inline'` | `'block'` | Stack direction |
| `gap` | `SpacingKeyword` | `'base'` | Gap between elements |
| `align` | `string` | — | Alignment |
| `wrap` | `boolean` | `false` | Whether items wrap |

```html
<!-- Vertical (BlockStack equivalent) -->
<s-stack direction="block" gap="base">
  <p>Item 1</p>
  <p>Item 2</p>
</s-stack>

<!-- Horizontal (InlineStack equivalent) -->
<s-stack direction="inline" gap="base">
  <s-button>Button 1</s-button>
  <s-button>Button 2</s-button>
</s-stack>
```

### s-grid

Matrix layout for responsive designs (replaces Layout).

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `gridTemplateColumns` | `string` | — | Column definitions |
| `gridTemplateRows` | `string` | — | Row definitions |
| `gap` | `SpacingKeyword` | — | Gap between items |
| `columnGap` | `SpacingKeyword` | — | Column gap |
| `rowGap` | `SpacingKeyword` | — | Row gap |
| `alignContent` | `AlignContentKeyword` | — | Content alignment |
| `alignItems` | `AlignItemsKeyword` | — | Items alignment |
| `justifyContent` | `JustifyContentKeyword` | — | Content justification |
| `justifyItems` | `JustifyItemsKeyword` | — | Items justification |

```html
<s-grid gridTemplateColumns="2fr 1fr" gap="base">
  <s-grid-item>Main content</s-grid-item>
  <s-grid-item>Sidebar</s-grid-item>
</s-grid>

<s-grid gridTemplateColumns="repeat(3, 1fr)" gap="base">
  <s-grid-item>Card 1</s-grid-item>
  <s-grid-item>Card 2</s-grid-item>
  <s-grid-item>Card 3</s-grid-item>
</s-grid>
```

### s-divider

Visual separation.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `direction` | `'block' \| 'inline'` | `'block'` | Divider direction |

```html
<s-divider />
```

### s-table

Data display in rows and columns.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `variant` | `'auto' \| 'list' \| 'table'` | `'auto'` | Layout style |
| `paginate` | `boolean` | `false` | Enable pagination |
| `hasNextPage` | `boolean` | `false` | Has next page |
| `hasPreviousPage` | `boolean` | `false` | Has previous page |
| `loading` | `boolean` | `false` | Loading state |

```html
<s-table>
  <s-table-header-row>
    <s-table-header>Name</s-table-header>
    <s-table-header>Email</s-table-header>
    <s-table-header format="numeric">Orders</s-table-header>
  </s-table-header-row>
  <s-table-body>
    <s-table-row>
      <s-table-cell>John Smith</s-table-cell>
      <s-table-cell>john@example.com</s-table-cell>
      <s-table-cell>23</s-table-cell>
    </s-table-row>
  </s-table-body>
</s-table>
```

### Lists

```html
<s-unordered-list>
  <li>First item</li>
  <li>Second item</li>
</s-unordered-list>

<s-ordered-list>
  <li>First step</li>
  <li>Second step</li>
</s-ordered-list>
```

---

## Media & Visuals

### s-avatar

User profile images or initials.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `alt` | `string` | — | Alternative text |
| `initials` | `string` | — | Initials to display |
| `src` | `string` | — | Image URL |
| `size` | `'small-200' \| 'small' \| 'base' \| 'large' \| 'large-200'` | `'base'` | Avatar size |

```html
<s-avatar alt="John Doe" initials="JD" />
<s-avatar alt="Jane Smith" src="https://example.com/avatar.jpg" size="large" />
```

### s-icon

Graphic symbols.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `type` | `string` | — | Icon type |
| `tone` | `string` | — | Icon tone |
| `color` | `'base' \| 'subdued'` | `'base'` | Color intensity |
| `size` | `string` | — | Icon size |

Common types: `home`, `order`, `product`, `settings`, `search`, `edit`, `delete`, `info`, `plus`, `minus`, `check`, `alert-circle`, `merge`, `incoming`, `outgoing`

```html
<s-icon type="home" />
<s-icon type="order" tone="success" />
<s-icon type="delete" tone="critical" />
```

### s-image

Image embedding.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `src` | `string` | — | Image source URL |
| `alt` | `string` | `''` | Alternative text |
| `aspectRatio` | `string` | `'1/1'` | Aspect ratio |
| `inlineSize` | `'fill' \| 'auto'` | `'fill'` | Inline width |
| `loading` | `'eager' \| 'lazy'` | `'lazy'` | Loading behavior |
| `objectFit` | `string` | — | How content is resized |
| `borderRadius` | `BoxBorderRadii` | — | Border radius |

```html
<s-image
  src="https://example.com/product.jpg"
  alt="Product image"
  aspectRatio="16/9"
/>
```

### s-thumbnail

Small preview images.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `src` | `string` | — | Image source URL |
| `alt` | `string` | — | Alternative text |
| `size` | `'small-200' \| 'small' \| 'base' \| 'large'` | `'base'` | Thumbnail size |

```html
<s-thumbnail
  src="https://example.com/product.jpg"
  alt="Product thumbnail"
  size="small"
/>
```

---

## Overlays

### s-modal

Overlay content display.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `heading` | `string` | — | Modal title |
| `padding` | `'base' \| 'none'` | `'base'` | Content padding |
| `accessibilityLabel` | `string` | — | Label for assistive tech |

**Slots:** `primary-action`, `secondary-actions`

```html
<s-button commandFor="my-modal">Open Modal</s-button>

<s-modal id="my-modal" heading="Confirm Action">
  <s-paragraph>Are you sure you want to proceed?</s-paragraph>

  <s-button slot="secondary-actions" commandFor="my-modal" command="--hide">
    Cancel
  </s-button>
  <s-button slot="primary-action" variant="primary" commandFor="my-modal" command="--hide">
    Confirm
  </s-button>
</s-modal>
```

### s-popover

Button-triggered overlays.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `blockSize` | `SizeUnitsOrAuto` | — | Block size |
| `inlineSize` | `SizeUnitsOrAuto` | — | Inline size |
| `maxBlockSize` | `SizeUnitsOrNone` | — | Max block size |
| `maxInlineSize` | `SizeUnitsOrNone` | — | Max inline size |

```html
<s-button commandFor="options-popover">Options</s-button>

<s-popover id="options-popover">
  <s-stack direction="block">
    <s-button variant="tertiary">Import</s-button>
    <s-button variant="tertiary">Export</s-button>
  </s-stack>
</s-popover>
```

### s-tooltip

Hover/focus information.

```html
<s-tooltip id="help-tip">This is helpful information</s-tooltip>
<s-button interestFor="help-tip" accessibilityLabel="Help">?</s-button>
```

### Command Reference

| Command | Description |
|---------|-------------|
| `--auto` | Default action for the component |
| `--show` | Shows the target component |
| `--hide` | Hides the target component |
| `--toggle` | Toggles visibility |

---

## Typography

### s-heading

Hierarchical titles.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityRole` | `'heading' \| 'presentation' \| 'none'` | `'heading'` | Semantic meaning |
| `lineClamp` | `number` | `Infinity` | Lines before truncation |
| `accessibilityVisibility` | `'visible' \| 'hidden' \| 'exclusive'` | `'visible'` | Visibility |

```html
<s-heading>Page Title</s-heading>
```

### s-paragraph

Text blocks.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `color` | `'base' \| 'subdued'` | `'base'` | Color intensity |
| `tone` | `string` | — | Text tone |
| `lineClamp` | `number` | `Infinity` | Lines before truncation |
| `dir` | `'' \| 'auto' \| 'ltr' \| 'rtl'` | `''` | Text direction |

```html
<s-paragraph>This is a paragraph of text.</s-paragraph>
<s-paragraph color="subdued">Subdued helper text</s-paragraph>
```

### s-text

Inline text with styling.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `type` | `'strong' \| string` | — | Semantic styling |
| `color` | `'base' \| 'subdued'` | `'base'` | Color intensity |
| `tone` | `string` | — | Text tone |

```html
<s-paragraph>
  <s-text type="strong">Name: </s-text>
  <s-text>Jane Doe</s-text>
</s-paragraph>
```

### s-chip

User-supplied keyword labels.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `color` | `'base' \| 'subdued' \| 'strong'` | `'base'` | Color intensity |
| `accessibilityLabel` | `string` | — | Label for assistive tech |

```html
<s-chip>Category</s-chip>
<s-chip color="strong">Featured</s-chip>
```

---

## Event Handling

### Inline Events

```html
<s-button onclick="handleClick()">Click me</s-button>
```

### JavaScript Events

```html
<s-button id="my-button">Click me</s-button>
<s-text-field id="my-field" label="Name"></s-text-field>

<script>
  document.getElementById('my-button').addEventListener('click', () => {
    console.log('Button clicked');
  });

  document.getElementById('my-field').addEventListener('input', (e) => {
    console.log('Value:', e.currentTarget.value);
  });
</script>
```

### React Integration

```jsx
<s-button onClick={() => handleClick()}>Click me</s-button>
<s-text-field
  label="Name"
  onInput={(e) => setValue(e.currentTarget.value)}
/>
```

---

## References

- [Polaris Web Components Documentation](https://shopify.dev/docs/api/app-home/polaris-web-components)
- [Polaris Design System](https://polaris.shopify.com)

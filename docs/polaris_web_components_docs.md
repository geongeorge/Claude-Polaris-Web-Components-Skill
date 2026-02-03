# Shopify Polaris Web Components Documentation

This document provides a comprehensive reference for Shopify Polaris Web Components. These components are designed for building Shopify app interfaces and follow the Polaris design system. All web components use the `s-` prefix (e.g., `s-button`, `s-box`).

---

## Actions

### Button (`s-button`)

Triggers actions or events, such as submitting forms, opening dialogs, or navigating to other pages. Buttons can also function as links, guiding users to internal or external destinations.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | A label for assistive technologies when button text is insufficient. |
| `command` | `'--auto' \| '--show' \| '--hide' \| '--toggle'` | `'--auto'` | Sets the action when the button is activated. |
| `commandFor` | `string` | — | The ID of the element this button controls. |
| `disabled` | `boolean` | `false` | Disables the button. |
| `download` | `string` | — | Treats the linked URL as a download. |
| `href` | `string` | — | The URL to link to. |
| `icon` | `string` | — | The type of icon to display. |
| `inlineSize` | `'auto' \| 'fill' \| 'fit-content'` | `'auto'` | The inline width of the button. |
| `interestFor` | `string` | — | Sets the element for interest-based interactions. |
| `loading` | `boolean` | `false` | Shows a loading indicator. |
| `target` | `'auto' \| '_blank' \| '_self' \| '_parent' \| '_top'` | `'auto'` | Where to display the linked URL. |
| `tone` | `'critical' \| 'auto' \| 'neutral'` | `'auto'` | The tone of the button. |
| `type` | `'button' \| 'reset' \| 'submit'` | `'button'` | The behavior of the button. |
| `variant` | `'auto' \| 'primary' \| 'secondary' \| 'tertiary'` | `'auto'` | The visual appearance of the button. |

```html
<s-button variant="primary">Add Product</s-button>
<s-button variant="secondary">Save Theme</s-button>
<s-button variant="tertiary" icon="delete" tone="critical">Delete</s-button>
```

### ButtonGroup (`s-button-group`)

Displays multiple buttons in a layout.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | Label for screen reader users. |
| `gap` | `'base' \| 'none'` | `'base'` | The gap between elements. |

```html
<s-button-group>
  <s-button slot="primary-action">Save</s-button>
  <s-button slot="secondary-actions">Cancel</s-button>
</s-button-group>
```

### Link (`s-link`)

Makes text interactive, allowing users to navigate to other pages or perform specific actions.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | A label for assistive technologies. |
| `command` | `'--auto' \| '--show' \| '--hide' \| '--toggle'` | `'--auto'` | Sets the action when the link is activated. |
| `commandFor` | `string` | — | The ID of the element this link controls. |
| `download` | `string` | — | Treats the linked URL as a download. |
| `href` | `string` | — | The URL to link to. |
| `interestFor` | `string` | — | Sets the element for interest-based interactions. |
| `lang` | `string` | — | Indicates the text language. |
| `target` | `string` | — | Where to display the linked URL. |
| `tone` | `string` | — | The tone of the link. |

```html
<s-link href="https://shopify.com">Visit Shopify</s-link>
```

### Menu (`s-menu`)

Displays a list of actions that can be performed on a resource.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | A label for assistive technologies. |

```html
<s-button commandFor="customer-menu">Edit customer</s-button>
<s-menu id="customer-menu" accessibilityLabel="Customer actions">
  <s-button icon="merge">Merge customer</s-button>
  <s-button icon="incoming">Request customer data</s-button>
  <s-button icon="delete" tone="critical">Delete customer</s-button>
</s-menu>
```

---

## Feedback and Status Indicators

### Badge (`s-badge`)

Informs users about the status of an object or indicates that an action has been completed.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `color` | `'base' \| 'strong'` | `'base'` | Modifies the color intensity. |
| `icon` | `string` | — | The type of icon to display. |
| `size` | `'base' \| 'large' \| 'large-100'` | `'base'` | The size of the badge. |
| `tone` | `'info' \| 'success' \| 'warning' \| 'critical' \| 'auto' \| 'neutral' \| 'caution'` | `'auto'` | The tone of the badge. |

```html
<s-badge>Fulfilled</s-badge>
<s-badge tone="info">Draft</s-badge>
<s-badge tone="success">Active</s-badge>
<s-badge tone="caution">Open</s-badge>
<s-badge tone="warning">On hold</s-badge>
<s-badge tone="critical">Action required</s-badge>
```

### Banner (`s-banner`)

Highlights important information or required actions prominently within the interface.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `dismissible` | `boolean` | `false` | Shows a close button. |
| `heading` | `string` | `''` | The title of the banner. |
| `hidden` | `boolean` | `false` | Hides the banner. |
| `tone` | `'info' \| 'success' \| 'warning' \| 'critical' \| 'auto'` | `'auto'` | The tone of the banner. |

```html
<s-banner heading="Order archived" tone="info" dismissible>
  This order was archived on March 7, 2017 at 3:12pm EDT.
</s-banner>
```

### Spinner (`s-spinner`)

Displays an animated indicator showing users that content or actions are loading.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | A label for assistive technologies. |
| `size` | `string` | — | The size of the spinner. |

```html
<s-spinner accessibilityLabel="Loading" size="large-100" />
```

---

## Forms

### TextField (`s-text-field`)

Lets users enter or edit text within a single-line input.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `autocomplete` | `string` | `'on'` | A hint for autofill. |
| `defaultValue` | `string` | — | The default value. |
| `details` | `string` | — | Additional context or guidance. |
| `disabled` | `boolean` | `false` | Disables the field. |
| `error` | `string` | — | Error message to display. |
| `icon` | `string` | `''` | The type of icon to display. |
| `id` | `string` | — | A unique identifier. |
| `label` | `string` | — | The field label. |
| `labelAccessibilityVisibility` | `'visible' \| 'exclusive'` | `'visible'` | Label visibility. |
| `maxLength` | `number` | `Infinity` | Maximum characters allowed. |
| `minLength` | `number` | `0` | Minimum characters allowed. |
| `name` | `string` | — | Form field identifier. |
| `placeholder` | `string` | — | Placeholder text. |
| `prefix` | `string` | `''` | Value displayed before input. |
| `readOnly` | `boolean` | `false` | Makes the field read-only. |
| `required` | `boolean` | `false` | Marks the field as required. |
| `suffix` | `string` | `''` | Value displayed after input. |
| `value` | `string` | — | The current value. |

```html
<s-text-field
  label="Store name"
  value="Jaded Pixel"
  placeholder="Enter store name"
/>
```

### TextArea (`s-text-area`)

Collects longer text content from users with a multi-line input that expands automatically.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `label` | `string` | — | The field label. |
| `value` | `string` | — | The current value. |
| `placeholder` | `string` | — | Placeholder text. |
| `disabled` | `boolean` | `false` | Disables the field. |
| `error` | `string` | — | Error message to display. |
| `required` | `boolean` | `false` | Marks the field as required. |

```html
<s-text-area label="Description" placeholder="Enter product description" />
```

### Select (`s-select`)

Allows users to pick one option from a menu.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `label` | `string` | — | The field label. |
| `value` | `string` | — | The selected value. |
| `disabled` | `boolean` | `false` | Disables the field. |
| `error` | `string` | — | Error message to display. |
| `required` | `boolean` | `false` | Marks the field as required. |

```html
<s-select label="Country">
  <option value="us">United States</option>
  <option value="ca">Canada</option>
  <option value="uk">United Kingdom</option>
</s-select>
```

### Checkbox (`s-checkbox`)

Gives users a clear way to make selections, such as agreeing to terms or choosing multiple items from a list.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | A label for assistive technologies. |
| `checked` | `boolean` | `false` | Whether the checkbox is checked. |
| `defaultChecked` | `boolean` | `false` | Default checked state. |
| `disabled` | `boolean` | `false` | Disables the checkbox. |
| `error` | `string` | — | Error message to display. |
| `id` | `string` | — | A unique identifier. |
| `label` | `string` | — | The checkbox label. |
| `name` | `string` | — | Form field identifier. |
| `required` | `boolean` | `false` | Marks the field as required. |
| `value` | `string` | — | The value when checked. |

```html
<s-checkbox label="I agree to the terms and conditions" />
```

### ChoiceList (`s-choice-list`)

Presents multiple options to users, allowing either single selections with radio buttons or multiple selections with checkboxes.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `details` | `string` | — | Additional context or guidance. |
| `disabled` | `boolean` | `false` | Disables all choices. |
| `error` | `string` | — | Error message to display. |
| `label` | `string` | — | The field label. |
| `labelAccessibilityVisibility` | `'visible' \| 'exclusive'` | `'visible'` | Label visibility. |
| `multiple` | `boolean` | `false` | Allows multiple selections. |
| `name` | `string` | — | Form field identifier. |
| `values` | `string[]` | — | Selected values. |

```html
<s-choice-list label="Company name" name="company">
  <s-choice value="hidden">Hidden</s-choice>
  <s-choice value="optional">Optional</s-choice>
  <s-choice value="required">Required</s-choice>
</s-choice-list>
```

### Switch (`s-switch`)

Gives users a clear way to toggle options on or off.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | A label for assistive technologies. |
| `checked` | `boolean` | `false` | Whether the switch is on. |
| `defaultChecked` | `boolean` | `false` | Default checked state. |
| `details` | `string` | — | Additional context or guidance. |
| `disabled` | `boolean` | `false` | Disables the switch. |
| `error` | `string` | — | Error message to display. |
| `id` | `string` | — | A unique identifier. |
| `label` | `string` | — | The switch label. |
| `name` | `string` | — | Form field identifier. |
| `required` | `boolean` | `false` | Marks the field as required. |
| `value` | `string` | — | The value when checked. |

```html
<s-switch label="Enable feature" details="Ensure all criteria are met before enabling" />
```

### DropZone (`s-drop-zone`)

Lets users upload files through drag-and-drop functionality into a designated area on a page, or by activating a button.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accept` | `string` | `''` | Accepted file types. |
| `accessibilityLabel` | `string` | — | A label for assistive technologies. |
| `disabled` | `boolean` | `false` | Disables the drop zone. |
| `error` | `string` | — | Error message to display. |
| `files` | `File[]` | `[]` | Currently selected files (read-only). |
| `label` | `string` | — | The field label. |
| `labelAccessibilityVisibility` | `'visible' \| 'exclusive'` | `'visible'` | Label visibility. |
| `multiple` | `boolean` | `false` | Allows multiple files. |
| `name` | `string` | — | Form field identifier. |
| `required` | `boolean` | `false` | Marks the field as required. |

```html
<s-drop-zone
  label="Upload"
  accessibilityLabel="Upload image of type jpg, png, or gif"
  accept=".jpg,.png,.gif"
  multiple
/>
```

### DateField (`s-date-field`)

Allows users to select a specific date with a date picker.

```html
<s-date-field label="Start date" />
```

### DatePicker (`s-date-picker`)

Allows users to select a specific date or date range.

```html
<s-date-picker />
```

### ColorField (`s-color-field`)

Allows users to select a color with a color picker or as a text input.

```html
<s-color-field label="Background color" />
```

### ColorPicker (`s-color-picker`)

Allows users to select a color from a color palette.

```html
<s-color-picker />
```

### NumberField (`s-number-field`)

Collects numerical values from users with optimized keyboard settings and built-in validation.

```html
<s-number-field label="Quantity" value="1" />
```

### MoneyField (`s-money-field`)

Collects monetary values from users with built-in currency formatting and validation.

```html
<s-money-field label="Price" currency="USD" />
```

### EmailField (`s-email-field`)

Lets users enter email addresses with optimized keyboard settings.

```html
<s-email-field label="Email address" />
```

### PasswordField (`s-password-field`)

Securely collects sensitive information from users.

```html
<s-password-field label="Password" />
```

### URLField (`s-url-field`)

Collects URLs from users with built-in formatting and validation.

```html
<s-url-field label="Website URL" />
```

### SearchField (`s-search-field`)

Lets users enter search terms or find specific items using a single-line input field.

```html
<s-search-field placeholder="Search products" />
```

---

## Layout and Structure

### Box (`s-box`)

A generic container that provides a flexible alternative for custom designs not achievable with existing components.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | A label for assistive technologies. |
| `accessibilityRole` | `AccessibilityRole` | `'generic'` | Semantic meaning of the content. |
| `accessibilityVisibility` | `'visible' \| 'hidden' \| 'exclusive'` | `'visible'` | Visibility of the element. |
| `background` | `BackgroundColorKeyword` | `'transparent'` | Background color. |
| `blockSize` | `SizeUnitsOrAuto` | `'auto'` | Block size. |
| `border` | `BorderShorthand` | `'none'` | Border shorthand. |
| `borderColor` | `ColorKeyword` | `''` | Border color. |
| `borderRadius` | `BoxBorderRadii` | `'none'` | Border radius. |
| `borderStyle` | `BoxBorderStyles` | `''` | Border style. |
| `borderWidth` | `string` | `''` | Border width. |
| `display` | `'auto' \| 'none'` | `'auto'` | Display type. |
| `inlineSize` | `SizeUnitsOrAuto` | `'auto'` | Inline size. |
| `maxBlockSize` | `SizeUnitsOrNone` | `'none'` | Maximum block size. |
| `maxInlineSize` | `SizeUnitsOrNone` | `'none'` | Maximum inline size. |
| `minBlockSize` | `SizeUnits` | `'0'` | Minimum block size. |
| `minInlineSize` | `SizeUnits` | `'0'` | Minimum inline size. |
| `overflow` | `'visible' \| 'hidden'` | `'visible'` | Overflow behavior. |
| `padding` | `PaddingKeyword` | `'none'` | Padding on all edges. |
| `paddingBlock` | `PaddingKeyword` | `''` | Block padding. |
| `paddingBlockEnd` | `PaddingKeyword` | `''` | Block-end padding. |
| `paddingBlockStart` | `PaddingKeyword` | `''` | Block-start padding. |
| `paddingInline` | `PaddingKeyword` | `''` | Inline padding. |
| `paddingInlineEnd` | `PaddingKeyword` | `''` | Inline-end padding. |
| `paddingInlineStart` | `PaddingKeyword` | `''` | Inline-start padding. |

```html
<s-box padding="base">Available for iPad, iPhone, and Android.</s-box>

<s-box padding="base" background="subdued" border="base" borderRadius="base">
  Available for iPad, iPhone, and Android.
</s-box>
```

### Stack (`s-stack`)

Organizes elements horizontally or vertically along the block or inline axis.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `direction` | `'block' \| 'inline'` | `'block'` | The direction of the stack. |
| `gap` | `SpacingKeyword` | `'base'` | The gap between elements. |
| `align` | `string` | — | Alignment of items. |
| `wrap` | `boolean` | `false` | Whether items should wrap. |

```html
<s-stack direction="inline" gap="base">
  <s-button>Button 1</s-button>
  <s-button>Button 2</s-button>
</s-stack>
```

### Grid (`s-grid`)

Organizes content in a matrix of rows and columns for responsive layouts.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `gridTemplateColumns` | `string` | — | Column definitions. |
| `gridTemplateRows` | `string` | — | Row definitions. |
| `gap` | `SpacingKeyword` | — | Gap between items. |
| `columnGap` | `SpacingKeyword` | — | Column gap. |
| `rowGap` | `SpacingKeyword` | — | Row gap. |
| `alignContent` | `AlignContentKeyword` | — | Content alignment. |
| `alignItems` | `AlignItemsKeyword` | — | Items alignment. |
| `justifyContent` | `JustifyContentKeyword` | — | Content justification. |
| `justifyItems` | `JustifyItemsKeyword` | — | Items justification. |

```html
<s-grid gridTemplateColumns="repeat(2, 1fr)" gap="small" justifyContent="center">
  <s-grid-item gridColumn="span 2" border="base" borderStyle="dashed">
    Summary of sales
  </s-grid-item>
  <s-grid-item gridColumn="span 1" border="base" borderStyle="dashed">
    Orders
  </s-grid-item>
  <s-grid-item gridColumn="auto" border="base" borderStyle="dashed">
    Customers
  </s-grid-item>
</s-grid>
```

### Section (`s-section`)

Groups related content into clearly-defined thematic areas.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `heading` | `string` | — | The section heading. |
| `padding` | `'base' \| 'none'` | `'base'` | Padding around the section. |

```html
<s-section heading="Customer information">
  <s-text-field label="Name" />
  <s-text-field label="Email" />
</s-section>
```

### Page (`s-page`)

The main container for placing content in your app.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `heading` | `string` | — | The page heading. |

```html
<s-page heading="Products">
  <s-section heading="Product details">
    <s-text-field label="Title" />
  </s-section>
</s-page>
```

### Divider (`s-divider`)

Creates clear visual separation between elements in your user interface.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `direction` | `'block' \| 'inline'` | `'block'` | The direction of the divider. |

```html
<s-divider />
```

### Table (`s-table`)

Displays data clearly in rows and columns, helping users view, analyze, and compare information.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `hasNextPage` | `boolean` | `false` | Whether there's a next page. |
| `hasPreviousPage` | `boolean` | `false` | Whether there's a previous page. |
| `loading` | `boolean` | `false` | Whether the table is loading. |
| `paginate` | `boolean` | `false` | Whether to use pagination. |
| `variant` | `'auto' \| 'list' \| 'table'` | `'auto'` | The layout of the table. |

```html
<s-section padding="none">
  <s-table>
    <s-table-header-row>
      <s-table-header>Name</s-table-header>
      <s-table-header>Email</s-table-header>
      <s-table-header format="numeric">Orders placed</s-table-header>
      <s-table-header>Phone</s-table-header>
    </s-table-header-row>
    <s-table-body>
      <s-table-row>
        <s-table-cell>John Smith</s-table-cell>
        <s-table-cell>john@example.com</s-table-cell>
        <s-table-cell>23</s-table-cell>
        <s-table-cell>123-456-7890</s-table-cell>
      </s-table-row>
    </s-table-body>
  </s-table>
</s-section>
```

### OrderedList (`s-ordered-list`)

Displays a numbered list of related items in a specific sequence.

```html
<s-ordered-list>
  <li>First item</li>
  <li>Second item</li>
  <li>Third item</li>
</s-ordered-list>
```

### UnorderedList (`s-unordered-list`)

Displays a bulleted list of related items.

```html
<s-unordered-list>
  <li>Item one</li>
  <li>Item two</li>
  <li>Item three</li>
</s-unordered-list>
```

---

## Media and Visuals

### Avatar (`s-avatar`)

Shows a user's profile image or initials in a compact, visual element.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `alt` | `string` | — | Alternative text for the avatar. |
| `initials` | `string` | — | Initials to display. |
| `size` | `'small-200' \| 'small' \| 'base' \| 'large' \| 'large-200'` | `'base'` | Size of the avatar. |
| `src` | `string` | — | URL of the image. |

```html
<s-avatar alt="John Doe" initials="JD" />
<s-avatar alt="Jane Smith" src="https://example.com/avatar.jpg" />
```

### Icon (`s-icon`)

Renders a graphic symbol to visually communicate core parts of the product and available actions.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `color` | `'base' \| 'subdued'` | `'base'` | Color intensity. |
| `interestFor` | `string` | — | Element for interest-based interactions. |
| `size` | `string` | — | Size of the icon. |
| `tone` | `string` | — | Tone of the icon. |
| `type` | `string` | — | The type of icon to display. |

Available icon types include: `home`, `order`, `product`, `settings`, `search`, `edit`, `delete`, `info`, `complete`, `incomplete`, `alert-circle`, `alert-diamond`, `merge`, `incoming`, and many more.

```html
<s-stack direction="inline" gap="base">
  <s-icon type="home" />
  <s-icon type="order" />
  <s-icon type="product" />
  <s-icon type="settings" />
</s-stack>
```

### Image (`s-image`)

Embeds an image within the interface and controls its presentation.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityRole` | `'none' \| 'presentation' \| 'img'` | `'img'` | Semantic meaning. |
| `alt` | `string` | `''` | Alternative text. |
| `aspectRatio` | `string` | `'1/1'` | Aspect ratio. |
| `border` | `BorderShorthand` | — | Border shorthand. |
| `borderColor` | `ColorKeyword` | — | Border color. |
| `borderRadius` | `BoxBorderRadii` | — | Border radius. |
| `borderStyle` | `BoxBorderStyles` | — | Border style. |
| `borderWidth` | `string` | — | Border width. |
| `inlineSize` | `'fill' \| 'auto'` | `'fill'` | Inline width. |
| `loading` | `'eager' \| 'lazy'` | `'lazy'` | Loading behavior. |
| `objectFit` | `string` | — | How content is resized. |
| `sizes` | `string` | — | Media conditions and sizes. |
| `src` | `string` | — | Image source URL. |
| `srcset` | `string` | — | Image sources with descriptors. |

```html
<s-image
  src="https://cdn.shopify.com/example.png"
  alt="Product image"
  aspectRatio="59/161"
  inlineSize="auto"
/>
```

### Thumbnail (`s-thumbnail`)

Displays a small preview image representing content, products, or media.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `alt` | `string` | — | Alternative text. |
| `size` | `'small-200' \| 'small' \| 'base' \| 'large'` | `'base'` | Size of the thumbnail. |
| `src` | `string` | — | Image source URL. |

```html
<s-thumbnail
  alt="White sneakers"
  src="https://cdn.shopify.com/static/images/polaris/thumbnail-wc_src.jpg"
/>
```

---

## Overlays

### Modal (`s-modal`)

Displays content in an overlay. Use to create a distraction-free experience such as a confirmation dialog or a settings panel.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | A label for assistive technologies. |
| `heading` | `string` | — | The title of the modal. |
| `padding` | `'base' \| 'none'` | `'base'` | Padding around the content. |

```html
<s-button commandFor="modal">Open</s-button>
<s-modal id="modal" heading="Details">
  <s-paragraph>Displaying more details here.</s-paragraph>
  <s-button slot="secondary-actions" commandFor="modal" command="--hide">
    Close
  </s-button>
  <s-button slot="primary-action" variant="primary" commandFor="modal" command="--hide">
    Save
  </s-button>
</s-modal>
```

### Popover (`s-popover`)

Displays content in an overlay that can be triggered by a button.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `blockSize` | `SizeUnitsOrAuto` | — | Block size. |
| `inlineSize` | `SizeUnitsOrAuto` | — | Inline size. |
| `maxBlockSize` | `SizeUnitsOrNone` | — | Maximum block size. |
| `maxInlineSize` | `SizeUnitsOrNone` | — | Maximum inline size. |
| `minBlockSize` | `SizeUnits` | — | Minimum block size. |
| `minInlineSize` | `SizeUnits` | — | Minimum inline size. |

```html
<s-button commandFor="product-options-popover">Product options</s-button>
<s-popover id="product-options-popover">
  <s-stack direction="block">
    <s-button variant="tertiary">Import</s-button>
    <s-button variant="tertiary">Export</s-button>
  </s-stack>
</s-popover>
```

### Tooltip (`s-tooltip`)

Displays helpful information in a small overlay when users hover or focus on an element.

```html
<s-tooltip id="bold-tooltip">Bold</s-tooltip>
<s-button interestFor="bold-tooltip" accessibilityLabel="Bold">B</s-button>
```

---

## Typography and Content

### Heading (`s-heading`)

Renders hierarchical titles to communicate the structure and organization of page content.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityRole` | `'heading' \| 'presentation' \| 'none'` | `'heading'` | Semantic meaning. |
| `accessibilityVisibility` | `'visible' \| 'hidden' \| 'exclusive'` | `'visible'` | Visibility of the element. |
| `lineClamp` | `number` | `Infinity` | Number of lines before truncation. |

```html
<s-heading>Online store dashboard</s-heading>
```

### Paragraph (`s-paragraph`)

Displays a block of text and can contain inline elements such as buttons, links, or emphasized text.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityVisibility` | `'visible' \| 'hidden' \| 'exclusive'` | `'visible'` | Visibility of the element. |
| `color` | `'base' \| 'subdued'` | `'base'` | Color intensity. |
| `dir` | `'' \| 'auto' \| 'ltr' \| 'rtl'` | `''` | Text directionality. |
| `fontVariantNumeric` | `'auto' \| 'normal' \| 'tabular-nums'` | `'auto'` | Numeric font properties. |
| `lineClamp` | `number` | `Infinity` | Number of lines before truncation. |
| `tone` | `string` | — | Tone of the text. |

```html
<s-paragraph>
  Shopify POS is the easiest way to sell your products in person. Available for
  iPad, iPhone, and Android.
</s-paragraph>
```

### Text (`s-text`)

Displays inline text with specific visual styles or tones.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityVisibility` | `'visible' \| 'hidden' \| 'exclusive'` | `'visible'` | Visibility of the element. |
| `color` | `'base' \| 'subdued'` | `'base'` | Color intensity. |
| `dir` | `'' \| 'auto' \| 'ltr' \| 'rtl'` | `''` | Text directionality. |
| `fontVariantNumeric` | `'auto' \| 'normal' \| 'tabular-nums'` | `'auto'` | Numeric font properties. |
| `interestFor` | `string` | — | Element for interest-based interactions. |
| `tone` | `string` | — | Tone of the text. |
| `type` | `'strong' \| string` | — | Semantic meaning and styling. |

```html
<s-paragraph>
  <s-text type="strong">Name: </s-text>
  <s-text>Jane Doe</s-text>
</s-paragraph>
```

### Chip (`s-chip`)

Represents a set of user-supplied keywords that help label, organize, and categorize objects.

| Property | Type | Default | Description |
|----------|------|---------|-------------|
| `accessibilityLabel` | `string` | — | A label for assistive technologies. |
| `color` | `'base' \| 'subdued' \| 'strong'` | `'base'` | Color intensity. |

```html
<s-chip>Chip</s-chip>
```

---

## References

- [Polaris Web Components Documentation](https://shopify.dev/docs/api/app-home/polaris-web-components)
- [Polaris React Components](https://polaris-react.shopify.com/components)

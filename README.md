# React Components Styleguide

## Table of Contents

- [Components](#components)
  - [Base](#base)
  - [Buttons](#buttons)
  - [Inputs](#inputs)
  - [Modals](#modals)
  - [Navigation](#navigation)
- [Behaviors](#behaviors)
  - [Change](#change)
  - [Click](#click)
  - [Close](#close)
  - [Focus](#focus)

## Components

### Base

```tsx
interface Base {
  id?: string;
  name?: string;
  className?: string;
  ariaLabel?: string;
  ariaLabelBy?: string;
  ariaDescribedBy?: string;
}
```

#### Accessability

- Allow using `aria-label`, `aria-labeledby` and `aria-describedby` - to label the element and describe it with extra information.

**[🔝 Back to top](#table-of-contents)**

### Buttons

```tsx
interface Button extends Base, Click, Focus {
  children: React.ReactNode;
  size?: 'small' | 'medium' | 'large';
  disabled?: boolean;
  prefix?: React.ReactNode;
}
```

Extending: [Base](#base), [Click](#click), [Focus](#focus).

#### Accessability

- When the button isn't implemented using the native `<button>` element, `role="button"` is needed.

#### Extensions

##### Toggle Button

```tsx
interface ToggleButton extends Button {
  selected?: boolean;
}
```

**[🔝 Back to top](#table-of-contents)**

### Inputs

```tsx
interface Input<T> extends Base, Change<T>, Focus {
  size?: 'small' | 'medium' | 'large';
  disabled?: boolean;
  required?: boolean;
}
```

Extending: [Base](#base), [Change](#change), [Focus](#focus).

#### Accessability

- Text Field must have label associated with the input using a `for` attribute.
- In case of error validation, `aria-describedby` should be associated with the error message element.

#### Extensions

##### Text Field

```tsx
interface TextField extends Input<HTMLInputElement> {
  label: string;
  placeholder?: string;
  readOnly?: boolean;
  minLength?: number;
  maxLength?: number;
}
```

##### Checkbox

```tsx
interface Checkbox extends Input<HTMLInputElement> {
  checked?: boolean;
}
```

##### Radio

```tsx
interface Radio extends Input<HTMLInputElement> {
  checked?: boolean;
}
```

**[🔝 Back to top](#table-of-contents)**

### Modals

```tsx
interface Modal extends Base, Close {
  children: React.ReactNode;
}
```

Extending: [Base](#base), [Close](#close).

#### Accessability

-

#### Extensions

##### Dialog

```tsx
interface Dialog extends Modal {
  title?: string;
  actions?: React.ReactNode;
}
```

**[🔝 Back to top](#table-of-contents)**

## Behaviors

### Change

```tsx
interface Change<T> {
  value?: any;
  onChange?: (event: ChangeEvent<T>) => void;
}
```

**[🔝 Back to top](#table-of-contents)**

### Click

```tsx
interface Click {
  onClick?: React.MouseEventHandler;
  onDblClick?: React.MouseEventHandler;
}
```

**[🔝 Back to top](#table-of-contents)**

### Close

```tsx
interface Close {
  open?: boolean;
  onClose?: () => void;
}
```

**[🔝 Back to top](#table-of-contents)**

### Focus

```tsx
interface Focus {
  autoFocus?: boolean;
  onFocus?: (event: React.FocusEvent) => void;
  onBlur?: (event: React.FocusEvent) => void;
}
```

**[🔝 Back to top](#table-of-contents)**

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
  - [Focus](#focus)

## Components

### Base

```tsx
interface Base {
  id?: string;
  name?: string;
  className?: string;
}
```

**[🔝 Back to top](#table-of-contents)**

### Buttons

```tsx
interface Button extends Base, Click, Focus {
  children: React.ReactNode;
  size?: 'small' | 'medium' | 'large';
  disabled?: boolean;
  prefix?: React.ReactNode;
  ariaLabel?: string;
  ariaLabelBy?: string;
  ariaDescribedBy?: string;
}
```

Extending: [Base](#base), [Click](#click), [Focus](#focus).

#### Accessability

- Allow using `aria-label`, `aria-labeledby` and `aria-describedby` - to label the button and describe it with extra information.
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
  value?: any;
  size?: 'small' | 'medium' | 'large';
  disabled?: boolean;
  required?: boolean;
  ariaLabel?: string;
  ariaLabelBy?: string;
  ariaDescribedBy?: string;
}
```

Extending: [Base](#base), [Change](#change), [Focus](#focus).

#### Extensions

##### Text Field

```tsx
interface TextField extends Input<HTMLInputElement> {
  label?: string;
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

## Behaviors

### Change

```tsx
interface Change<T> {
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

### Focus

```tsx
interface Focus {
  autoFocus?: boolean;
  onFocus?: (event: React.FocusEvent) => void;
  onBlur?: (event: React.FocusEvent) => void;
}
```

**[🔝 Back to top](#table-of-contents)**

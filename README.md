# React Components Styleguide

## Table of Contents

- [Components](#components)
  - [Base](#base)
  - [Buttons](#buttons)
  - [Inputs](#inputs)
  - [Modals](#modals)
  - [Navigation](#navigation)
- [Behaviors](#behaviors)
  - [Click](#click)
  - [Focus](#focus)

## Components

### Base

```jsx
interface Base {
  id?: string;
  name?: string;
  className?: string;
}
```

**[🔝 Back to top](#table-of-contents)**

### Buttons

```jsx
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

- Allow using `aria-label`, `aria-labeledby` and `aria-describedby` to label the button and describe it with extra information.
- When the button isn't implemented using the native `<button>` element, `role="button"` is needed.

#### Extensions

##### Toggle Button

```jsx
interface ToggleButton extends Button {
  selected?: boolean;
}
```

**[🔝 Back to top](#table-of-contents)**

### Inputs

```jsx

```

## Behaviors

### Click

```jsx
interface Click {
  onClick?: React.MouseEventHandler;
  onDblClick?: React.MouseEventHandler;
}
```

**[🔝 Back to top](#table-of-contents)**

### Focus

```jsx
interface Focus {
  autoFocus?: boolean;
  onFocus?: (event: React.FocusEvent) => void;
  onBlur?: (event: React.FocusEvent) => void;
}
```

**[🔝 Back to top](#table-of-contents)**

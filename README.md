# React Components Styleguide

An opinionated styleguide concentrating essential props, common behaviors and accessibility guidelines for various components implemented by React.

The purpose is to guide developers in a clear and cohesive way when specifying
design systems' components or applicative ones.

⚠️ Although the suggestions below were collected from popular design systems, they are still opinionated. You don't have to completely adhere, but rather consider them.

## Table of Contents

- [🧱 Components](#components)
  - [Base](#base)
  - [Buttons](#buttons)
  - [Inputs](#inputs)
  - [Modals](#modals)
  - [Navigation](#navigation)
- [🖱️ Behaviors](#behaviors)
  - [Change](#change)
  - [Click](#click)
  - [Error](#error)
  - [Focus](#focus)
  - [Open](#open)

## 🧱 Components

This section lists components by familiar categories. Each category specifies likely needed props (that might be inherited from other components or behavior compositions), accessibility guidelines and prominent extensions of this kind of component.

### Base

```tsx
interface BaseProps<T> {
  id?: string;
  name?: string;
  className?: string;
  ref?: React.RefObject<T>;
  ariaLabel?: string;
  ariaLabelBy?: string;
  ariaDescribedBy?: string;
}
```

#### Accessability

- Allow the consumer passing `aria-label`, `aria-labeledby` and `aria-describedby` in order to label the element and describe it with extra information.

**[🔝 Back to top](#table-of-contents)**

### Buttons

```tsx
interface ButtonProps extends BaseProps<HTMLButtonElement>, ClickProps, FocusProps {
  children: React.ReactNode;
  size?: 'small' | 'medium' | 'large';
  disabled?: boolean;
  prefix?: React.ReactNode;
}
```

Extending: [Base](#base), [Click](#click), [Focus](#focus).

#### Accessability

- When the button isn't implemented using the native `<button>` element, `role="button"` is needed.
- Non-textual buttons (e.g Toggle Button) should have a descriptive title - whether implemented using the native `title` attribute or a custom tooltip.

#### Extensions

##### Toggle Button

```tsx
interface ToggleButtonProps extends ButtonProps {
  title: string;
  selected?: boolean;
}
```

**[🔝 Back to top](#table-of-contents)**

### Inputs

```tsx
interface InputProps<T> extends BaseProps<T>, ChangeProps<T>, ErrorProps<T>, FocusProps {
  value?: any;
  size?: 'small' | 'medium' | 'large';
  disabled?: boolean;
  required?: boolean;
}
```

Extending: [Base](#base), [Change](#change), [Error](#error), [Focus](#focus).

#### Accessability

- Text Field must have label associated with the input using a `for` attribute.
- In case of error validation, `aria-describedby` should be associated with the error message element and `aria-invalid` should be attached to the input element.

#### Extensions

##### Text Field

```tsx
interface TextFieldProps extends InputProps<HTMLInputElement> {
  label: string;
  placeholder?: string;
  readOnly?: boolean;
  minLength?: number;
  maxLength?: number;
  autocomplete?: any;
}
```

##### Checkbox

```tsx
interface CheckboxProps extends InputProps<HTMLInputElement> {
  checked?: boolean;
}
```

##### Radio

```tsx
interface RadioProps extends InputProps<HTMLInputElement> {
  checked?: boolean;
}
```

##### Select

```tsx
interface SelectProps extends InputProps<HTMLSelectElement>, OpenProps {
  children: React.ReactNode;
  placeholder?: string;
  multiple?: boolean;
  native?: boolean;
}

interface OptionProps extends BaseProps {
  value: any;
  children?: React.ReactNode;
  disabled?: boolean;
}
```

**[🔝 Back to top](#table-of-contents)**

### Modals

```tsx
interface ModalProps extends BaseProps<HTMLDialogElement>, OpenProps {
  children: React.ReactNode;
}
```

Extending: [Base](#base), [Open](#open).

#### Accessability

- When the modal isn't implemented using the native `<dialog>` element, `role="dialog"` and `aria-modal="true"` are needed.
- If a close button exits, it should be allowed to pass `aria-label` and `aria-labeledby` from the consumer to that button.

#### Extensions

##### Dialog

```tsx
interface DialogProps extends ModalProps {
  title?: string;
  actions?: React.ReactNode;
}
```

**[🔝 Back to top](#table-of-contents)**

## Navigation

### Link

```tsx
interface LinkProps extends BaseProps<HTMLLinkElement> {
  children: React.ReactNode;
  href: string;
  rel?: string;
  target?: string;
}
```

Extending: [Base](#base).

#### Accessability

- Pressing the enter key when the link is focused should activate it.

**[🔝 Back to top](#table-of-contents)**

## 🖱️ Behaviors

This section lists compositions of common behaviors, so that each behavior consists of several likely needed props and may have public methods.

### Change

```tsx
interface ChangeProps<T> {
  value?: any;
  onChange?: (event: ChangeEvent<T>) => void;
}
```

**[🔝 Back to top](#table-of-contents)**

### Click

```tsx
interface ClickProps {
  onClick?: React.MouseEventHandler;
  onDblClick?: React.MouseEventHandler;
}
```

**[🔝 Back to top](#table-of-contents)**

### Error

```tsx
interface ErrorProps<T> {
  error?: boolean;
  errorMessage?: string;
  onError?: (event: React.SyntheticEvent<T>) => void;
}
```

**[🔝 Back to top](#table-of-contents)**

### Focus

```tsx
interface FocusProps<T> {
  // Consider `autoFocus` carefully - since it may confuse screen readers and real users as well.
  autoFocus?: boolean;
  onFocus?: (event: React.FocusEvent) => void;
  onBlur?: (event: React.FocusEvent) => void;
}
```

#### Public Methods

```tsx
interface FocusMethods {
  // Sometimes programmatically managing focus is inevitable and necessary.
  focus: () => void;
}
```

**[🔝 Back to top](#table-of-contents)**

### Open

```tsx
interface OpenProps {
  open?: boolean;
  onOpen?: () => void;
  onClose?: () => void;
}
```

#### Public Methods

```tsx
interface OpenMethods {
  // Apparently most of the time the component will be competently controlled,
  // but in some cases we might need to open it programmatically.
  open: () => void;
}
```

**[🔝 Back to top](#table-of-contents)**

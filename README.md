# ReactMentoring ⚛️

A modern mentorship platform built with **React** and **TypeScript**, showcasing best practices in component architecture, state management, and routing in contemporary React applications.

## 📸 Project Preview

<p align="center">
  <img src="https://github.com/Figrac0/React_TS-Mentoring/blob/main/src/assets/screenshots/1.png" width="450" height = "600"/>
</p>

<p align="center">
  <img src="https://github.com/Figrac0/React_TS-Mentoring/blob/main/src/assets/screenshots/2.png" width="450" height = "600"/>
</p>

<p align="center">
  <img src="https://github.com/Figrac0/React_TS-Mentoring/blob/main/src/assets/screenshots/3.png" width="450" height = "600"/>
</p>

<p align="center">
  <img src="https://github.com/Figrac0/React_TS-Mentoring/blob/main/src/assets/screenshots/4.png" width="450" height = "600"/>
</p>

<p align="center">
  <img src="https://github.com/Figrac0/React_TS-Mentoring/blob/main/src/assets/screenshots/5.png" width="450" height = "600"/>
</p>

## 🎯 Overview

ReactMentoring is a feature-rich web application that connects React developers with experienced mentors. The platform demonstrates professional React development patterns including advanced TypeScript usage, context-based state management, and modern component composition.

## ✨ Key Features

- **Browse Mentoring Sessions**: View available React mentoring sessions with detailed descriptions
- **Session Booking**: Book individual mentoring sessions with form validation
- **Upcoming Sessions Management**: Track and manage booked sessions
- **Responsive Navigation**: Intuitive routing with React Router
- **Modal Management**: Reusable modal components with imperative APIs
- **Type-Safe Development**: Full TypeScript coverage for enhanced developer experience

## 🛠️ Technology Stack

### Core Technologies
- **React 18**: Latest React features including concurrent rendering
- **TypeScript**: Full type safety with advanced type patterns
- **React Router v6**: Modern client-side routing with data APIs
- **CSS3**: Custom styling with modern features and animations

### Advanced React Patterns
- **Context API**: Global state management for session data
- **Custom Hooks**: Reusable logic abstraction
- **Compound Components**: Flexible UI component patterns
- **Imperative Handles**: Controlled component APIs
- **Portals**: Advanced DOM manipulation for modals

## 🏗️ Architecture

### Component Structure
The application follows a modular architecture with clear separation of concerns:
```text
src/
├── components/
│ ├── UI/ # Reusable presentational components
│ ├── Sessions/ # Session-related components
│ └── Navigation/ # Navigation components
├── pages/ # Route-level page components
├── store/ # Context and state management
└── assets/ # Static assets
```


### State Management
- **SessionsContext**: Centralized state for session booking and management
- **Reducer Pattern**: Predictable state updates with typed actions
- **Custom Hooks**: Abstracted context consumption (`useSessionsContext`)

## 🔧 Technical Implementation

### TypeScript Excellence
The project leverages TypeScript's advanced features:
- **Discriminated Unions**: Type-safe component props and actions
- **Generic Components**: Reusable UI components with type constraints
- **Utility Types**: `ComponentPropsWithoutRef`, custom type helpers
- **Type Guards**: Runtime type checking with compile-time safety

### Routing Implementation
```typescript
// Type-safe routing with React Router
const Router = createBrowserRouter([
  {
    path: '/',
    element: <Root />,
    children: [
      { index: true, element: <HomePage /> },
      { path: 'sessions', element: <SessionsPage /> },
      { path: 'sessions/:id', element: <SessionPage /> },
    ],
  },
]);
```

### Reusable Component Patterns

```typescript
// Polymorphic Button component
type ButtonProps = ComponentPropsWithoutRef<'button'> & { to?: never };
type ButtonLinkProps = LinkProps & { to: string };

function isRouterLink(props: ButtonProps | ButtonLinkProps): props is ButtonLinkProps {
  return 'to' in props;
}
```

### Modal Management

```typescript
// Imperative modal API with forwardRef
export type ModalHandle = {
  open: () => void;
};

const Modal = forwardRef<ModalHandle, ModalProps>(function Modal(
  { children, onClose },
  ref
) {
  const dialog = useRef<HTMLDialogElement>(null);
  
  useImperativeHandle(ref, () => ({
    open: () => {
      if (dialog.current) {
        dialog.current.showModal();
      }
    },
  }));
  
  return createPortal(
    <dialog ref={dialog} className="modal" onClose={onClose}>
      {children}
    </dialog>,
    document.getElementById('modal-root')!
  );
});
```

# Component in React


# Class componemt



# functional component 

# JSX

JSX — short for JavaScript XML — is a syntax extension for JavaScript used by React to describe UI structure in a way that looks like HTML. It’s not required (React works without it) but it makes writing component trees far more readable. Under the hood JSX is transformed (by Babel/TypeScript) into React.createElement calls.

What JSX is
- A convenient, declarative syntax for creating React elements/components.
- Syntactic sugar that gets compiled to plain JavaScript (React.createElement or the new JSX transform).
- Not HTML — it looks like HTML but follows JavaScript expression rules and has some React-specific conventions.

Why use JSX
- Easier to read and reason about UI structure.
- Lets you embed JavaScript expressions directly inside markup.
- Works well with tooling (linters, type checkers, formatters).

Key rules and differences from HTML
- JSX must return a single root element (wrap siblings in a parent element or a Fragment: <>...</>).
- Use camelCase for event handlers and attributes (onClick, onMouseEnter).
- Use className instead of class, htmlFor instead of for.
- All tags must be closed: `<img src="..."/>` or `<br />`.
- Components must be capitalized to be treated as custom components (MyButton vs div).
- You can embed expressions with { ... } — any JS expression (not statements).
- Comments inside JSX: {/* comment */}.
- Browser engines do not understand JSX; it must be transpiled (Babel/TS).

How JSX compiles (simple example)
JSX:
```jsx
const el = <button onClick={() => alert('hi')}>Click</button>;
```
Compiles roughly to:
```js
const el = React.createElement(
  'button',
  { onClick: () => alert('hi') },
  'Click'
);
```
With the new automatic JSX runtime (React 17+), transpiled output is more optimized and doesn’t always show createElement directly.

Common patterns

- Functional component:
```jsx
function Greeting({ name }) {
  return <h1>Hello, {name}!</h1>;
}
```

- Conditional rendering:
```jsx
return (
  <div>
    {isLoading ? <Spinner /> : <Content />}
  </div>
);
```

- Lists and keys:
```jsx
<ul>
  {items.map(item => (
    <li key={item.id}>{item.text}</li>
  ))}
</ul>
```
Always provide a stable key (preferably an id), not array index unless unavoidable.

- Fragments (no extra DOM node):
```jsx
return (
  <>
    <Header />
    <Main />
  </>
);
```

- Inline styles:
```jsx
<div style={{ color: 'red', fontSize: 14 }}>Text</div>
```
Style names are camelCased and values are usually strings or numbers.

Security note
- By default React escapes values interpolated in JSX, preventing XSS. To insert raw HTML you must use dangerouslySetInnerHTML:
```jsx
<div dangerouslySetInnerHTML={{ __html: htmlString }} />
```
Use with caution.

File extensions and TypeScript
- .jsx or .js is common for files containing JSX; .tsx for TypeScript with JSX.
- Your build tool / Babel / TypeScript must be configured to compile JSX.

Best practices and pitfalls
- Keep JSX readable: avoid deeply nested inline logic — pull logic into variables or helper functions.
- Prefer small components with clear props.
- Remember event handlers receive SyntheticEvent objects; to pass extra args, wrap in an arrow function.
- Don’t mutate props; keep UI declarative.

If you want, I can:
- Show how to configure Babel/webpack or Vite to compile JSX.
- Convert a JSX snippet to its React.createElement equivalent.
- Explain the new automatic JSX runtime and why it matters.

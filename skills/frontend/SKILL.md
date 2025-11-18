---
name: frontend-web-stack
description: Master modern frontend development with React, Vue, Angular, TypeScript, CSS frameworks, and performance optimization. Use when building web applications, working with UI components, or optimizing web performance.
---

# Frontend & Web Stack Skill

Master modern frontend technologies and build scalable web applications.

## Quick Start

Build a React component with hooks:

```javascript
import React, { useState, useEffect } from 'react';

export const Counter = () => {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Count: ${count}`;
  }, [count]);

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={() => setCount(count + 1)}>Increment</button>
    </div>
  );
};
```

## Frontend Stack Overview

### Core Technologies
- **HTML5**: Semantic elements, forms, accessibility
- **CSS3**: Flexbox, Grid, animations, responsive design
- **JavaScript/TypeScript**: ES6+, async/await, modules
- **DOM API**: Element selection, manipulation, event handling

### Frameworks & Libraries
- **React**: Component-based UI with hooks and state management
- **Vue 3**: Progressive framework with composition API
- **Angular**: Full-featured enterprise framework
- **Next.js**: React framework with SSR and SSG
- **TypeScript**: Type-safe JavaScript development

### Styling Solutions
- **Tailwind CSS**: Utility-first CSS framework
- **CSS Modules**: Component-scoped styles
- **Styled Components**: CSS-in-JS solution
- **Material UI / Chakra UI**: Component libraries

### State Management
- **React Context**: Built-in state management
- **Redux Toolkit**: Predictable state container
- **Zustand**: Lightweight state management
- **Jotai / Recoil**: Atomic state management

### Testing & Quality
- **Jest**: JavaScript testing framework
- **React Testing Library**: Component testing
- **Cypress / Playwright**: End-to-end testing
- **ESLint / Prettier**: Code quality tools

## Learning Resources

### Tutorials & Courses
- [React Official Docs](https://react.dev)
- [Vue 3 Guide](https://vuejs.org/guide/)
- [Frontend Masters](https://frontendmasters.com)
- [Scrimba](https://scrimba.com)

### Practice Projects
1. **Beginner**: Todo app with React hooks
2. **Intermediate**: E-commerce product page with state management
3. **Advanced**: Full-stack dashboard with real-time updates

### Documentation
- [MDN Web Docs](https://developer.mozilla.org)
- [CSS-Tricks](https://css-tricks.com)
- [Dev.to](https://dev.to)

## Essential Patterns

### Component Composition
```javascript
// Reusable Button component
const Button = ({ variant = 'primary', size = 'md', children, ...props }) => {
  const sizeClass = { md: 'px-4 py-2', lg: 'px-6 py-3' }[size];
  const variantClass = {
    primary: 'bg-blue-500 text-white',
    secondary: 'bg-gray-200 text-black'
  }[variant];

  return (
    <button className={`${sizeClass} ${variantClass} rounded`} {...props}>
      {children}
    </button>
  );
};
```

### Custom Hooks
```javascript
// useFetch custom hook
const useFetch = (url) => {
  const [data, setData] = useState(null);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    fetch(url)
      .then(res => res.json())
      .then(data => { setData(data); setLoading(false); })
      .catch(err => { setError(err); setLoading(false); });
  }, [url]);

  return { data, loading, error };
};
```

## Performance Optimization

1. **Code Splitting**: Lazy load components with React.lazy()
2. **Memoization**: Use React.memo() for pure components
3. **Bundle Analysis**: Monitor with webpack-bundle-analyzer
4. **Image Optimization**: Use next/image for automatic optimization
5. **Core Web Vitals**: Measure with Lighthouse

## Common Mistakes to Avoid

❌ Prop drilling (passing props through multiple levels)
✅ Use Context API or state management library instead

❌ Missing dependencies in useEffect
✅ Use ESLint exhaustive-deps rule

❌ Heavy components in main render
✅ Use React.lazy() for code splitting

## Certification & Assessment

- Google Cloud Associate Cloud Engineer
- AWS Certified Solutions Architect
- Frontend Masters Certificates
- LeetCode JavaScript Challenges

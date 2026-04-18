# Simple Timer App 🕒

A learning project built while following the [Modern React From The Beginning](https://www.udemy.com/course/modern-react-from-the-beginning/) course on Udemy.

## About

This project is a simple countdown timer that focuses on learning the `useRef` hook — one of the built-in React hooks. It covers two main use cases of `useRef`:

1. **Referencing a DOM element directly** — to auto-focus the Start button when the component first mounts
2. **Persisting a value across renders** — to hold the interval ID without causing a re-render

## Live Demo

**➡️ [View Live App](https://dikidikay-simple-timer.netlify.app/)**

## What I Learned

### `useRef` to Reference a DOM Element

In `TimerControls.jsx`, a ref is attached directly to the Start button. Combined with `useEffect`, the button receives focus automatically when the component mounts — no state involved, no re-render triggered.

```jsx
const startButtonRef = useRef(null);

useEffect(() => {
  if (startButtonRef.current) {
    startButtonRef.current.focus();
  }
}, []);
```

### `useRef` to Persist a Value Across Renders

The interval ID returned by `setInterval` is stored in a ref instead of state. This means it stays available across renders and can be used to clear the interval on pause or reset — but changing it never causes the component to re-render.

```jsx
const timerRef = useRef();

// Start
timerRef.current = setInterval(() => {
  setTime((prev) => prev + 1);
}, 1000);

// Stop
clearInterval(timerRef.current);
```

### Component Structure

| Component           | Role                                             |
| ------------------- | ------------------------------------------------ |
| `App.jsx`           | Root layout                                      |
| `Timer.jsx`         | Core logic — state, ref, handlers                |
| `TimerDisplay.jsx`  | Renders the current time value                   |
| `TimerControls.jsx` | Start/Pause and Reset buttons, handles DOM focus |

## Run Locally

```bash
npm install
npm run dev
```

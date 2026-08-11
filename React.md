## Hooks
### useRef
- Frozen stable object, only "current" can be modified (prevents rerender when .current state changes)\
  <img width="28%" alt="image" src="https://github.com/user-attachments/assets/a9863c5c-f599-4056-b70e-c87a90c27f3e" />
  <img width="28%" alt="image" src="https://github.com/user-attachments/assets/b2f76498-e568-4de2-8393-6afc188b79ab" />
- Also provides DOM access\
  <img width="36%" alt="image" src="https://github.com/user-attachments/assets/8e113b34-a047-42d4-befc-24c68723b251" />

### useEffect
- runs background tasks based on dependency array
- return fn is triggered when component is unmounted (used for cleanup to prevent memory leak) <img width="450" height="250" alt="image" src="https://github.com/user-attachments/assets/663efb90-a544-44ed-8fd5-78bafeb2233c" />

### useState
- state and setState with init value (component which uses it will rerender)
<img width="30%" alt="image" src="https://github.com/user-attachments/assets/d1269544-7abf-4756-ae99-07b2da83924a" />

### useContext
- global state management wrapped with provider (prevent prop drilling)
- every component that calls "useContext" will rerender when context changes (their childer will re-render too, unless memoized) (SPLIT context like: ErrorContext, ApplicationContext - to prevent entire parent componet rerender and reduce blast radius)

### useReducer
- reducer is basically a function which updates complex/multiple states\
  <img width="36%" alt="image" src="https://github.com/user-attachments/assets/30fa7a82-6dbb-4959-869c-ed57555d59a7" /><img width="30%" alt="image" src="https://github.com/user-attachments/assets/27e64a31-716e-44d7-a809-8b7350922a5e" />

### useMemo (memoize a value) && useCallback (memoize a fn)
- execute once and prevent rerender unless and until the values in dep array changes
<img width="48%" src="https://github.com/user-attachments/assets/a3574860-ff10-4794-923c-c541e7bad712" />
<img width="48%" src="https://github.com/user-attachments/assets/2d853363-00b5-4414-984a-4a8950baf15b" />



## strict mode
extra checks: (will give warning of bad cope practices, if packages, fns are deprecated or about to be)
- double renders components which will trigger effects twice (2 API calls, happens only in development not in builds)

### react dev tools
react dev tools is useful to inspect component and state changes
$r - last select component in inspector\
$0 - last dom selected in inspector\
Profiler > (falmegraph / ranked) check component rendering time and performance

## React performance
whenever a component changes, all its child components re-renders:
<img width="516" height="414" alt="image" src="https://github.com/user-attachments/assets/6c96297c-ab1a-4108-a89d-95635df83350" />  


## lazy loading
split build into chunks and render them only when its route is visited
<img width="520" height="340" alt="image" src="https://github.com/user-attachments/assets/62535178-e27a-4f82-957b-c43752dc790a" />

## react server components:
SSR - server renders and sends HTML -> client browser parses HTML to DOM  
RSC - server sends RSC payload (serialized component) -> client browser creates / updates DOM  
both happens at request time unlike SSG which happens at build time

## React Compiler
A build tool installed through npm amd add to vite config\
It automatically optimizes React app at build time by handling memoization, eliminating the need for manual useMemo, useCallback, and React.memo

## Vite build process
- bundler (doesnt bundle on dev mode)
- .1. build dependency graph (tree structure of file and components), 2. Tree shaking (unused export, dead code), 3. chunks (code split based on imports / shared modules / libraries). 4. when request is hit, it loads main chunk and its dependency chunks... then loads the rest on demand


># React Component Lifecycle
>Every component has 3 phases in its lifecycle
>- Mounting phase
>- updating phase
>- unmounting phase



> **Mounting** :Mounting is the process where React renders a component for the first time and inserts its resulting DOM element into Actual DOM <br>
> OR <br>
> Mounting means a component appears in the UI for the first time.

> **Unmountion** Unmounting is the process of removing mounted component from Actual DOM


> **updating** : when component state or props change the we update it to the Actual DOM

---
## Class Component Lifecycle 
### Mounting phase
- constructor()
- static getDerivedStateFromProps()
- render()
- componentDidMount()

### Updating phase
- static getDerivedStateFromProps()
- shouldComponentUpdate()
- render()
- getSnapshotBeforeUpdate()
- componentDidUpdate()
- shouldComponentUpdate(nextProps,nextState)
- 
### unmounting phase
- componentWillUnmount()

## Functional Component Lifecycle

># `useEffect` hook
> ## useEffect
> `useEffect` is a React Hook for handiling side effects like API call or updating DOM in functional components.
>
>```javascript
> useEffect(()=>{
>   //implementation
>},[array of dependancy])
>```
>## variations of `useEffect` hook
>1. **No Dependancy** -  `useEffect` executes once after compount mounts and every time the component gets updated.
>   ```javascript
>       useEffect(()=>{
>         //implementation
>        })
>    ```
>   
>2. **An Empty Array** - `useEffect` executes once after component mounts.
>    ```javascript
>       useEffect(()=>{
>         //implementation
>        },[])
>    ```
>
>3. **Props or State** - `useEffect` executes once agter component mounts and every time the depedency value change
>   ```javascript
>       useEffect(()=>{
>         //implementation
>        },[count,list,isUpdated])
>    ```


> ## useState
> `useState` is a React Hook that let you add state to the functional components.
> 


[json-server](https://www.npmjs.com/package/json-server)
json-server is user to create api endpoints from json file


`axios`  api call library

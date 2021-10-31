[***Compass***](https://web.compass.lighthouselabs.ca/days/w07d5)

***[Instructor's Notes](https://web.compass.lighthouselabs.ca/activities/1013/lectures/4876)***

***[Today's Work: Scheduler Appointment Custom Hook](https://github.com/ShuhaoZQGG/scheduler)***

# Custom Hooks:

1. Rules:
    1. Don't call Hooks inside loops, conditions, or nested functions
    2. Only call Hooks from inside React components
    3. **A custom Hook is a function that must start with the word "use"**
    
2. How to build a custom hook:
    
    example:
    
    ```jsx
    import React, {useState} from "react";
    
    export default function useVisualMode(initial) {
      const [mode, setMode] = useState(initial);
      const [history, setHistory] = useState([initial]);
    
      function transition(next, replace = false) { 
        if (replace === true) {
          back();
          setMode(next);
          history.push(next);
          setHistory(history) ;
        } else {
          setMode(next);
          history.push(next) 
          setHistory(history)
        }
      }
    
      function back() { 
        if (history.length <= 1) {
          setMode(history[0])
        } else {
        history.pop(); 
        setMode(history[history.length-1]);
        }
      }
    
      return { mode, transition, back };
    }
    
    https://github.com/ShuhaoZQGG/scheduler/blob/master/src/hooks/useVisualMode.js
    https://github.com/ShuhaoZQGG/scheduler/blob/master/src/hooks/__tests__/useVisualMode.test.js
    ```
    
    This hook is allowed us to go forward or backward to the next or the last component by using to states mode and history
    

3. How to use a custom hook:
    
    ![Appointment Flow](https://s3-us-west-2.amazonaws.com/reactv2/figures/c665622e-5093-4552-8519-51b4f274cf21.png)
    
    example:
    
    ```jsx
    import React, {Fragment} from "react";
    import Header from "./Header"
    import Empty from "./Empty";
    import Show from "./Show";
    import Confirm from "./Confirm";
    import Status from "./Status";
    import Error from "./Error";
    import Form from "./Form";
    import useVisualMode from "hooks/useVisualMode";
    
    import "./style.scss";
    
    export default function Appointment (props) {
      const EMPTY = "EMPTY";
      const SHOW = "SHOW";
      const CREATE = "CREATE";
    
      const { mode, transition, back } = useVisualMode(
        props.interview ? SHOW : EMPTY
    
        // if (mode === EMPTY && transition(CREATE))
    
      );
    
      return (
        <article className="appointment">
        <Header time = {props.time}/>
        {mode === EMPTY && <Empty onAdd={() => transition(CREATE)} />}
        {mode === SHOW && (
         <Show
           student={props.interview.student}
           interviewer={props.interview.interviewer}
        />
        )} 
        {mode === CREATE && <Form interviewers = {props.interviewers} onCancel = {() => back()}/>}
        </article>
    
      )
    }
    
    https://github.com/ShuhaoZQGG/scheduler/blob/master/src/components/Appointment/index.js
    ```

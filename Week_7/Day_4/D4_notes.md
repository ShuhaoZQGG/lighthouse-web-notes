****Instructor's Notes (Not uploaded yet)****

****[Compass](https://web.compass.lighthouselabs.ca/days/w07d4)****

****Today's Work:****

[Scheduler](https://github.com/ShuhaoZQGG/scheduler/tree/master/src)

[Live Search For Album](https://www.notion.so/71ffbbe878220126aabc64cd05685ac9) ⇒ [Project Link](https://github.com/lighthouse-labs/album-search/tree/base)

1. ***UseEffect***
    1. The form: useEffect(() => { ... }, [ ... ])
    2. Inside the curly brackets we put funciton and inside the square brackets is the dependency state (run the function if the state is changed)
    3. The form to active two function in one onClick call in react: 
        
        `onClick={function(event){ func1(); func2()}}`
        
    4. prev holds the value of the state before the setState call is triggered
        
        example with non-prev vs. prev:
        
        ```jsx
        // Non prev => only increment 1 per click
        export default function App() {
          const [num, setNum] = useState(0);
        
          const addNum = () => {
            setNum(num + 1);
            setNum(num + 1);
            setNum(num + 1);
            setNum(num + 1);
            setNum(num + 1);
          };
        
          return (
            <div className="App">
              <h1>BAD BATCHING</h1>
              <h2>{num}</h2>
              <button onClick={addNum}>Add 5</button>
            </div>
          );
        }
        
        // Prev => increment 5 per click
        export default function App() {
          const [num, setNum] = useState(0);
        
          const addNum = () => {
            setNum((prev) => prev + 1);
            setNum((prev) => prev + 1);
            setNum((prev) => prev + 1);
            setNum((prev) => prev + 1);
            setNum((prev) => prev + 1);
          };
        
          return (
            <div className="App">
              <h1>GOOD BATCHING</h1>
              <h2>{num}</h2>
              <button onClick={addNum}>Add 5</button>
            </div>
          );
        }
        ```
        
    5. use clearTimeOut if there are multiple setTimeOut functions which make the app behaving "weird":
        
        ```
        useEffect(() => {
          if (likes > 0) {
            const timeout = setTimeout(() => setLikes(prev => prev - 1), 1000);
            return () => clearTimeout(timeout); // clears the timer set above
          }
        }, [likes]);
        ```
        
2. ***Axios***
    1. **Usage (Get / Post)**
        - `axios.get(url[, config])`
        - `axios.post(url[, config])`
        - `axios.put(url[, config])`
        - `axios.delete(url[, config])`
        
        ```
        axios.get("/api/appointments").then((response) => {
          console.log(response);
        });
        ```
        
        ```jsx
        axios
          .put(`/api/appointments/2`, {
            id: 2,
            time: "1pm",
            interview: {
              student: "Archie Cohen",
              interviewer: 9,
            },
          })
          .then((response) => {
            console.log(response);
          });
        ```
        
    2. **Errors**
        
        ```jsx
        axios
          .get("/api/appointments")
          .then((response) => {
            console.log(response);
          })
          .catch((error) => {
            console.log(error.response.status);
            console.log(error.response.headers);
            console.log(error.response.data);
          });
        ```
        
    3. **Use Axios inside UseEffect**
        
        ```jsx
        useEffect(()=> {
        	axios.get(url)
        			 .then((res) => {
        						console.log(res);
        				}
        }, [state])
        ```
        
3. ***Handle multiple useStates***
    1. **create multiple useStates with only one [state, setState]**
        
        Replace:
        
        ```jsx
        const [day, setDay] = useState('Monday');
        const [days, setDays] = useState([]);
        // you may not have the appointments state, its ok if you dont
        const [appointments, setAppointments] = useState({})
        
        ```
        
        With:
        
        ```jsx
        const [state, setState] = useState({
          day: "Monday",
          days: [],
          // you may put the line below, but will have to remove/comment hardcoded appointments variable
          appointments: {}
        });
        ```
        
    2. **Two techniques to setState**
        - **Spread Operator**
            
            ```jsx
            const state = { day: "Monday", days: [] };
            setState({ ...state, day: "Tuesday" });
            ```
            
        - **Object.assign**
            
            ```jsx
            const state = { day: "Monday", days: [] };
            setState(Object.assign({}, state, { day: "Tuesday" });
            ```
            
    3. **Aliasing Actions**
        
        `const setDay = day => setState({ ...state, day });`

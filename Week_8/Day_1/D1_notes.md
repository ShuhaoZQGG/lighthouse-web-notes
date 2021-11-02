## [Compass](https://web.compass.lighthouselabs.ca/days/w08d1)

## [Instructor's Notes](https://web.compass.lighthouselabs.ca/activities/1254/lectures/4878)

## [Today's Work](https://github.com/ShuhaoZQGG/scheduler/blob/master/src/hooks/useApplicationData.js)

### **Immutable Update Patterns**

1. **Copying an object using ... spread pattern**
    
    Example:
    
    ```jsx
    const original = { one: 1 };
    const bad = original;
    const good = { ...original };
    
    console.log(original === original); // true
    console.log(original === bad); // true
    console.log(original === good); // false
    ```
    
2. **Adding to an Object (...spread first and then add the value of key after the comma)**
    
    Example:
    
    ```jsx
    const original = { one: 1 };
    const copy = { ...original, two: 2 };
    
    console.log(original === copy); // false
    
    /* original */
    {
      one: 1
    }
    
    /* copy */
    {
      one: 1,
      two: 2
    }
    ```
    
3. **Update an Object (...spread first and then update the value of key after the comma)**
    
    Example:
    
    ```jsx
    const original = { one: 1, two: 3 };
    const copy = { ...original, two: 2 };
    
    console.log(original === copy); // false
    
    /* original */
    {
      one: 1,
      two: 3
    }
    
    /* copy */
    {
      one: 1,
      two: 2
    }
    ```
    
4. **Merging Multiple Objects**
    
    Example:
    
    ```jsx
    const first = { one: 1 };
    const second = { two: 2 };
    const copy = { ...first, ...second };
    
    console.log(copy === copy); // true
    console.log(first === copy); // false
    console.log(second === copy); // false
    
    /* first */
    {
      one: 1
    }
    
    /* second */
    {
      two: 2
    }
    
    /* copy */
    {
      one: 1,
      two: 2
    }
    ```
    

## CRUD (Create, Read, Update, Delete):

```jsx
// For update the data
axios.put(url, data)
		 .then(() => )
		 .catch(() => )

// For delete the data
axios.delete(url, data)
			.then(() => )
			.catch(() => )
```

The flow:

When we click some button in the front-end, the button will first trigger a function which has the axios method inside it. Axios will connect to the API url provided, then the data provided (optional, depends on how the backend is designed) will be sent to the backend router. Over there it will run the database query.  Inside Axios.then(), the state of react will be changed first (setState) and then the data will be sent to the backend.

Notes: 

1. remember to ***return** **axios method**, if it will be called in another function*
2. If the axios is returned in one function, it will make that function to be an async function, so it also has .then() and .catch() funcitonality. Therefore, noted that **don't use .catch() inside the axios but instead use it in the parent function** otherwise the error will be catched inside the axios and be returned as part of the .then(res)
    
    example:
    
    ```jsx
    function bookInterview(id, interview) {
        console.log(id, interview);
    
        const appointment = {
          ...state.appointments[id],
          interview: { ...interview }
        };
    
        console.log(appointment);
    
        const appointments = {
          ...state.appointments,
          [id]: appointment
        };
    
        setState({...state, appointments});
    
        //Update the API:id and setState
        return axios.put(`http://localhost:8001/api/appointments/${id}`, appointments[id])
             .then((res) => {
               setState({...state, appointments, days: spotsRemaininig(appointments)});
               console.log(res);
             })
            **//  .catch((err) => { 
            //    console.log(err);
            //   });**
      }
    
    function save(name, interviewer) {
        const interview = {
          student: name,
          interviewer
        };
        
        transition(SAVING);
    
        props.bookInterview(props.id, interview)
             .then(()=>transition(SHOW))
             .catch(err =>{
               console.log(err);
               transition(ERROR_SAVE, true);
             });
    
      }
    ```
    

## Adding Modes vs. Replacing Modes

If no error, we will first display "Loading..." and then display Show (async), here we only need to add modes

If error, we will first display "Loading..." and then display Error (async), here we only need to replace Loading by Error, otherwise when we try to goes back from Error to Form, we will end up go back to "Loading...".
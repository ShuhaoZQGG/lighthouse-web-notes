****[Compass](https://web.compass.lighthouselabs.ca/days/w07d3)****

****[[Instructor's Notes](https://web.compass.lighthouselabs.ca/activities/1149/lectures/4867)****[

****[[Today's work](https://github.com/ShuhaoZQGG/scheduler/tree/master/src/components/Appointment) and [StoryBook](https://github.com/ShuhaoZQGG/scheduler/blob/master/stories/index.js)****

1. When pass props from List down to ListItem, we can pass the argument inside the function so we don't have to pass an extra props (the argument ex. id, name). However, it only applies if we don't need to render the argument.
    
    Example:
    
    ```jsx
    // InterviewerList.js
    
    const interviewers = props.interviewers.map((interviewer) => {
      return (
        <InterviewerListItem
          key={interviewer.id}
          name={interviewer.name}
          avatar={interviewer.avatar}
          selected={interviewer.id === props.interviewer}
          setInterviewer={() => props.setInterviewer(interviewer.id)}
        />
      );
    });
    
    // InterviewerListItem.js
    
    return (
      <li className={interviewerClass} onClick={props.setInterviewer}>
        <img
          className="interviewers__item-image"
          src={props.avatar}
          alt={props.name}
        />
        {props.selected && props.name}
      </li>
    );
    ```
    

2. How to write stories in storybook:
    1. The `storiesOf` function is used with two parameters:
        - a `string` that labels a group of stories.
        - the `module` is a webpack module, which is available on the global (per-file) scope. If it's not included you'll need to refresh your browser with each change you make. Don't worry too much about this parameter.
        
        example:
        
        ```jsx
        storiesOf("Appointment", module)
        ```
        
    2. The `addParameters` function can be chained to `storiesOf` and can be passed an object of parameters. We will use the `backgrounds` property to set the Storybook preview background color to white.
        
        example:
        
        ```jsx
        storiesOf("Appointment", module)
        .addParameters({
            backgrounds: [{ name: "white", value: "#fff", default: true }]
          })
        ```
        
    3. chain the children components under the story of the parent component
        
        example:
        
        ```jsx
        storiesOf("Appointment", module)
          .addParameters({
            backgrounds: [{ name: "white", value: "#fff", default: true }]
          })
          .add("Appointment", () => <Appointment />)
          .add("Appointment with Time", () => <Appointment time="12pm" />);
          .add("Header"... // the rest of your code should go here);
        ```
        
        Summary for storybook:
        
        1. create a new component
        2. pass the props to the new component
        3. import it to the index.js of its folder
        4. import it to the index.js of stories
        5. chaining the .add(), pass the <Component /> and pass its props
        6. for the function props, do onFunctionName = {action("onFunctionName)}
        
        example:
        
        ```jsx
        storiesOf("Appointment", module)
              .addParameters({
                backgrounds: [{name: "white", value: "#fff", default: true}]
              }) 
              .add("Appointment", () => <Appointment />)
              .add("Appointment with Time", () => (
                <Appointment 
                  time = "12pm"
                />
              ))
              .add("Header", () => (
                <Header 
                  time = "12pm"
                />
              ))
              .add("Empty", () => (
                <Empty 
                  onAdd = {action("onAdd")}
                />
              ))
              .add("Show", () => (
                <Show 
                  student = "Lydia Miller-Jones"
                  interviewer = {interviewer.name}
                  onEdit = {action("onEdit")}
                  onDelete = {action("onDelete")}
                />
              ))
              .add("Confirm", () => (
                <Confirm 
                  message = "Delete the appointment?"
                  onConfirm = {action("onConfirm")}
                  onCancel = {action("onCancel")}
                />
              ))
        ```
        
    
    The higher level view of creating a component:
    
    - Create a file with our component name
    - Create & Export the component function
    - Add the base HTML in the return statement of our component
    - Create & Import a CSS / SCSS file holding the style of our component
    - Write stories for Storybook to render our component in isolation
    - Refactor the hard coded content to use props & state
    
3. be careful about the passed function props, whether the input is from the html input or from the passed in parameter
    
    example:
    
    ```jsx
    <section className="appointment__card-left">
        <form autoComplete="off" onSubmit={event => event.preventDefault()}>
          <input
            className="appointment__create-input text--semi-bold"
            name="name"
            type="text"
            placeholder="Enter Student Name"
            value = {student}
            interviewer = {interviewer}
            **onChange={(event) => setStudent(event.target.value)}**      
            />
        ****</form>
        <InterviewerList 
          interviewers = {interviewers}
          value = {interviewer}
          **onChange = {(id) => setInterviewer(id)}**
          /* your code goes here */
        />
      </section>
    ```
    
4. We can use ...spread to replace the key value pair in props
    
    example: 
    
    ```jsx
    <Appointment key={appointment.id} id={appointment.id} time={appointment.time} interview={appointment.interview} />
    <Appointment key={appointment.id} {...appointment} />
    ```

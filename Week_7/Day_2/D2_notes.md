[Instructor Notes](https://github.com/FrancisBourgouin/lectures-2021-east-sep13/tree/main/w7d2)

[Compass](https://web.compass.lighthouselabs.ca/days/w07d2) 

Before beginning the project, it's better to draw a react map to simulate the flow of each components and their props & states because react can only pass props and state from parents to children not the reverse

Storybook testing:

It's a framework used to isolate each component and test each's functionality.

We typically create a storied directory folder in the /src, and then write "stories" inside the index.js in the /src/stories

A typical story test:

```jsx
const interviewers = [
    { id: 1, name: "Sylvia Palmer", avatar: "https://i.imgur.com/LpaY82x.png" },
    { id: 2, name: "Tori Malcolm", avatar: "https://i.imgur.com/Nmx0Qxo.png" },
    { id: 3, name: "Mildred Nazir", avatar: "https://i.imgur.com/T2WwVfS.png" },
    { id: 4, name: "Cohana Roy", avatar: "https://i.imgur.com/FK8V841.jpg" },
    { id: 5, name: "Sven Jones", avatar: "https://i.imgur.com/twYrpay.jpg" }
  ];
  
  storiesOf("InterviewerList", module)
    .addParameters({
      backgrounds: [{ name: "dark", value: "#222f3e", default: true }]
    })
    .add("Initial", () => (
      <InterviewerList
        interviewers={interviewers}
      />
    ))
    .add("Selected", () => (
      <InterviewerList
        interviewers={interviewers}
        interviewer={3}
      />
    ))
    .add("Clickable", () => (
      <InterviewerList
        interviewers={interviewers}
        setInterviewer={action("setInterviewer")}
      />
    ));
```

Use Array.map() function to render a list of items

Pass the props to the next react component 

Example: 

```jsx
import React from "react";
import InterviewerListItem from "./InterviewerListItem";
import "./InterviewerList.scss";

export default function InterviewerList(props) {
  const {interviewers, setInterviewer, interviewer} = props;
  const InterviewerListItems = interviewers.map((eachInterviewer) => 
      <InterviewerListItem 
        id = {eachInterviewer.id}
        name = {eachInterviewer.name}
        avatar = {eachInterviewer.avatar}
        selected = {eachInterviewer.id === interviewer}
        setInterviewer = {setInterviewer}
      />
  )
  return (
    <section className="interviewers">
      <h4 className="interviewers__header text--light">Interviewer</h4>
      <ul className="interviewers__list">
        {InterviewerListItems}
      </ul>
    </section>
  )
}
```

Dynamically changing classes using the [classnames](https://github.com/JedWatson/classnames#usage) library combining with .scss files

examples:

```jsx
import React from "react";
import classNames from "classnames";
import "components/DayListItem.scss";

export default function DayListItem(props) {
  const DayListItemClass = classNames("day-list__item", {
    "day-list__item--selected": props.selected,
    "day-list__item--full": props.spots === 0
  });

  const formatSpots = () => {
      return (
      props.spots === 0 ? <h3 className="text--light">no spots remaining</h3> :
      props.spots === 1 ? <h3 className="text--light">{props.spots} spot remaining</h3> :
      <h3 className="text--light">{props.spots} spots remaining</h3> 
      )
    }

  return (
    <li className = {DayListItemClass} onClick={() => props.setDay(props.name)}>
      <h2 className="text--regular">{props.name}</h2> 
      {formatSpots()}
    </li>
  );
}
```

```scss
@import "styles/mixins.scss";
@import "styles/variables.scss";

.day-list {
  &__item {
    @include fade;

    color: #8395a7;
    height: 5rem;
    padding-left: 2rem;
    display: flex;
    flex-direction: column;
    justify-content: center;

    &:hover {
      background-color: #ee5253;
      cursor: pointer;
      color: $dark-background;
    }

    &--selected {
      background-color: darken($white, 5%);
      color: $dark-background;

      &:hover {
        background-color: darken($white, 5%);
      }
    }

    &--full {
      opacity: $inactive-opacity;
    }
  }
}
```
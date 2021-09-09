---
layout: page
title: "A Developer's Guide"
permalink: /front-end/developer-guide/
---

# A Developer's Guide

Overview
As the focus of the form is on data collection, state management was a key consideration in the design of the software. The idea was to make it as simple as possible to add to or remove state fields from the form if there were changes in the requirements of the study. As such, the software was implemented using a combination of class-based components and React state. 
For container components, a class-based component called <Form/> was used for ease of state management. For presentational components, functional components could have had been used over class-based components. However, I decided to use class-based components for presentational components. This was more of a preference rather than a design choice. I preferred to use class-based components life cycle methods rather than the useEffect() hook as the former was intuitive relative to the latter.
React state was used over Redux because of its simplicity in modifying state fields. Whenever new fields are added in Redux, actions, action creators, reducers, and dispatching methods have to be defined for the field, and mappings from state to props have to be done. This is unnecessarily time-consuming. On the other hand, if any React state changes are required, only a few lines of code have to be changed. Moreover, the small scale of the application does not justify the usage of Redux.
Software Design
Single-page Form
The front-end software is a single-page form called Form.js. Form.js is made up of five different pages - Introduction.js, UserDetails.js, Instruction.js, Quiz.js, and Email.js. Upon reaching the home page, Form.js is rendered. Users move from Introduction.js to Email.js as represented in blue in the above diagram. This is done by incrementing a “step” field as the user proceeds through Form.js.
Container and Presentational Components

Form.js and Email.js are container components that manage their own states. The reason for this design decision is because email submission for lucky draw/updates in Email.js is optional. Therefore, the survey results should immediately be submitted to the back-end upon reaching the Email page.
Event handlers are also defined in Form.js. Both the state and event handlers defined in Form.js are passed as props into the presentational components for state manipulation. As Email.js manages its own state, there are states and event handlers defined in Email.js as well. The aforementioned ideas are represented in red in the above diagram. 
Remarks: As there is a reCAPTCHA boolean field in Instruction.js to enable the “Continue” button once reCAPTCHA is verified, Instruction.js can be considered as a container component as well. However, I would still consider Instruction.js as a presentational component because the state managed in Instruction.js is trivial.

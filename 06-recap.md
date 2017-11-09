# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) React Recap

Don't worry - while there is a lot to see at first, React is a pretty straightforward framework to use. You can create user interface components that extend from `React.Component`. These have a built-in lifecycle that accepts data and can trigger automatic re-rendering whenever that data is updating. In a React Component, an update in either the State or Props will trigger the method cascade that can lead to a `render()`.

#### Best Practices

- Each component should be in a file unto itself. Don't put multiple components into one Javascript file.
- Do not automatically render elements on the DOM *inside* its own component class definition.
  - If you look through your files, you'll see in your component classes, you define a `render()` method for that component, which is great. That class then is called by `ReactDOM.render()` in **a different place, outside that class definition** (likely index.js).
  - In some tutorials or older code, you may find examples of `ReactDOM.render()` inside a component, but you should avoid this at all cost; this was an older technique in past versions of React.
- Don't ever let yourself think that State and Props are the same thing. They aren't!
  - Remember that `state` represents the _state_ of your user interface component.
  - State can trigger changes in `props`, or `props` can come from parent components.
- State **never** gets passed back up to parent components! Unidirectional flow means changes are only ever propagated down the component tree.

#### Last thoughts...

[A video on React in general.](https://generalassembly.wistia.com/medias/2qrtla3y8a)

Think of a few websites you've seen. Would they benefit from using React?

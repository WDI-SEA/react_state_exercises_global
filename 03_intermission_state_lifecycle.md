# ![](https://ga-dash.s3.amazonaws.com/production/assets/logo-9f88ae6c9c3871690e33280fcf557f33.png) State Recap


### Learning Objectives
*After this code-along section, you will be able to:*
* Describe the flow of methods in a component
* Identify the triggers for re-rendering of a component

## Review

Now that you've wrapped up the Blog project for now, you should take a moment to review the component lifecycle at a high level.

An example of a Post Component could be seen as follows:

```js
class Post extends Component {

  constructor(props) {
    super()
    this.state = {
      body: props.body
    }
  }

  changeBody(e) {
    let newBody = prompt("What should the new body be?")
    this.setState({
      body: newBody
    })
  }

  render() {
    return (
      <div>
        <h1>{this.props.title}</h1>
        <Author authorList={this.props.allAuthors[0]} />
        <div>
          <p>{this.state.body}</p>
          <button onClick={(e) => this.changeBody(e)}>Edit Body</button>
        </div>
        <h3>Comments:</h3>
        <Comment body={this.props.comments[0]} />
      </div>
    )
  }
}
```

In the `Post` component above, there are three methods:

- `constructor()`
- `changeBody()`
- `render()`

Upon instantiation of your component, the `constructor` method is called. It calls `super`, which is the base class (`React.Component`)'s constructor. Next, the component's initial state is set. Here we define that our component's state contains a `body` attribute whose value will start as whatever `body` prop was passed to the component.

Let's consider a data flow example.

1. Here's the code that kicks everything off:

  ```js
  <Post body="This is my first blog post" />
  ```

2. Inside of this post component, our constructor would essentially be saying:

  ```js
  constructor (props) { // props is { body: "This is my first blog post" }
    super()
    this.state = {
      body: props.body // props.body is "This is my first blog post"
    }
  }
  ```

3. Next, we define a listener in the JSX `<button>` element. This calls the `changeBody()` method `.onClick`. That is defined here:

  ```js
  <button onClick={(e) => this.changeBody(e)}>Edit Body</button>
  ```

4. When the _button_ is _clicked_, the `changeBody()` method is called.

  ```js
  changeBody (e) {
    let newBody = prompt("What should the new body be?")
    this.setState({
      body: newBody
    })
  }
  ```

  This method uses `prompt` to get a new value from the user (but please do not ever use `prompt` in production - users hate popups!).

  Then, `setState()` is called to update the component's state.  This will eventually lead to `render` being called to automatically re-render the component with the new data.

Understanding the component lifecycle is key to being a productive React developer (and it will save you headaches).

#### Check Yourself

When you `setState()`, what methods are fired? How are your `props` and `state` handled in the component? Draw this out or comment throughout your code.

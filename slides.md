# web team
### `<GatsbyWorkshop />`

---

# Review: React Components

### Diving into more React basics

***

# React Component

- The `render` method is the only required method
<!-- .element: class="fragment" -->

- Place everything you need to display within `render`
<!-- .element: class="fragment" -->

```jsx
class Counter extends React.Component {
  render() {
    return (<div>
      <h1>Your count</h1>
    </div>);
  }
}
```
<!-- .element: class="fragment" -->

***

# Using Components

- Components get rendered by importing them and using their JSX syntax
<!-- .element: class="fragment" -->

- This can occur by calling `ReactDOM.render` at the **top-level**, or by any child components of the root in _their_ `render` functions, i.e.:
<!-- .element: class="fragment" -->

```jsx
import Counter from './Counter';
class App extends React.Component {
  render() {
    return <Counter />;
  }
}
```

<!-- .element: class="fragment" -->

***

# Inline Exercise: About Me

[https://tinyurl.com/web-team-inline](https://glitch.com/edit/#!/react-inline-exercises)

Write a component that has some information about yourself inside of `src/AboutMe.js`!

Include your name in a heading, a picture of yourself (upload to the `assets` folder), and a little introduction blurb.

***

# Using Props

- Props are used to communicate values between **parents** and **children**.
<!-- .element: class="fragment" -->

- Props can allow your component to hold different values, depending on what your parent says
<!-- .element: class="fragment" -->

```jsx
import Counter from './Counter';
class App extends React.Component {
  render() {

    // startCount available to an instance of the 
    // Counter component as this.props.startCount

    return <Counter startCount={3} />;
  }
}
```

<!-- .element: class="fragment" -->

***

# Sending values as props

- `String` (no `{}` to go into JS context needed)

```jsx
<Counter message="Start count!" />
```
<!-- .element: class="fragment" -->

- `Number` (requires `{}`)

```jsx
<Counter startCount={3} />
```
<!-- .element: class="fragment" -->

- `Function` (requires `{}`) 

```jsx
<Counter onNextCount={(count) => alert(count)} />
```
<!-- .element: class="fragment" -->

- `Object` (2 sets of `{}` - why?)

```jsx
<Counter info={{ startCount: 3 }} />
```
<!-- .element: class="fragment" -->

***

# Inline Exercise: About Your Best Friends

Copy your `AboutMe` component `render` function into `src/AboutPerson.js`. Modify this code to display prop values instead of fixed values!

- _Reminder_: props can be accessed within a component instance through the `this.props` object.

- _Hint_: You'll need to edit `src/PeopleContainer.js` to pass down your props correctly!

***

# Managing state

- State is used to store a component instance's current internal data
<!-- .element: class="fragment" -->

```jsx
class Counter extends React.Component {
  constructor(props) {
    super(props);
    this.state = { count: props.initialCount || 0 };
  }
  onClick() {
    this.setState({ count: this.state.count + 1 });
  }
  render() {
    return (<div>
      <button onClick=(() => this.onClick())>Click!</button>
      <p>{this.state.count}</p>
    </div>);
  }
}
```
<!-- .element: class="fragment" -->

***

# Modifying state

- Never touch `this.state` to set it `=` to something! **It won't work.**
<!-- .element: class="fragment" -->

- Use `this.setState` to change what state is
<!-- .element: class="fragment" -->

- `setState` takes a single object as an argument and applies the _changes_ only.
<!-- .element: class="fragment" -->

***

# Inline Exercise: Deleting Your Best Friends

Open up `src/PeopleEditable.js` and implement deletion of friends from side buttons next to `<AboutPerson>` components!

**Bonus**: Add a text box next to `<AboutPerson>` components and allow them to modify the names of people.

---

# Enter Gatsby
### Or, the reason we're learning React in the first place

***

# Gatsby

- Static site generator for React
<!-- .element: class="fragment" -->

- Takes a React codebase and strips down features to make it efficient (it's a static site, after all)
<!-- .element: class="fragment" -->

- Adds built-in tools to make routing, paging, and pulling from external content sources _much, much easier_.
<!-- .element: class="fragment" -->

***

# Important Gatsby starter tips

- All components exported from JS files inside of the `src/pages` directory _become_ routes
  - i.e., `src/pages/about.js` is served at `[your url]/about`

<!-- .element: class="fragment" -->

- Use the `<Link>` component exported by `gatsby-link` for internal links (**not `<a>`**)
  - i.e., `<Link to="/about">About</Link>`

<!-- .element: class="fragment" -->

- Place components used by all pages (or a set of pages) in `src/layouts/`

<!-- .element: class="fragment" -->

***

# Where we're headed with Gatsby

- Export GraphQL queries from components to pull in data from external sources
<!-- .element: class="fragment" -->

- External data will be available to us as if passed in via `this.props` (!!)
<!-- .element: class="fragment" -->

- Integrating with different content management systems to fetch and display this external data
<!-- .element: class="fragment" -->

---

# Setting up for project work
### Did you try turning it off and on again?

***

# Install requirements

- Node.js (>= 6.x) - [https://nodejs.org](https://nodejs.org)

- Gatsby CLI - `npm i -g gatsby-cli`
  - If you don't like global dependencies, you can use `npm i -D gatsby-cli` and `npx gatsby` inside of a project folder to generate your starter code.

***

# External service requirements

- GitHub - sign up for an account and join the [InnoD-WebTier](https://github.com/InnoD-WebTier) organization

***

# Testing it all out

Create a repository on GitHub and push a new Gatsby starter project to it!

***

# Take-home assignment

Using this new Gatsby project,

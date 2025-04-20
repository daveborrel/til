# Lifecycle Methods

Each component is composed of three phases, the **mounting** phase, the **updating** phase, and **unmounting** phase.

### Mounting

Creating the component and inserting it into the DOM

Examples Include

- constructor()
- render()
- componentDidMount()

### Updating

Occurs when there is a change in props or state and component needs to be updated in the DOM

- shouldComponentUpdate()
- componentWillUpdate()
- componentDidUpdate()
- getSnapshotBeforeUpdate()

### Umounting

When the component is being removed from the DOM and is no longer rendered or accessible

- componentWillUnmount()

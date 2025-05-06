# Adding a className into a functional component

Lets say that you have a `Card` component, and you want to create a css file that handles styling. Just add it as a tag into the main div or anywhere else that you want those changes to be in.

```ts
function Card({ cat }: CardProps) {
  return (
    <div className="card">
      <img src={cat.url}></img>
      <h1>{cat.name}</h1>
      <h2>
        {cat.breed + " *"}
        {cat.age + " years"}
      </h2>
      <p>{cat.description}</p>
    </div>
  );
}
```

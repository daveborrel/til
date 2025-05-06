# Creating a 2 x 3 Grid with Resizing the images

In order to create a 2 x 3 grid you'll need to create a css file with 3 components.

Given this

```ts
return (
  <div className="container">
    {data.slice(0, 6).map((item) => (
      <Card key={item.id} image={item.image} title={item.title} />
    ))}
  </div>
);
```

You'll need the following css

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 columns */
  gap: 1em; /* gap between rows and columns */
}

.card {
  /* Styling for each card itself */
  border: 1px solid #ccc;
  padding: 1em;
  text-align: center;
}

.card img {
  /* Styling for individual card */
  width: 100%;
  height: 150px;
  object-fit: cover; /* Ensures the image fills the space without distortion */
  border-radius: 8px;
}
```

**Grid Component**
`fr` - fractional unit.
`repeat(3, 1fr)` - create 3 columns, and each column should tak eup 1 fraction of the available space.

**Image Resizing**
`width: 100%;` - will scale image to fit entire width of its parent card
`height: 150px;` - caps the image height of all images
`object-fit: cover;` - scale yourself to fit the height and width even if it crops.

This should result in:
![image](/css/assets/2x3_grid.JPG)

### Sources

[grid-template-columns](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-columns)

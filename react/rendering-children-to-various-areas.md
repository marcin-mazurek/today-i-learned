# Rendering children to various areas in React

React has a special prop `children`, which you can use to provide some content. Most tutorials show just a simple use like:

```
const Header = ({ children }) => <h1>{children}</h1>;

const App = () => <Header>Hello!</Header>
```

But the `children` prop can be much more powerful, if you combine it's potential with a bit of pure JS.

You can build the following interface:

```
<Card>
   <CardTitle>Hello!</CardTitle>
   <CardContent>Hello world!</CardContent>
   <CardActions><Button>Hide</Button></CardActions>
</Card>
```

... and still have full control over where you render your content. You just need to convert your children to an array
and extract the needed elements by the type:

```
import { CardTitle, CardContent, CardActions } from '....';

function Card ({ children }) {
  const children = React.Children.toArray(children);
  const title = children.find(c => c instanceof CardTitle);
  const content = children.find(c => c instanceof CardContent);
  const actions = children.find(c => c instanceof CardActions);
  
  return (
    <div>
      <h3>{title}</h3>
      <p>{content}</p>
      <form>{actions}</form>
    </div>
  );
}
```

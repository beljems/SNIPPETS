# REACT
```sh
create-react-app

Command - npx create-react-app [FOLDER_NAME]

Repo
[https://github.com/facebookincubator/create-react-app](https://github.com/facebookincubator/create-react-app)
```

## Why JSX
```sh
-how events are handled
-you can change the data
-handling of data are separated properly```

### What are valid expresions in javascript ?
```sh
Arithmetic - numbers
Strings
Logical - true or false
Primary - like variables
Functions
Ternary operators```

### Embedding Expressions
```sh
{1+2}

Do not enclose expressions
src=“{src}” - NG
src={src} - G

In JSX className
ES6 uses class

JSX Children
If no content,

<div></div> - NG
<div /> - G

-

Safe Embedding

Let html = ‘<b>Bold</b>’

Let element = (
<I>{html}</I>
)
```

## Two types ( Functional and Class components)
### Functional
```sh
Function Hello(props) {
	return <div>Hello {props.name}</div>
}```

### GET CURRENT ITEM
```sh
  const [active, setActive] = useState('');

  const handleClick = (key) => setActive(key);

  return (
    <div className={`hide${item === active ? ' is-active' : ''}`}>
       {box}
    </div>
  }
```

### Class
```sh
Class Hello extends React.Component {
	return <div>Hello {props.name}</div>
}
```

### Sample of Array Push
```sh
.pop // remove last item
.push // add item```

```sh
const article = {
    image: articleImage,
    time: '2019.06.19',
    desc: 'サンプルテキストサンプル ルテキストサンプルテキストサンプルテキストサンプル ルテキスト'
}

const articleData = [];

for(let i=1; i<=6; i++) {
    articleData.push(
        <li className="news-item">
            <Article
                key={i}
                image={article.image}
                time={article.time}
                desc={article.desc}
                link={`/article-${i}`}
            />
        </li>
    )
}
```

### Handle CLICK
```sh
const handleClick = () => {
    quizItemCount();
    setQuizItem([
      ...quizItem,  // old array
      <Quiz count={quizCount} /> // this will add the old array
    ]);
  }
```



## REACT ROUTER
-Transfer to different page
[https://reacttraining.com/react-router/web/api/Link](https://reacttraining.com/react-router/web/api/Link)
(https://knowbody.github.io/react-router-docs/api/Link.html)

```sh
When to use Link ?
-use link for internal links
-then use a tag if there are external links
```

## REACT REDUX a library
[https://github.com/erikras/ducks-modular-redux](https://github.com/erikras/ducks-modular-redux)

```sh
Sample

Import { Provider } from react-redux;

<Provider store={store}>
  <App />
</Provider>

Reducer - talk to store
It Is pure function

Post reducer - talk to store
User reducer -

Action - payloads of information
The source of information to store

Two types
Action type
get user, set user

Thunk - to create side effects
```

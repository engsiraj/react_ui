# React ui guide.

making react js easier a bit with best practice.


- [installation](#installation)
- [folder structure](#folder-structure)
- [cascading style sheet](#cascading-style-sheet)
- [styled components](#styled-components)


## installation

although react js is Javascript frontend libarary. there are some pre requirement for learning libarary like basics of `html`, `css`, `dom`,`es6`, `node` and `npm`.you don't need to master them all.

react js takes some time for installation so you can use [vite](https://vitejs.dev/guide/) instead of installing react. it will save your time and provide more features too.

```
npm create vite@latest
```
## folder structure

your project folder structure based on few things like: size,complexity and technologies used in project. 
here is how you can structure your files when you have,

- small project

```
src/
├── asset/
│   └── projectimage.png
│
├── pages/
│    ├─ landing/
│    │   ├── LandingPage.jsx
│    │   └── Landing.css
│    └─ contact/
│        ├── Contact.jsx
│        └── Contact.css
│
└── components/
    ├─ button/
    │   ├── Button.jsx
    │   └── Button.css
    └─ card/
        ├── Card.jsx
        └── Card.css
```
- large project

```
src/
├── asset/
│   └── projectimage.png
│
├── pages/
│    ├─ landing/
│    │   ├── LandingPage.jsx
│    │   └── Landing.css
│    └─ contact/
│        ├── Contact.jsx
│        └── Contact.css
│
├── components/
│    ├─ button/
│    │   ├── Button.jsx
│    │   └── Button.css
│    └─ card/
│        ├── Card.jsx
│        └── Card.css
│   
├── routs/
│   ├── Component.jsx
│   └── Pages.jsx
│  
└── services/
    ├── Actions/
    ├── Reducers/
    ├── Utils/
    └── Consts/

```
## cascading style sheet

## styled components

1 - install styled-components using npm.

```
npm install styled-components
```

2 - importing styled components `App.jsx` as:

```js
import styled from "styled-components";

const Title = styled.h1`
  font-size: 20px;
`;
return <Title>style title</Title>;
```

3 - extending styles

```js
const Title = styled.h1`
  font-size: 20px;
  color: black;
`;
const RedTitle = styled(Title)`
  color: red;
`;
return (
  <>
    <Title>style title</Title>
    <RedTitle>this is extended title</RedTitle>
  </>
);
```

4 - props

```js
const Button = styled.button`
  background-color: {
    props=>props.bg==="black"?"black": "blue";
  }
`;
return (
  <>
    <Button bg="black">Login</Button>
    <Button bg="blue">Login</Button>
  </>
);
```

5 - nesting

```js
const Container = styled.div`
border : 1px solid white;
margin : 20px;
p{
  font-size: 20px;
  color: red;
  &:hover{
    color:blue;
  }
  &::after{
    content:"__"
    color:red;
  }
}
`;
```

6 - animations

```js
import styled, { keyframes } from "styled-components";

const SlideIn = keyframes`
from{
  opacity:0;
  }
to{
  opacity:1;
}`;
const Toast = styled.div`
  animation: ${SlideIn} 0.5sec cubic bazier(0.4, 0, 0, 0.2, 1) both;
  border-radius: 5px;
  padding: 20px;
`;
```

7 - Global styles

```js
import { createGlobalStyle } from "styled-components";

const GlobalStyles = creatGlobalStyle`
// All css reset will be placed here. 
`;
return (
  <>
    <GlobalStyles />
    <App />
  </>
);
```





<!-- 

## import and exports

imports and export are JavaScript concept its came in use in es6 update.

### components

we have to create file `index.js/ts/jsx` to add exports in components folder.

```js
//export your component as index.js/ts/jsx file.

export { default as ChannelCard } from "./ChannelCard";
export { default as VideoCard } from "./VideoCard";
export { default as ChannelDetail } from "./ChannelDetail";
export { default as Feed } from "./Feed";

//import from your component as index.js/ts/jsx file.

import { ChannelCard, VideoCard, ChannelDetail, Feed } from "./";
```

### files and links

we have to create file `utils/constant.js/ts/jsx` to export components.

```js
// mui components
import MusicNoteIcon from "@mui/icons-material/MusicNote";
import HomeIcon from "@mui/icons-material/Home";
import CodeIcon from "@mui/icons-material/Code";
import OndemandVideoIcon from "@mui/icons-material/OndemandVideo";
import SportsEsportsIcon from "@mui/icons-material/SportsEsports";
//logo.png link
export const logo = "https://i.ibb.co/s9Qys2j/logo.png";
//react icons
export const categories = [
  { name: "New", icon: <HomeIcon /> },
  { name: "Coding", icon: <CodeIcon /> },
  { name: "ReactJS", icon: <CodeIcon /> },
  { name: "NextJS", icon: <CodeIcon /> },
];
// links url
export const demoThumbnailUrl = "https://i.ibb.co/G2L2Gwp/API-Course.png";
export const demoChannelUrl = "/channel/UCmXmlB4-HJytD7wek0Uo97A";
export const demoVideoUrl = "/video/GDa8kZLNhJ4";
//import from your component as utils/constant.js/ts/jsx file.
import {
  demoThumbnailUrl,
  demoVideoUrl,
  demoVideoTitle,
  demoChannelUrl,
  demoChannelTitle,
} from "../utils/constant";
```

### maping through array

```js
// importing images
import post1 from "assets/post1.png";
import post2 from "assets/post2.png";
import post3 from "assets/post3.png";
import post4 from "assets/post4.png";
import post5 from "assets/post5.png";
import post6 from "assets/post6.png";
// adding to the array
const posts = [post1,post2,post3,post4,post5,post6,];
// maping array in the  div
posts.map((post, index) => <div key={`post-${index}`} src={post} />
```

## destructuring

### destructuring props

there are many ways to destructure props in JavaScript. we will explore few of them.

1 - props without destructuring.

```js
//Props without destructuring - function recieve props as parameter.
function Product(props) {
  return (
    <div>
      <img src={props.img} alt="products" />
      <h4>{props.name}</h4>
      <p>{props.description}</p>
      <h4>{props.price}</h4>
    </div>
  );
}
export default Product;
```

2 - function recieve props as parameter

```js
function Product = (props) => {
//destructuring props in the body of function.
    const { img, name, desc, price} = props;
    return (
      <div>
      // props usage.
      <img src={img} alt="products"/>
        <h4>{name}</h4>
        <p>{description}</p>
        <h4>{price}</h4>
      </div>
    );
}
export default Product
```

3 - function recieve props to destructure

```js
//destructuring in function's parameter
function Product = ({ img, name, desc, price}) => {
    return (
      <div>
      // props usage.
      <img src={img} alt="products" />
        <h4>{name}</h4>
        <p>{description}</p>
        <h4>{price}</h4>
      </div>
    );
}
export default Product
```

usage of props from product functuion

```js
<Product
img="https://ng.jumia.is/unsafe/fit-in/300x300/filters:fill(white)/product/82/6142201/1.jpg?2933"
name="Cyxus"
desc="Non-Slip Fitness Leisure Running Sneakers"
price="$29"
/>
<Product
img="https://ng.jumia.is/unsafe/fit-in/300x300/filters:fill(white)/product/01/241417/1.jpg?6747"
name="Vitike"
desc="Latest Men Sneakers -Black"
price="$100"
/>
<Product
img="https://ng.jumia.is/unsafe/fit-in/300x300/filters:fill(white)/product/06/4410121/1.jpg?4437"
name="Aomei"
desc="Men's Trend Casual Sports Shoe"
price="$40"
/>
```

### pro tips

- create a good folder-structure.
- keep your key prop unique across the whole app.
- don't use inline-styles.
- use functional components (like arrow-functions).
- maintain a proper import structure (third-party imports first  internal imports below).
- Maintain a structured import order.
- format your code before committing.

### author

errors are expected if you find one report it to the [author](https://twitter.com/engsiraj_).
 -->

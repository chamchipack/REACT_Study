# 1. 변수 옮겨오기
### (1) 함수형 컴포넌트
```
// App.js
import { useState } from 'react';

function App() {
  let[변수, 변수바꿈] = useState('Hello World')
  return(
    <div>
      <컴포넌트 새로운변수 = {변수}/>
    </div>
  )
}

// Component.js
function Component(props){
  let content = props.새로운변수
  return(
    <div>
      <p>{content}</p>
      <p>{props.새로운변수}</p>
    </div>
  )
}
```
#### 변수를 넘기면서 새로운 변수명으로 잡아주는 것에 주의

### (2) 클래스형 컴포넌트
```
function App() {
  let[변수, 변수바꿈] = useState('Hello World')
  return(
    <div>
      <컴포넌트 새로운변수 = {변수}/>
    </div>
  )
}

// Component.js
class props extends Component{
  render(){
    let value = this.props.새로운변수
    return(
      <div>{value}</div>
    )
  }
}
```

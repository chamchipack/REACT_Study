# 리액트 기본 개념
## 1. 선언형 프로그래밍과 명령형 프로그래밍
리액트 공식페이지에 들어가면 가장 먼저 마주치는 단어는 '리액트는 선언형이다' 라는 문구이다. 초심자의 입장에서 선언형이 무엇이고 그와 대척점(?)에 있는 명령형은 무엇인지 기본부터 알아갈 필요가 있었다.  
많은 개발 블로거분들이 말씀하시는 선언형과 명령형의 차이는  
#### 선언형 프로그래밍은 무엇을 할것인가 ( what )
#### 명령형 프로그래밍은 무엇을 어떻게 할것인가 ( how )
였다. 단순히 무엇과 어떻게 라는 차이로는 이해할 수 없었지만 여러 예시들을 통해서 어느정도 감을 잡아갈 수 있었다.
https://boxfoxs.tistory.com/430 박스여우님이 원문을 번역하여 설명해주신 블로그를 통해 자세히 알수있다. 
즉 명령형은 마트에서 집으로 어떻게 갈것인지 루트를 일일이 지정해주는것이다. 여기서 왼쪽 저기서 오른쪽으로 가도록 어떻게 갈 것인지 명령을 해주는 것이다
반대로 선언형은 우리집 주소를 정의해주기만 하고, 어떻게 갈것인지에 대한 부분은 추상화가 되어있는 것이다.  

물론 선언형도 기본 베이스로 명령형이 추상화가 되어있어야 하는것은 명백한 사실이다. 하지만 명령형의 일련의 과정들이 생략된다면 코드는 간단해질것이고, 가독성 또한 높아질 것이다.

## 2. 컴포넌트
컴포넌트는 독립적인 단위의 소프트웨어 모듈을 말한다. 즉 소프트웨어를 독립적인 하나의 부품으로 만드는 방법이다. 리액트는 웹에서 쓰는 각 요소들을 컴포넌트로 만들 수 있게 해 기존의 UI를 다른 화면에서 다시 쓰거나, 다른 프로젝트에서 다시 쓸 수 있도록 하는 재사용성을 가진다.

컴포넌트를 정의하고 관리하는것은 자바스크립트 파일에서 하기때문에 모든 템플릿을 손댈 필요가 없고 용이하다. 컴포넌트는 웹사이트를 조각내는것이다. 그렇다면 궁금한건 어디서부터 어떤 범위까지를 나눠서 컴포넌트화를 시켜야 할까?

## 3. 가상 돔 (Virtual Dom)
DOM 이라는것은 스크립트 언어를 사용하여 document 객체를 통해 HTML 등의 문서에 접근할 수 있도록 도와주는 것이다. 자바스크립트 언어를 통해 객체를 손대어 변화가 일어나면 브라우저가 CSS 등을 연산하여 
페이지를 다시 그려내는, 렌더링을 하는 작업이 일어난다.

그렇다면 가상 돔이라는것은 무엇일까? 아직 정확하게 이해하진 못했지만 돔을 지속적으로 사용하면 렌더링이 많이 일어나기 때문에 실제 낭비되는 렌더링을 줄이기 위해 가상돔으로 여러차례의 렌더링과정을 거치고 렌더링이 마무리
되면 최종적으로 실제 렌더링을 진행하여 실질적으로는 1회의 렌더링만 동작하게 하는것이라고 이해하고 있다. 가상돔을 사용하면 실제 돔에 접근하여 조작하는것이 아닌 가상으로 조작하여 불필요한 렌더링 횟수를 줄일 수 있다고 한다.

## 4. CSR과 SSR
#### Client Side Rendering
클라이언트에서 렌더링을 진행하는 것이다. 서버는 요청을 받으면 HTML과 JS를 클라이언트로 보내어 그곳에서 렌더링을 진행한다. 
#### Server Side Rendering
서버에서 렌더링을 마치고 클라이언트에 전달하는 방식이다. 서버는 HTML 파일을 렌더링 가능하게 하고 클라이언트에 전달하면 HTML은 렌더링이 된다. 그 후 자바스크립트를 다운받아 실행한다. 자바스크립트가 다운받는 동안에는
HTML 화면은 볼 수 있으나 동작은 할 수 없다.

## 5. 라이프사이클
아직 상당히 헷갈리는 개념이다. 라이프사이클은 컴포넌트가 생성, 수정되거나 제거될 때 발생하는 이벤트의 개념인듯 하다. 이러한 일련의 과정들을 거치는 중 하고싶은 일들을 동작하게 하는것이다. 
![image](https://user-images.githubusercontent.com/90598408/158525302-171a1b5c-5203-4ea1-85c5-9d9ac1f557a7.png)

클래스형 컴포넌트에서는 위에 함수들을 사용하여 조작이 가능하다. 함수형에서는 훅이라는 것을 이용하여 사용할 수 있다.

## 6. 훅
#### Side Effect
React 컴포넌트가 화면에 1차로 렌더링된 이후에 비동기로 처리되어야 하는 부수적인 효과들을 흔히 Side Effect라고 한다.
예를들어 데이터를 가져오려고 외부 API를 호출할 때, 일단 화면에 렌더링할 수 있는 것은 1차로 먼저 렌더링하고 실제 데이터는 비동기로 가져오는 것이 권장된다. 왜 먼저 렌더링하냐면 연동된 API가 응답이 늦거나 없을 때 데미지(답답함)을 최소화 시켜 사용자 경험 측면에서 유리하기 때문이다.


#### 훅을 사용하는 이유
기존의 클래스형 컴포넌트에서는 컴포넌트간 상태로직 교환이 자유롭지 못했다고 한다. 또한 componentDidMount 와 같은 라이프사이클 메소드들은 버그가 쉽게 발생하고 무결성을 해친다는 단점이 있다. 이러한 단점들을 보완하기위해 함수형 컴포넌트에서 훅을 이용해 단점을 상쇄한다.
컴포넌트의 라이프사이클 중간중간 훅을 걸수 있다. 예를들어 컴포넌트가 생성되기 전에 혹은 삭제되기 전에 A라는 행동을 해달라는 훅을 걸 수 있는것이다. 
#### useEffect
렌더링이 된 후 처리되는 훅이다. 이게 있으면 해당 컴포넌트가 화면 렌더링이 된 후에, 혹은 업데이트 된 후에 실행되는 것이다. useEffect는 클래스형의 componentDidMount(최초렌더링시)
componentDidUpdate(렌더링 후 업데이트시)를 합친 형태로 본다고 한다.  
- state의 setState로 변경시 useEffect가 한번더 실행이된다.
- 만약 A와 그의 자식컴포넌트가 B -> C -> ... 이런식으로 진행될때 C의 useEffect가 가장먼저 실행되고 역으로 올라가면서 B -> A useEffect가 실행된다.
- useEffect 훅이 자동으로 실행되지 않게 하려면?? : 해당 변수명의 로직이 작동할때만 useEffect가 아래 코드와같이 작동한다. 연속적 컴포넌트일때도 해당 컴포넌트의 useEffect는 실행이 안된다.
```
useEffect(()=>{
  ...로직
}, [변수명])
```
![image](https://user-images.githubusercontent.com/90598408/159205299-5f25b829-2a5f-496e-9d83-a479c1151f4b.png)

#### useEffect로 componentwillUnmount (컴포넌트가 사라질때) 효과 내기
```
useEffect(()=>{
    console.log('컴포넌트 등장') 1번
    return ()=>{
      console.log('컴포넌트가 사라질때') 2번
    }
  })
```
이런식으로 코드를 구성하면 컴포넌트가 등장할 때 1번 콘솔이 찍히게 되고, 컴포넌트가 사라질 때 즉, 다른화면으로 옮겨간다거나 할 때 2번이 찍힌다
<img width="158" alt="스크린샷 2022-03-30 오후 1 01 55" src="https://user-images.githubusercontent.com/90598408/160748982-23031e9f-0479-4dd1-bc1d-e78298c4bf6e.png">


## 7. 리덕스
#### 전제
- 리액트는 부모 컴포넌트의 데이터를 자식 컴포넌트가 props를 받아서 사용 가능하다. 이것이 지속적으로 이어지는 것을 두고 프롭스 드릴링이라고 한다. 물이 위에서 아래로 흐르듯 데이터도 부모에서 자식으로 흘러야지 자식에서 부모로 흐르는것은 지양해야 한다.
- 이와같이 리덕스를 통해서는 자식 컴포넌트에서 부모데이터를 수정하는 것은 좋은 것은 아닌데 이러한 상황이 발생했을때 어떤 State를 마치 중립상태로 두고 부모의 state는 건드리지 않으면서 그 변수를 수정할 수 있게 할수있다.
- 또한 props drilling이 일어날때 만약 최하위 자식 컴포넌트만 최상의 부모의 데이터를 사용한다면 나머지 사이에 껴있는 컴포넌트들은 낭비가 될것이다. 그럴때에 리덕스로 관리해줄 수 있다.
- 상태관리를 해주는 라이브러리인데, 메시징시스템? 커맨드? 페이로드? 개념들 CQRS / 앱이 복잡해지는걸 방지하기 위해 CQRS 개념을 도입한다. 

## CQRS
CQRS는 `Command and Query Responsibility Segregation`(명령과 쿼리의 책임 분리)을 말한다.
리덕스에게 커맨드(명령)와 쿼리는 무엇일까? 예를들어 리덕스에게 스테이트를 변경하는 등의 이벤트가 발생했다고 명령을 던지면 페이로드도 동시에 발생한다고 한다. 페이로드는 함수와 같다고 이해하면 되는데, 이런 이벤트가 발생했다고 명령을 던지면 리덕스에게 던지면 리덕스는 알아채고 리덕스에 정의된대로 쿼리를 진행한다.

즉, 리덕스에게 명령을 주는 부분과 쿼리가 진행되는부분이 명확히 분리가 된다는 의미이다.이렇게되면 어떤동작을 수행할 때 그 명령이 다 기록이 될것인데, 깃의 로그를 추적하듯이 그 명령이 쌓인 순서대로 역으로 돌릴수가 있다. 그렇게되면 관리도 용이해질뿐더러 버그를 찾는데에도 도움이 된다고 한다.

#### 리덕스 용어
State : 현재 데이터의 상태라고 이해하면 쉽다. 조금더 정확히 말하자면 리덕스에서 저장하고있는 상태값이다  
ActionCreator : 실제 행동(변경, 로딩 등)을 하기위해서 만드는 함수이다  
Reducer : 실제 데이터의 변경이 일어나는 곳이다. 액션 생성함수를 부르고 → 액션을 만들면 → 리듀서가 현재 상태(=데이터)와 액션 객체를 받아서 → 새로운 데이터를 만들고 → 리턴해줍니다.  
Store : 데이터가 담겨있는 곳  
dispatch : 액션을 발생시키는 함수 (동작을 유발함)  

#### 리덕스 설치
npm i redux  
npm i react-redux  
npm i -D redux-devtools

#### 리덕스 파일구성은 파일하나 따로 파뒀으니 거길 확인해라

## 8. 리액트 key
리액트를 사용하는 중 map 함수로 출력을 진행하다보면 key에 대한 경고문이 콘솔창에 띄워지는걸 자주 확인할 수 있다. 그렇다면 key값은 왜 주는것일까?
#### 변경사항을 알아차리기 위해서 필요함
key는 어떤 아이템이 변화하거나 추가, 삭제되었는지를 알아차리기 위해 필요하다고 말한다.

많은 개발 블로거들을 참고한 결과, 리액트는 State에서 변경사항이 있는 부분만 캐치해서 다시 랜더링을 한다. 즉, 바뀐게 없는 데이터까지 DOM을 조작해서 불필요한 자원을 낭비하지 않겠다는 것이다. 예를들어 state 배열에 어떤 요소가 추가되면 배열에 추가된 한가지 요소만 리랜더링을 한다. 다만 배열의 key값을 제대로 넘겨주었을 때 만이다.

#### index값으로 하면 안되는 이유는?
```
[
{index : 0, content : 'first'}
{index : 1, content : 'second'}
{index : 2, content : 'third'}
]

```
위와같이 배열이 존재할 때 만약 새로운 요소가 배열안으로 추가될 때 인덱스의 첫번째로 들어가게 되면 리액트는 기존 값들의 key와 value값이 변경된 것으로 착각하기때문에 배열 전체가 바뀐것으로 판단한다. 이는 삭제할때도 마찬가지일수도 있다.

## 9. 스타일 컴포넌트
기존에 CSS를 사용하듯이 class, id를 가져와 쓰지 않고, 컴포넌트를 생성하여 스타일값을 지정하여 쓰는 것을 말한다. 즉, 리액트에서 ui단위를 나누어 컴포넌트화 하듯, 스타일을 컴포넌트화 하여 재사용이 가능하다. 그리고 `export`를 사용하여 유사한 스타일을 사용하는 다른 컴포넌트에도 재사용이 가능하다
#### 예시
```
export const Background = styled.div` div, input 등 많이 들어감
    margin: 0 auto;
    width: 30%;
    height: 70%;
    padding: 50px;
`
<Background>
	... 안에 뭐있다
</Background>
```
#### 설치
`npm install styled-components` 설치 및  
`import styled from 'styled-components'`

## Grid
리액트에서 스타일컴포넌트와 같이 적용할 수 있는 요소이다. Input, Image, Button 등 요소들은 컴포넌트화를 시켜서 사용하는 예가 있다.

> npm install styled-components ;
npm install @material-ui/core @material-ui/icons

```
import styled from 'styled-components';
// elements 폴더로 스타일 컴포넌트 파일들을 한데 묶어주자

function Grid(props){
1번	const { is_flex, width, margin, children ...} = props;
2번  const styles = {
		is_flex : is_flex,
        width : width,
        ...
	};
3번  return (
    	<>
        	<GridBox {...styles} onClick={_onclick}>{children}<GridBox>
    	</>
    )
};
```
먼저 Grid 라는 값의 디폴트값을 4번에서 선언해준다. 그렇게 선언한 것들을 1번에서 동일하게 선언해 준다. 5번의 값들은 본격적으로 스타일링을 해주는데, 사용자가 직접 적용한 값이 적용될 수 있도록 props를 넣어서 해당컴포넌트에서 사용할 때 적용 되도록 한다.
```
위에 이어서...
4번 Grid.defaultProps = {
      chidren: null,
      is_flex: false,
      width: "100%",
      bg : false
      ...
      _onClick: () => {}
};

5번
const GridBox = styled.div`
  width: ${(props) => props.width};
  height: 100%;
  box-sizing: border-box;
  ${(props) => (props.margin ? `margin: ${props.margin};` : "")}
  ${(props) => (props.bg ? `background-color: ${props.bg};` : "")}
  ${(props) =>
    props.is_flex
      ? `display: flex; align-items: center; justify-content: space-between; `
      : ""}
    ${(props) => (props.center ? `text-align: center;` : "")}
`;

export default Grid;
```

```
실제 적용된 모습
<Grid
    padding="16px"
    is_flex
    bg="#fffff
    margin="8px 0px"
    _onClick={() => {history.push(`/post/${post_id}`);}}>
```


## 10. useMemo
컴포넌트 최적화를 위해서 사용되는 훅이다. 즉 컴포넌트의 성능을 늘리기 위해서 사용한다. Memoization이란 `동일한 값을 리턴하는 함수를 반복해서 출력할 때` 연산을 계속하게 하면 낭비가 될 것이다. 그래서 필요할때마다 연산을 하지 않고 캐시에서 꺼내다 쓰는것을 의미한다. 
>처음에 계산된 계산값을 메모리에 저장하여 렌더링이되어도 다시 연산을 하지 않고 값을 가져와서 재사용을 하는 것 이다.

```
const value = useMemo(()=>{
    return calculate()
},[item])
```
언제쓸까? 동일하고 반복된 연산을 하는 함수에 사용하면 될 것 같다.

## 11. useReducer
여러가지의 복잡한 하위값을 갖는 state를 쓸때 useReducer를 사용한다. dispatch, reducer, action 세가지로 나뉜다. Dispatch는 하나의 명령이다. 어떤 동작을 하게 해달라는 명령을 하면 명령의 내용이 담긴 Action을 담아서 Reducer에게 보내준다. Reducer는 명령을 받아서 받아서 수행하는 역할을 한다. Action에는 여러가지의 명령 (삭제, 생성 등)을 지정해줄 수 있다


## 12. useCallback

## 13. input으로 파일 업로드
```
<input type="file" onChange={selectFile} ref={fileInput}/>
```
input의 타입이 file 이면 파일을 업로드 할 수 있는 input으로 바뀌어서, 로컬환경에서 업로드 할 수 있다. 그리고 이를 리덕스에 보내주기 위해서는 내장함수(?)를 사용해야한다.
```
const selectFile = (e) =>{
    const reader = new FileReader();
    const file = fileInput.current.files[0];
    reader.readAsDataURL(file);
    reader.onloadend = () => {
        imageFile = reader.result;
        console.log(imageFile)
        setFiles(imageFile) // state
        dispatch(uploadImage(imageFile))
    }
}
```
FileReader를 생성해주어 `readAsDataURL`을 사용해 받아온 로컬파일을 입력해준다. 그리고 `onloadend` 함수를 통해 `reader.result` 라는 결과값을 보내주고 dispatch 로 결과값을 보내준다

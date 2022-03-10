# 함수형 컴포넌트에서 사용하는 함수선언
```
function App(){
  let [text, setText] = useState('');
  const = onChange = (e) =>{
    setText(e.target.value)
  }
  return(
    <>
      <input onChange={onChange}/>
      <h1>{test}</h1>
    </>
  )
}
```
#### 클래스형에서 함수를 생성하는 방법과 달리, 변수를 선언하듯이 함수를 선언하는 방법을 사용하면 됩니다. setText가 text의 값을 바꿔주어서 출력됩니다.

# Vue Todo

Vue로 제작한 Todo List입니다. <br>
business / personal 두 가지로 구분하여 리스트를 작성할 수 있도록 코딩했습니다. <br />
또한 LocalStorage를 이용하여 내용이 저장되록 했습니다.

<br>

## 💡 목차
- [개발 환경](#개발-환경) <br>
- [코드 내용](#코드-내용)

<br>

## ⚙️ 개발 환경

React, react-router-dom, tailwind, scss

<br>

## ✒️ 코드 내용
- [타이핑 효과 구현](#타이핑-효과-구현) 

<br>

### 타이핑 효과 구현

실제 도트 게임처럼 말풍선 안에 타이핑 효과를 낼 수 있도록 하고 싶어서 useState와 useEffect, setInterval을 사용했습니다.<br>
먼저 useState를 사용하여 출력할 텍스트를 저장할 변수와 글자 수를 카운트해주는 변수를 정의했습니다. 그리고 txt 변수에 타이핑 효과를 줄 텍스트를 저장합니다.<br>
<br>
useEffect 내부에서 setInterval을 사용하여 0.1초 간격으로 글씨가 출력되도록 작성했습니다.<br>

```js
// App.js

function App() {
  const txt = "Baek Seung Yeon’s portfolio!";
  const [text, setText] = useState("");
  const [count, setCount] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setText(text + txt[count]);
      setCount(count + 1);
    }, 100);
    if (count === txt.length) {
      clearInterval(interval);
    }
    return () => clearInterval(interval);
  });

  return (
    <div className="wrap">
      <Header />
      <Visual />
      <Balloon text={text} compUrl="/profile" />
    </div>
  );
}
```

<br>

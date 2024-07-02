
[link:](https://inpa.tistory.com/entry/CSS-%F0%9F%93%9A-%ED%8A%B8%EB%9E%9C%EC%A7%80%EC%85%98-%ED%8A%B8%EB%9E%9C%EC%8A%A4%ED%8F%BC-%EC%95%A0%EB%8B%88%EB%A9%94%EC%9D%B4%EC%85%98)
## 1. Transition
### 1.1 Transition
- 트랜지션은 CSS 프로퍼티(property)의 값이 변화할 때, 프로퍼티(property) 값의 변화가 일정 시간(duration)에 걸쳐 일어나도록 하는것<br>
- 표시의 변화를 부드럽게 하기 위해 애니메이션 속도를 조절
- transition이 가상클래스 선택자 이전/이후에 들어가는 차이가 존재하나요?<br>
  <strong>YES</strong>
  ```css
      /* 이 부분에 들어가면 원상태로 돌아올때도 속도가 조절된다.*/
    .move-up {
    transition: transform 1s ease;
    }

      /* 이 부분에 들어갈경우 원상태로 돌아올때는 속도 조절 X */ 
  .move-up:hover {
      transform: translateY(-10px);
    }
  ```
### 1.2 Transition property
|속성|설명|
|---|---|
|```transition```|transition 단축 속성 표현|
|```transition-property```|요소에 추가할 전환 효과 설정<br>초 단위(s) 또는 밀리 초 단위(ms)로 지정|
|```transition-duration```|전환 효과가 지속될 시간을 설정|
|```transition-timing-function```|진환 효과의 시간당 속도를 설정함|
|```transition-delay```|전환 효과가 나타나기 전까지의 지연 시간을 설정함|

- 예시
```css
div {
   width: 100px;
   height: 50px;
   background-color: red;
   margin-bottom: 10px;

   /* 어떤 css 프로퍼티를 transition할지 지정 */
   transition-property: width, background-color;
   /* 색의 변화는 자연스럽게 그라데이션으로 바뀐다. */
   
   /* width와 bg-color가 2초동안 변화 */
   transition-duration: 2s, 2s;
}

div:hover { /* 마우스를 올리면 transition발동해서 적용될 상태 */
   width: 300px;
   background-color: blue;
}
```
```css
/* transition-duration */
div {
  transition-property: width, opacity, left, top;
  transition-duration: 2s, 1s; /* width, left는 2초 opacity top은 1초에 걸쳐 변화 */
}

div {
  /* shorthand syntax */
  transition: width 2s, opacity 4s; /* 축약 표현 */
}
```
- ```transition-timing-function``` : 시간에 따른 변화 속도와 같은 일종의 변화의 리듬을 지정
```css
{
  /* 느리게 시작하여 점점 빨라졌다가 느려지면서 종료 */
  transition-timing-function: ease;

  /* 시작부터 종료까지 등속 운동 */
  transition-timing-function: linear;

  /* 느리게 시작한 후 일정한 속도에 다다르면 그 상태로 등속운동 */
  transition-timing-function: ease-in;

  /* 일정한 속도의 등속으로 시작에서 점점 느려지면서 종료한다. */
  transition-timing-function: ease-out;

  /* ease와 비슷하게 느리게 시작하여 느려지면서 종료한다. */
  transition-timing-function: ease-in-out;
}
```
- ```transition-delay``` : 트랜지션 발동 대기시간 / 초 단위 또는 밀리 초 단위로 지정
- ```transition``` : 단축 속성 표현
```css
{
  /* 
  transition: property duration function delay
  기본값      all      0        ease     0
  */
    /* duration */
  transition: 1s

  /* property duration */
  transition: width 1s

  /* duration function */
  transition: 1s ease-in;

  /* duration delay*/
  transition: 1s 1s;

  /* property duration function delay */
  transition: width 1s ease-in 1s;

}
```
- 주의사항 : 모든 CSS 프로퍼티가 트랜지션의 대상이 될 수는 없다.<br>
(1) Box model<br>
  width height, max-width, max-height, min-width, min-height<br>
  padding, margin<br>
  border-color, border-width, border-spacing<br>
(2) Background<br>
  background-color, background-position<br>
(3) 좌표<br>
  top, left, right, bottom<br>
(4) 텍스트<br>
  color font-size, font-weight, letter-spacing, line-height<br>
  text-indent, text-shadow, vertical-align, word-spacing<br>
(5) 기타<br>
  opacity, outline-color, outline-offset, outline-width<br>
  visibility, z-index<br>


## Transform
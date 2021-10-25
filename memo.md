App.vue에서 짠 코드를 index.html에 박아넣어 페이지를 만드는 개념이다.
index.html에 박아넣는 역할은 main.js가 한다.
node_modules : 프로젝트에 쓰일 라이브러리들 위치
public: html,기타파일 보관위치
package.json : 설치한 라이브러리 기록

서버실행: 터미널에 npm run serve

주로 App.vue에서 작업

//js: document.getElementById().innerHTML = ??

동적 데이터 출력 형식 : {{ 변수명 }} (vue) \${변수명}(JS)
html태그안에 동적데이터 넣기 :: :대상="변수이름"
array값 꺼내기 :: {{ array[idx] }}
데이터는 `<script>` 태그의 data(){} 블록안에 선언한다.
문법의 용도를 아는 것이 중요하다.

반복적인 html태그 줄이기(반복문)
`<a v-for="(a, i) in array (또는 data블록에서 정한 array)" :key="name3">{{ name3 }}</a>` -- array의 값 중 하나 a를 넣어 반복한다.

key의 용도: 반복문으로 생성한 태그들을 구분하기 위한 속성

-- 위와 같이 사용하면 html이 짧아진다는 장점이 있음

이벤트리스너 핸들러 (클릭이벤트)
v-on:click="javascript" or @click="javascript"
혹은
@eventName = "functionName"

event mouseover : mouse 갖다댔을때 이벤트

function은 default 블록의 methods:{} object에 담아준다.

## 5이미지첨부 : <img src ="주소">

modal

동적UI 제작법:

1. UI현재상태를 데이터로 저장해둠 (데이터블록 : react에서는 state라고 부름)
2. 데이터에 따라 UI가 어떻게 표현될지 작성

조건식 : v-if

## 6 import export

export:
export default varName;
여러변수 export : export { 변수들 }

import:

import {export한 변수들} from '경로'

## 컴포넌트

길고 복잡한 html을 축약하는 방법 : component

- 이름.vue 로 파일을 작성해준다
- app.vue에서 import하고 components:에 등록하여 사용한다.

- 사용목적 : html 가시성 증대/ 반복사용이 필요할 시 호출해서 바로 사용가능
- 주의 : component화 할때 바인딩 했던 데이터들도 같이 옮겨야 한다. (그냥 복붙하는 것은 중복이 생겨 문제가 발생할 수 있다.)

- 데이터는 한군데다 만들어 놓고 가져다 쓰는형식으로 작성한다. (Props)

## Props

- 부모컴퍼넌트와 자식컴퍼넌트
- 자식컴퍼넌트가 부모컴퍼넌트의 데이터를 가져다 쓸 때 Props문법으로 전송.

1. 데이터 전송 :작명 = "데이터이름" 혹은 직접 데이터 입력 >> {
   ex)
   :작명 = "[ ... array ]" OR
   :작명 = "{ ... attr }" ... etc
   문자열은
   작명 = "string"

} (: == v-bind)

2. 등록 (자식컴퍼넌트에 props:{ ... })

- Props는 읽기전용이다. (수정불가)

3. 사용

- props(자식컴퍼넌트)에 데이터 안만드는 이유: 부모도 사용하는 데이터라면 최상위컴퍼넌트에서 선언하는 것이 유지보수에 좋다.

## custom event

- 자식컴퍼넌트 > 부모 컴퍼넌트 데이터 전달 : @emit('작명', 데이터) //뷰내장변수
- 부모컴퍼넌트 수신: @작명 = "data조작... x = $event" //$event : @emit에서 전달한 데이터

## input

- @input : 입력즉시 이벤트발생
- @change: 항목변동발생시 이벤트발생
- \$event == JS의 HTML_element.addEventListener('click', function(e){
  e.event
  })
- v-model : \$event의 약어버전

- input에 입력한 것은 전부 문자자료형. 숫자로 받으려면 v-model.number =

## watcher :입력데이터 검증

- defaulst 블록에 watch 객체

- 복잡하고 귀찬은 validation은 form validation library를 이용하는 것이 좋다.

## animation

- <div class="start" :class="{ end: true }"> { 클래스명: 조건}
- <transition name="작명"> : 별다른 스타일이나 구문조작없이 애니메이션효과 부여가능
  -- css에 <<등장>> .작명-enter-from {}(시작) .작명-enter-active {}(중간?) .작명-enter-to {}(끝)
  <<퇴장>> .작명-leave-to

## sort()

//문자순 정렬: arr(또는 obj).sort();
//숫자정렬 arr.sort(function(a, b){
// return a - b; 음수면 b를 a와 위치전환.
//})

//sort는 원본을 변환시킴

//map, filter는 원본보존

## component lifeCycle

- 컴퍼넌트는 표시될 때 까지 일련의 과정을 거침 : 그 과정을 lifeCycle 이라고함

- lifeCyle hook : lifeCycle 도중에 hook을 걸어 원하는 코드 실행가능

1. script블록에 mounted(){
   /_
   beforeCreate()
   created()
   beforreMount()
   mounted()
   beforeUpdate()
   updated()
   beforUnmount()
   unmounted()
   등
   _/
   } 선언

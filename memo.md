App.vue에서 짠 코드를 index.html에 박아넣어 페이지를 만드는 개념이다.
index.html에 박아넣는 역할은 main.js가 한다.
node_modules : 프로젝트에 쓰일 라이브러리들 위치
public: html,기타파일 보관위치
package.json : 설치한 라이브러리 기록

서버실행: 터미널에 npm run serve

주로 App.vue에서 작업

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

--5
이미지첨부 : <img src ="주소">
modal

동적UI 제작법:

1. UI현재상태를 데이터로 저장해둠 (데이터블록 : react에서는 state라고 부름)
2. 데이터에 따라 UI가 어떻게 표현될지 작성

조건식 : v-if

--6
export:
export default varName;
여러변수 export : export { 변수들 }

import:

import {export한 변수들} from '경로'

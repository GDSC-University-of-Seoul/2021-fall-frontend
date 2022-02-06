# 우당탕탕 JS 프로젝트 + React

이번에 간단한(?) JS 프로젝트를 완성(?)시키고 새로운 기술, React의 세계를 탐험 중에 있습니다.

그리하여 JS 프로젝트 간에 겪은 문제나 React를 하면서 느낀 점을 간단하게 이야기하려 합니다.

## JS 프로젝트를 하면서

---

### 디자인

기술적인 이야기를 하기 이전에 다른 중요한 점을 하나 느꼈습니다.

디자인이 너무 구렸습니다. 기술적인 부분은 어떻게든 구글링해서 해결할 수 있었는데 이 디자인은 참 답이 없더라구요ㅎㅎ 그리하여 가능하다면 다음 학기에 웹디자인을 한 번 들어볼까 합니다.

이 이야기는 여기까지 진행하고 이번 프로젝트 간에 저를 가장 힘들게 했던 것은
바로 CORS 문제였습니다.

### CORS Error

아마 이 곳에 계신 모든 분들이 한 번쯤은 겪어 보시지 않았을까 싶습니다.

CORS(Cross-origin Resource Sharing)는 추가적인 HTTP 헤더를 이용해 한 출처에서 다른 출처에 있는 자원에 접근 가능하도록 하는 것인데,

그러나 대개의 경우는 CORS가 아닌 SOP를 따르고 있습니다. 이 전에도 외부의 API를 사용한 적이 있어서 사실 이미 겪었어야 했는데 운 좋게도 Access-Control-Allow-Origin: \*이 설정되어 있던 것인지 제가 모르는 특별한 무언가가 있었는지 이로 인해 이를 드디어 겪게 되었습니다.

위의 SOP란 무엇인가?

이는 Same Origin Policy를 칭합니다.
즉 같은 출처에 있는 것에 대해서만 자원을 공유한다라는 것입니다. 사실 이는 보안상에서 최소한의 효율적인 대처이긴 합니다. 만약에 이러한 것이 설정되어 있지 않다면 어디에서 날아올지 모르는 수많은 시도들에 휩싸여 많은 시간을 낭비하게 될 것입니다. 이 중에 나쁜 마음을 먹고 이루어지는 시도들 역시 수없이 많을 것입니다. 이러한 것을 방지하기 위한 기본적인 보안이 SOP라 할 수 있겠습니다.

하지만 이러한 조치는 그러한 나쁜 접근뿐 아니라 선하고 무지한 개발자들의 발목을 마구 잡아버리게 되었습니다.

왜냐하면 이로 인해 브라우저 단에서 JS를 통해 API를 fetch하는 것이 사실상(제 수준에서) 불가해졌기 때문입니다.

상식적으로 외부 API와 어떻게 출처가 동일하겠습니까?

이러한 것을 어떻게 해결할 수 있을까요???

- #### JSONP

사실 이건 꼼수입니다. 사실 요근래에 이게 먹히는 게 있는지 저도 좀 궁금합니다(만약 아신다면 알려주세요!)

이는 일반적으로 저희가 사용하는 AJAX 통신과는 결이 좀 다른 친구입니다.

이는 데이터 타입 요청이 아니라 script 호출 방식이고 HTML의 script요소로부터 요청되는 호출에는 보안상 정책이 적용되지 않는 점을 이용한 우회 방법입니다. 이렇게 호출해온 것에 callback 파라미터를 이용해서 처리를 하는 것입니다. 하지만 이는 서버에서 지원하지 않으면 애초에 불가하기에 꼼수라고 할 수 있겠습니다.

그리고 제가 이걸 사용해보려고 노력하다가 실패했습니다. ㅎㅎ

- #### 서버를 사용하기

이게 정석이라고 할 수 있겠습니다. 서버간 통신을 통한 정상적인 데이터 요청은 가능하기 때문입니다. 그리하여 포기를 하려던 차에 이전에 사용해봤던 nodeJS가 생각났고 이걸 사용하면 어떻게든 되지 않을까 생각하였습니다.

그리하여 nodeJS의 express를 이용해 간단한 서버를 구성해서 여기서 서버단 통신과 데이터 가공을 해주었습니다. 추가적으로 CORS를 사용하여 white list를 작성하여 브라우저에서 통신이 가능하도록 하였습니다.

이러한 방법을 처음부터 사용하였더라면 좋았을 텐데 괜히 꼼수 부리다가 늦어진 느낌이네여 그래도 덕분에 좋은 경험을 했던 것 같습니다.

## React를 만지면서

---

### 총평

아직 React를 공부중에 있지만 너무 좋은 것 같습니다.
이 이상의 찬사를 사용할 수 없을 것 같습니다.
역시 대단한 사람들이 만든 것에는 토를 달 것이 없습니다.
신세 좀 지겠습니다.

- ### JSX

이것은 HTML? 인데 중간중간 JS를 끼워넣을 수 있다는 것이 과연 말이 되는가?
처음 보고 정말 깜짝 놀랐던 것 같습니다.
간단하게 설명하자면 JS에 html을 합치고 이러한 것을 기반으로 userdefine component를 만들어내는 것이 아닐까 싶네요??
이를 기반으로 코드 재사용성을 높일 수 있을 것 같습니다.

역시 자세한 설명은 [공식 문서](https://ko.reactjs.org/docs/introducing-jsx.html)

- ### props, state

이 부분에 대해서 간단하게만 설명한다면
일단 props를 통해서 저희가 만들어낸 component에 생명을 불어 넣을 수 있습니다. 이를 통해서 component에 eventlistener를 붙이거나 props를 이용해 내부의 text등을 수정하는 것이 가능합니다.
state를 통해 효과적인 re-rendering이 가능하고요.

사실 React 쪽은 현재 공부하고 있는 지라 조금 부족하지만
다음에는 제 실제 경험담과 함께 돌아오도록 하겠습니다.
## 이벤트 루프란? 

<img src='https://i.imgur.com/rnQEY7o.png' width="700px"/>

---

- Heap, Web API (Browser), Callback Queue / Message Queue 로 구성 되어있다.

- Heap
  
  - 선언 후 변수가 저장되는 공간 (메모리)
  
- Call Stack
  - LIFO / FILO 구조. 
  - 함수가 실행 되면 Call stack에 frame으로 push 된다. 실행이 종료되는 즉시 Call stack에서 pop 된다.
  - 중첩함수를 실행 했을 경우, 내부함수가 실행되고 있는 순간에는 두개의 frame이 call stack에 쌓여있다.

- Web API
  - 웹 브라우저에 있는 Application Programming Interface. 브라우저와 컴퓨터 주변 환경의 데이터를 가지고 복잡하고 유용한 일들을 처리해줌. web api는 자바스크립트 언어의 속하지 않고, 코어 자바스크립트를 기반으로 하여 만들어진 것이다. 
  - 예를 들면 Geolocation API는 위치 데이터를 가져올 수 있도록 간단한 자바스크립트 구조를 제공해준다. 그리고 이것은 구글맵에 내 현재 위치를 보여줄 때 사용된다. 브라우저는 사실 뒤에서 C++ 와도 같은 lower-level code를 써서 장치의 GPS 하드웨어와 소통하여 위치 데이터를 가져오고 브라우저 환경에서 쓸 수 있도록 반환해준다. 이런 식으로 복잡한 작업을 API가 간단하게 만들어 주는 것이다.

- Message Queue / Callback Queue
  - LILO / FIFO 구조.
  - setTimeout 혹은 promise와 같은 비동기로 함수를 실행 했을 경우 실행 준비가 완료 된 함수들이 차례대로 대기하고 있는 공간.
  - Call Stack이 비어있을 경우에만 message queue에 대기하고 있는 함수가 하나씩 순서대로 shift되면서 call stack으로 이동하고 실행된다.

  

  코드

  ```js
  function main () {
    console.log('A')
    setTimeOut(function () { console.log('B')}, 0)
  	console.log('C')
  }
  
  // A
  // C
  // B
  ```

  ```js
  function main () {
    console.log('A')
    setTimeOut(function () { console.log('B')}, 0)
    console.log('C')
    runWhileLoopForNSeconds(3)
  }
  
  function runWhileLoopForNSeconds(sec) {
    const start = Date.now();
    let now = start;
  
  	while ( now - start < sec * 1000 ) {
      now = Date.now()
    }
  }
  
  // A
  // C
  // B
  ```

  ```js
  // code excerpt from https://stackoverflow.com/questions/25915634/difference-between-microtask-and-macrotask-within-an-event-loop-context/25933985#25933985
  
  console.log('stack [1]');
  setTimeout(() => console.log("macro [2]"), 0);
  setTimeout(() => console.log("macro [3]"), 1);
  
  const p = Promise.resolve();
  for(let i = 0; i < 3; i++) p.then(() => {
      setTimeout(() => {
          console.log('stack [4]')
          setTimeout(() => console.log("macro [5]"), 0);
          p.then(() => console.log('micro [6]'));
      }, 0);
      console.log("stack [7]");
  });
  
  console.log("macro [8]");
  
  /* Result:
  stack [1]
  macro [8]
  
  stack [7], stack [7], stack [7]
  
  macro [2]
  macro [3]
  
  stack [4]
  micro [6]
  stack [4]
  micro [6]
  stack [4]
  micro [6]
  
  macro [5], macro [5], macro [5]
  ```

  

  ----

- 위의 설명은 필립 로버트의 자바스크립트 이벤트 루프에 관한 강의를 기반으로 작성한 것입니다. 필립 로버트가 만든 http://latentflip.com/loupe에서 이벤트 루프의 작동 방식을 한눈에 실시간으로 확인할 수 있습니다.  

   

  ### 이벤트 루프 기본 동작 방식 (simplified)

- 함수가 실행되면 우선 자바스크립트 엔진의 콜스택에 대기한다.

- 함수 안에 내부 함수가 없는한 web API로 넘어간다

- web API에서 callback queue 에 대기

- callback queue 에서 대기하면서 call stack을 지켜보다가 call stack이 비어있는 순간 이벤트 루프가 차례대로 callback queue에 대기하고 있는 순서대로 함수를 call stack으로 옮겨서 실행.  

  

  ### 이벤트 루프 (on micro & macro tasks)
- message queue는 사실 두가지 queue 로 나뉜다. 하나는 microtask queue 이고, 그리고 다른 하나는 macrotask queue 이다.

- 이름에서 알 수 있듯이, microtask queue 에느 microtask만 대기하고, macrotask queue에는 macrotask마 대기하는 것이다.

- setTimeout은 macrotask 에 속하고 Promise는 microtask 속한다.

- Microtask queue는 call stack을 계속해서 확인하면서 완전히 비워졌을 때 call stack으로 이동하여 차례대로 모두 비워질 때 까지 실행된다..

- microtask queue가 비면 그제서야 macrotask queue 실행 가능하다.

- requestAnimationFrame는 task는 브라우저마다 다름. 

  - chrome은 micro task -> requestAnimationFrame -> macro task
  - firefox는 micro task -> macro task => requestAnimationFrame

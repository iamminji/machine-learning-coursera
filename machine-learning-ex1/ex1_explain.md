## ex1 문제 설명 및 풀이

#### 환경설정
우선 Octave 혹은 Matlab을 설치한 후에 주어진 ex1 파일을 다운 받고 압축 파일을 푼다.
주어진 주요 파일을 살펴보면 다음과 같다.

- ex1.m
    - 테스트 코드를 실행할 수 있는 스크립트이다. 문제를 푼 후에 ex1을 실행 시키면 올바르게 문제를 풀었는지를 알 수 있다.
- ex1_multi.m
    - Optional 문제를 위한 테스트 스크립트이다.
- submit.m
    - 제출을 위한 스크립트이다.

나머지 파일은 문제를 풀기 위한 파일들이다.


#### warmUpExercise
문제를 어떻게 풀어야 하는지 알려주는 워밍업이다. 
`A=eye(5);` 를 warmUpExercise.m 파일에 적은 후에 submit() 을 하면 제대로 제출는지 확인 할 수 있다. 한 가지 헷갈려 할 수 있는 것은, 동영상에선 문제를 선택할 수 있게끔 나오지만 그것은 예전 버전이므로 현재 submit()을 하면 바로 제출이 되게끔 변경 되었다.
또한 이메일, token 입력하는 홈페이지도 달라졌는데 현재 동영상 주소에 나와있는 곳으로 가면 아무것도 없을 것이다. 이메일은 coursera의 자기 이메일을 사용하면 되고 token은 assignment 페이지를 누르면 자신의 token이 보일 것이다.

만약 `Submission failed: You used an invalid email or your token may have expired. Please make sure you have entered all fields correctly. Try generating a new token if the issue still persists.` 같은 에러가 뜬다면 
1. 이메일이 자신의 coursera 이메일인지 확인해 보기
2. token 을 재발급 받기
3. 컴퓨터의 timestamp가 올바른지 확인해 보기
위의 세 가지를 시도해 보길 바란다.

여기까지 오면 워밍업은 끝났다. 이 다음 부터는 진짜 문제 풀기이다.

#### computeCost
J(θ) 를 구현하는 문제이다. 사실 Octave 튜토리얼 동영상을 잘 보다 보면 답이 나와 있다.
그래서 딱히 설명할 게 없다. 강의에 있는 J(θ)를 그대로 구현하면 된다.
(h가 theta * X라는 것만 알면 될듯)

#### gradientDescent
이 문제에서 시간을 꽤 할애했는데 옥타브 문법을 몰라서 자꾸 에러가 났다. 이 문제 역시 주어진 경사하강법을 옥타브로 구현하면 되는것이다.
```
    delta = 1/m * X'*(X*theta-y)
    theta = theta - (alpha * delta);
```
delta라는 벡터를 만드는데 이 때 값이(1/m 말고) 바로 경사 하강법 sum 안에 있는 내용이다. sum을 vectorized 한 것으로서 X*theta는 추론 h 이고 여기에 y라는 (matrix와 스칼라와의 사칙연산은 가능하므로) 실수를 빼준다. 이 때 X의 transpose를 곱해주므로써 matrix가 아니라 vector 값을 만든다. 이것이 delta이다.

그 다음엔 그냥 공식 대로 풀면 된다.
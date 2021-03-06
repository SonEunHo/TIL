# 데이터 서버 이전

만약 레디스 혹은 DB서버를 새로운 서버군으로 교체해야한다면 어떻게 작업할 수 있을까?

다른 방법이 있는지 모르겠지만 주로 이 순서로 작업을 한다.

1. 새로운 서버군에 필요한 환경 구축 (레디스 설치 or DB설치)

2. 기존 서버군 -> 신규 서버군으로 데이터 복제 (이때부터 작업이 완료될 때 까지 계속 복제한다)

3. 기존 서버군에 read only만 가능토록 한다. (신규 서버군은 write 해도 된다)

4. 신규 서버군을 사용하도록 연관 서버를 배포한다.

5. 이상이 없으면 완료. 기존 서버군을 철거한다.

이렇게 작업을 하면 write액션시 애플리케이션에서는 에러가 발생하기에 완벽한 방법이 아닐 수 있다.
하지만 나는 아직 이것보다 깔끔하고 확실한 방법을 알지 못한다.

마치 "살을  주고 뼈를 취한다"
잠깐의 에러는 감수한다.

물론 트래픽이 과도하다면 지표를 확인해서 새벽작업이 필요한지 확인해야한다.

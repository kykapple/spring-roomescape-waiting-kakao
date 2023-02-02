# spring-roomesacpe-waiting

## 요구사항
- auth 패키지를 nextstep 패키지로부터 분리한다.
  - [x] auth 패키지에서 nextstep로 의존하는 부분을 제거한다.
    - [x] MemberDao 제거
    - [x] Member 제거
  - [x] auth 패키지 내에서 스프링 빈으로 사용되던 객체를 Component Scan이 아닌 Java Configuration으로 빈 등록한다.
- [x] 예약 대기 테이블 생성
  - [x] id, memberId, scheduleId, waitNum을 컬럼을 갖는다.
- [x] 예약 대기 신청
  - [x] 예약이 된 스케줄 대상으로 예약 대기를 신청할 수 있다.
  - [x] 예약이 없는 스케줄일 경우 예약 대기 신청을 할 경우 예약이 된다.
- [x] 예약 대기 취소
  - [x] 자신의 예약 대기를 취소할 수 있다.
  - [x] 자신의 예약 대기가 아닌 경우 취소할 수 없다.
- [x] 나의 예약 조회
    - [x] 나의 예약 목록을 조회할 수 있다.
    - [x] 예약과 예약 대기를 나눠서 조회한다.
    - [x] 예약은 reservation을 조회하고 예약 대기는 reservation-waiting을 조회한다.
    - [x] 예약 대기의 경우 대기 순번도 함께 조회할 수 있다.

## 추가 요구사항
- 예약금이 입금 되어야만 예약 승인이 되도록 정책을 변경한다.
- 매출 이력을 관리한다.
- 예약 상태에는 예약 미승인, 예약 취소, 예약 취소 대기, 예약 거절 5가지가 있다.
- [x] 관리자의 예약 미승인/승인
  - [x] 사용자가 예약을 신청 후 관리자는 예약금 입금 확인을 하고 예약 승인을 한다.
  - [x] 예약 승인 시 예약의 상태는 예약 승인으로 변경된다.
  - [x] 예약금이 매출로 기록된다.
- [ ] 사용자의 예약 취소
  - [ ] 예약 미승인 상태에서 취소하는 경우 바로 예약 취소 상태가 된다. 
  - [ ] 예약 미승인 상태에서 취소하는 경우 예약금을 입금하지 않았다고 가정하여 매출 기록의 변경은 없다.
  - [ ] 예약이 승인 상태인 경우 관리자의 승인이 필요하여 예약 취소 대기가 된다.
- [ ] 관리자의 예약 취소 승인
  - [ ] 사용자가 예약을 취소한 후 관리자가 예약 취소를 승인하는 경우, 예약이 취소 대기 상태에서 취소 상태로 변경된다.
  - [ ] 매출에 예약금 환불 이력이 추가된다.
- [ ] 관리자의 예약 거절
  - [ ] 예약이 미승인 상태인 경우 예약이 취소되어 예약 거절이 된다.
  - [ ] 예약이 승인 상태인 경우 예약이 취소되어 예약 거절이 된다. 이때 예약금 환불이 발생하여 매출 기록에 변경이 있다. 

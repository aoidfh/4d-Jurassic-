# 🎮 4D Battle: Jurassic Adventure

> Unity 기반 4D 레일 슈팅 게임 (Rail Shooter)

---

## 🧩 프로젝트 개요 (Project Overview)

**4D 배틀 (Jurassic Adventure)** 는 Unity(C#) 기반으로 개발된 **레일 슈팅 (Rail Shooter)** 게임입니다.
플레이어는 정해진 경로를 따라 이동하며, 등장하는 적들을 조준하고 격파하는 형태로 진행됩니다.

주요 목표는 **‘생존 + 퇴각’**이며, 공룡을 제압하거나 회피하여 탈출 지점에 도달해야 합니다.
게임의 중심은 **공룡 개체의 자율적 행동**입니다.
각 공룡은 플레이어의 개입이 없어도 환경 안에서 독립적으로 행동하며, 실제로 ‘그곳에 서식하고 있는 생물’처럼 느껴지도록 설계되었습니다.

본 프로젝트는 **2개월간의 팀 프로젝트**로 진행되었으며,
저는 **적 AI 행동 및 공격 로직**을 담당했습니다.
팀원들과 협업하여 **레일 이동 구조, UI, 사운드 시스템을 통합 개발**했습니다.

**제작 기간:** 22.05 ~ 22.06 (2개월, 팀 프로젝트)
**개발 환경:** Unity (C#), Visual Studio
**플랫폼:** PC
**장르:** 4D 레일 슈팅 게임
**역할:** 적 AI 행동, 공격 로직 구현

---

## 🎯 주요 기능 (Key Features)

### 🧩 적 행동 로직 (AI Behavior System)

* **자율 행동 AI**

  * 공룡은 플레이어와 무관하게 지정된 영역 내에서 독립적으로 활동하며, 실제 서식하는 생명체처럼 행동
* **거리 기반 감지**

  * 공룡은 거리 값만으로 플레이어를 감지
  * 감지 범위 이내 접근 시 공격 상태로 전환하고, 일정 거리 이상 멀어지면 이동 또는 대기 상태로 복귀
* **FSM 기반 공룡 행동 제어**

  * 각 공룡은 Idle → Move → Attack 상태로 순환 동작
  * Update()에서 거리 조건을 실시간 검사해 부드러운 상태 전환 유지
  * 다수 개체 동시 동작에도 경량 로직으로 프레임 안정성 확보
* **NavMesh 기반 이동 / 추적**

  * 이동 및 추적은 NavMeshAgent로 수행
  * Move 상태: 서식 구역 내 NavMesh 경로 이동 (지정 경로)
  * Attack 전개: 플레이어 방향으로 NavMesh 경로 재설정
  * 감지 범위 이탈 시 경로 취소 / 감속 후 상태 복귀
  * NavMesh Bake 시 영역 구분 (통행 불가 지형 제외)으로 길찾기 안정화
* **거리 기반 감지 로직**

  * Vector3.Distance로 감지 수행
  * 감지 범위 이내 → Attack, 범위 이탈 → Move/Idle 복귀
  * 단순 구조로 저사양에서도 반응 일관성 유지

---

## ⚙️ 기술 구현 (Implementation Details)

* **FSM(Finite State Machine)** 기반 공룡 행동 제어
* **NavMeshAgent** 기반 경로 탐색 및 이동 구현
* **거리 기반 감지 로직**으로 단순하면서도 안정적인 전투 흐름 유지
* **저사양 환경에서도 동시 AI 동작 안정성 확보**

---

## 🧩 Tech Stack & Contact

**Language:** C#
**Engine:** Unity 2020
**Tools:** Visual Studio, PowerDirector

**Contact**

* 박준영 | Game Programmer
* Email: [soiw5386@naver.com](mailto:soiw5386@naver.com)
* Demo Video: [https://youtu.be/Adlh1-6eikc](https://youtu.be/Adlh1-6eikc)

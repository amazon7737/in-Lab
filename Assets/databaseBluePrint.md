# 데이터베이스 설계서

# 👥 사용자

## userTable

: 사용자 정보를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| uid | varchar(30) | 사용자 식별 문자열 |
| upw | varchar(30) | 사용자 비밀번호(암호화된) |
| name | varchar(20) | 사용자 이름 |
| phone | varchar(11) | 사용자 전화번호 |
| email | varchar(200) | 사용자 이메일 |

## userGroupTable

: 사용자 ↔ 그룹간 관계를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| group | varchar(20) | 그룹 식별 문자열 |
| user | varchar(30) | 사용자 식별 문자열 |

## userGroupListTable

: 사용자 그룹을 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| gid | int(Auto Increase) | 그룹 식별 문자열 |
| name | varchar(30) | 그룹 이름 |

# 👤 관리자

## adminTable

: 관리자 정보를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| aid | varchar(30) | 관리자 식별 문자열 |
| apw1 | varchar(30) | 관리자 1차 비밀번호(암호화된) |
| apw2 | varchar(20) | 관리자 2차 비밀번호(암호화된) |
| name | varchar(20) | 관리자 이름 |
| isSuper | tinyint | 0 : 일반 관리자, 1 : 슈퍼 관리자 |

# 💬 커뮤니티

## noticeTable

: 공지사항 정보를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| nid | int(Auto Increase) | 공지사항 식별 번호 |
| type | varchar(20) | 공지사항 타입 |
| title | varchar(200) | 공지사항 제목 |
| datetime | datetime | 공지사항 생성 날짜 & 시간 |
| content | blob | 공지사항 내용 |
| files | varchar(200) | 공지사항 첨부파일(S3 링크) |

## noticeTypeTable

: 공지사항 말머리를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| ntid | int(Auto Increase) | 공지사항 말머리 식별 번호 |
| name | varchar(30) | 공지사항 말머리 이름 |

# 🚪 출결관리

## attendanceTable

: 입/퇴실 정보를 관리하는 테이블(로그형 데이터)

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| atid | int(Auto Increase) | 입/퇴실 식별 번호 |
| type | tinyint | 0 : in / 1 : out |
| datetime | datetime | 입/퇴실 날짜 & 시간 |
| user | varchar(30) | 사용자 식별 문자열 |

## alertTable

: 사용자 경고 정보를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| alid | int(Auto Increase) | 경고 식별 번호 |
| type | int | 0 : 회수됨 / 1 : 부여됨 |
| datetime | datetime | 부여 또는 회수 날짜 & 시간 |
| user | varchar(30) | 사용자 식별 문자열 |

# 📻 프로젝트

## projectTable

: 프로젝트 정보를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| pid | int(Auto Increase) | 프로젝트 식별번호 |
| type | tinyint | 0 : 공개 / 1 : 비공개 |
| name | varchar(200) | 프로젝트 이름 |
| desc | varchar(2000) | 프로젝트 설명 |

## projectUserTable

: 프로젝트 ↔ 유저 관계를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| project | int | 프로젝트 식별번호 |
| user | varchar(20) | 사용자 식별 문자열 |
| isOwn | tinyInt | 0 : 참여자 / 1 : 소유자 |

## projectBlogTable

: 프로젝트 내 포스트를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| bid | int(Auto Increase) | 포스트 식별 번호 |
| title | varchar(200) | 포스트 제목 |
| datetime | datetime | 포스트 생성 날짜 & 시간 |
| content | blob | 포스트 내용 |
| files | varchar(200) | 포스트 첨부파일(S3 링크) |
| project | int | 프로젝트 식별번호 |

## projectScheduleTable

: 프로젝트 일정을 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| wid | int(Auto Increase) | 일정 식별 번호 |
| name | varchar(200) | 일정 이름 |
| start | datetime | 일정 시작 날짜 & 시간 |
| end | datetime | 일정 시작 날짜 & 시간 |
| project | int | 프로젝트 식별번호 |

# 📋 TO-DO

## todoTable

: To-Do리스트 정보를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| tid | int(Auto Increase) | 할일 식별번호 |
| name | varchar(200) | 할일 이름 |
| desc | varchar(2000) | 할일 설명 |
| start | datetime | 할일 시작 날짜 & 시간 |
| end | datetime | 할일 종료 날짜 & 시간 |
| user | varchar(200) | 사용자 식별 문자열 |

## todoLogTable

: To-Do 완료 정보를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| datetime | datetime | 할일 완료 날짜 & 시간 |
| todo | int | 할일 식별번호 |
| user | varchar(200) | 사용자 식별 문자열 |

# 🖥️ 기자재

## equipmentTable

: 기자재 정보를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| eid | varchar(20) | 기자재 식별 문자열 |
| type | varchar(20) | 유형 |
| name | varchar(50) | 기자재 모델명 |
| sn | varchar(50) | 기자재 시리얼 넘버 |
| amount | int | 수량 |
| etc | varchar(200) | 비고 |

## equipmentUserTable

: 기자재 ↔ 사용자 관계를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| equipment | varchar(20) | 기자재 식별 문자열 |
| user | varchar(20) | 사용자 식별 문자열 |
| amount | int | 수량 |

## equipmentTypeTable

: 기자재 정보를 관리하는 테이블

| 컬럼명 | 타입 | 설명 |
| --- | --- | --- |
| etid | int(Auto Increase) | 기자재 유형 식별 번호 |
| name | varchar(20) | 기자재 유형 이름 |
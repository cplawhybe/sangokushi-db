# Dataview 쿼리 모음

자주 쓰는 쿼리 모음. 각 코드블록을 노트에 붙여넣으면 동적 목록이 생성됨.

---

## 인물 전체 목록

```dataview
TABLE 자, 소속, 생년, 몰년
FROM "인물"
SORT 소속 ASC, 생년 ASC
```

---

## 세력별 인물

```dataview
TABLE 자, 직위
FROM "인물"
WHERE 소속 = "위"
SORT 이름 ASC
```

> `소속 = "위"` 부분을 "촉한", "오", "군웅" 등으로 바꿔 사용.

---

## 기록 희박 인물 목록

```dataview
TABLE 소속, 생년, 몰년
FROM "인물"
WHERE contains(태그, "기록희박")
```

---

## 사건 타임라인

```dataview
TABLE 연도_시작, 연도_종료, 관련세력, 결과
FROM "사건"
SORT 연도_시작 ASC
```

---

## 미완성 노트 목록 (채워야 할 항목)

```dataview
TABLE 소속
FROM "인물"
WHERE 생년 = "" OR 생년 = null
SORT 이름 ASC
```

---

## 특정 인물 연결 사건

> 특정 인물 노트에서 사용. 해당 인물이 언급된 모든 사건 조회.

```dataview
LIST
FROM "사건"
WHERE contains(file.outlinks, [[조조]])
```

> `[[조조]]` 부분을 원하는 인물로 교체.

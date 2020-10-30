## 프로그래머스 level 1



#### 모든 레코드 조회하기

```sql
select * from ANIMAL_INS;
```



#### 역순 정렬하기

```sql
select NAME , DATETIME from ANIMAL_INS order By ANIMAL_ID desc;
```

- order by를 통해 정렬
- asc는 오름차순(default) , desc는 내림차순



#### 아픈 동물 찾기

```sql
select ANIMAL_ID , NAME from ANIMAL_INS 
where INTAKE_CONDITION = 'Sick';
```



#### 어린 동물 찾기

```sql
select ANIMAL_ID , NAME from ANIMAL_INS 
where not INTAKE_CONDITION = 'Aged';
```



#### 동물의 아이디와 이름

```sql
select ANIMAL_ID , NAME from ANIMAL_INS;
```



#### 여러 기준으로 정렬하기

```sql
select ANIMAL_ID , NAME , DATETIME from ANIMAL_INS
order by NAME asc, DATETIME desc;
```

- order by에서 여러 기준으로 정렬이 가능함

#### 

#### 상위 n개 레코드

```sql
select NAME from ANIMAL_INS
order by DATETIME limit 1;
```

- limit : n개의 레코드만 출력



#### 최댓값 구하기

```sql
select DATETIME from ANIMAL_INS
order by DATETIME desc limit 1;
```

- 역순 정렬하여 하나만 출력

```sql
select max(DATETIME) from ANIMAL_INS;
```

- max를 이용하여 최대값 출력



#### 이름이 없는 동물의 아이디

```sql
select ANIMAL_ID from ANIMAL_INS 
where NAME is null;
```



#### 이름이 있는 동물의 아이디

```sql
select ANIMAL_ID from ANIMAL_INS 
where NAME is not null;
```


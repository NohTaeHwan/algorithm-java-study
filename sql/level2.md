## 프로그래머스 level 2



#### 최솟값 구하기

```sql
select min(DATETIME) from ANIMAL_INS;
```



#### 동물 수 구하기

```sql
select count(*) from ANIMAL_INS;
```



#### 중복 제거하기

```sql
select count(distinct NAME) from ANIMAL_INS;
```

- count(*) 은 NULL값을 포함하여 출력 , count(칼럼) 은 NULL값을 제외하고 출력
- distinct는 중복 제거 키워드 
- 'distinct 칼럼 ' 하게 되면 중복 값 뿐만 아니라 null도 제외



#### 고양이와 개는 몇마리 있을까

```sql
SELECT ANIMAL_TYPE , count(ANIMAL_TYPE) as count from ANIMAL_INS
group by ANIMAL_TYPE
order by ANIMAL_TYPE;
```

- as : 칼럼 이름을 커스텀으로 정의
- group by : 해당 칼럼을 그룹화하여 표시



#### 동명 동물 수 찾기

```sql
select NAME , count(NAME) as count from ANIMAL_INS
group by NAME
having count > 1 and NAME is not NULL
order by NAME;
```

- having : 그룹화 후의 조건문 



#### 입양 시각 구하기(1)

```sql
select hour(DATETIME) , count(*) as count from ANIMAL_OUTS
where hour(DATETIME) >= 9 and hour(DATETIME) < 20
group by hour(DATETIME)
order by hour(DATETIME);
```

- hour : 시간 알려주는 함수



#### NULL 처리하기

```sql
select ANIMAL_TYPE , ifnull(NAME,'No name') , SEX_UPON_INTAKE from ANIMAL_INS
order by ANIMAL_ID;
```

- IFNULL : 값이 null일 때 다른 값으로 출력하도록 함

#### 

#### 루시와 엘라 찾기

```sql
select ANIMAL_ID , NAME ,SEX_UPON_INTAKE from ANIMAL_INS
where NAME IN ('Lucy','Ella','Pickle','Rogan','Sabrina','Mitty')
order by ANIMAL_ID;
```

- in : where 절 내에서 특정값 여러개를 선택하는 연산자 , 괄호 안의 값중 하나라도 해당되면 true



#### 이름에 el이 들어가는 동물 찾기

```sql
select ANIMAL_ID , NAME from ANIMAL_INS
where NAME like '%el%' AND ANIMAL_TYPE = 'Dog'
order by NAME;
```

- like : 부분적으로 일치하는 칼럼을 찾을 때 주로 where에서 사용
- '%' 는 글자 수 명시 x , '_' 는 글자 수 명시
- [^A] : 첫글자 A가 아닌
- [A-Z] : 첫 번째 문자가 A부터 Z중에 있는지
# 파일 읽기 & 쓰기

## 파일 열기
- 파일의 데이터를 읽거나 쓰기 위해 파이썬 내장함수 open()사용
  ```
  f = open([파일명], [파일모드])
  ```
- open() 함수는 파일을 파일 모드에 맞게 파일을 열어 파일 객체인 f를 반환
- 파일 모드
  - r: default, 읽기 모드
  - w: 쓰기, 같은 파일명이 있을 경우, 기존 내용 삭제
  - x: 쓰기, 같은 파일명이 있을 경우 에러
  - a: 추가, 찾는 파일명이 없으면 쓰기 기능 
  - b: 바이너리 파일 열기
  - t: default, 텍스트 파일 열기
  - 즉, 파일모드 default값은 'rt'임

## 파일 쓰기
```
f = open([파일명], 'w')
f.write([내용])
f.close()
```
- write()에서는 print()함수와 같은 출력방식 사용가능
  - 문자열을 그대로 파일로 출력 가능
  - 형식 지정 출력 방식으로 문자열을 파일로 출력
- 파일을 쓴 후 close()사용해 파일을 닫아야 파일 객체 f가 사라짐
- 쓴 파일 내용 확인
  ```
  !type [파일명.확장자]
  ```
  
## 파일 읽기
- 기본 방식: read()로 읽기
```
  f = open([파일명], 'r')
  data = f.read()
  f.close()
```
  
## 반복문 사용하여 파일 데이터 처리
  ### 문자열 한 줄씩 처리
    - 쓰기
      
        ```
          f = open([파일명], 'w')
          for n in range(1, [전체 줄수]):
            ...처리내용
            f.write(처리내용)
          f.close()
        ```
        
     - 이때, write()함수는 자동으로 줄바꿈하지 않기 때문에 개행문자 등을 추가하여 처리
    - 읽기
     - 파일 한 줄씩 읽기 위해 전체 내용을 반환하는 f.read() 대신 readline()이나 readlines() 사용
      - readline(): 실행횟수만큼 문자열을 한 줄씩 읽음
        - 마지막 한 줄을 읽고 readline() 수행 시 빈 문자열 반환
        - 이미 readline()은 개행문자가 포함되어 읽은 것을 출력할 때는 end=""로 줄바꿈 중복을 피함
          ```
            f = open([파일명])
            line = f.readline()
            while line:
              print(line, end="")
              line = f.readline()
            f.close()
           ```
      
      - readlines(): 파일 전체의 모든 줄을 읽어 한 줄 한줄 리스트 요소로 반환
        ```
        f = open([파일명])
        f.close()
        for line in f.readlines(): # = for line in f
          print(line, end="")
        ```
 ## with 문
  - with문을 이용하면 파일 처리 수행 후 자동으로 파일을 닫아주기 때문에 close()를 수행하지 않아도 됨 
    ```
      with open([파일명], [파일모드]) as f:
        ...
    ```
 

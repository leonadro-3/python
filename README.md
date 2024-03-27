# python
파이썬으로 데이터 분석하기

### 01 파일 경로 확인하기
```
import os
print("현재 파일 이름 :", __file__)
print("현재 파일 실제 경로 :",os.path.realpath(__file__))
print("현재 파일 절대 경로 :", os.path.abspath(__file__))
print("현재 폴더 경로; 작업 폴더 기준 :", os.getcwd())
print("현재 파일의 폴더 경로; 작업 파일 기준 :", os.path.dirname(os.path.realpath(__file__)))
```
![스크린샷 2024-03-27 082120](https://github.com/leonadro-3/python/assets/69701682/77d9b60d-a902-4967-b1b7-102b24ba82b3)

### 02 판다스로 .xlsx 파일 읽기
```
import  pandas as pd
filename = "./excel/seoul/[제22대_국회의원선거]_후보자_명부[국회의원선거][서울특별시][강남구갑].xlsx"
df = pd.read_excel(filename, engine='openpyxl')
print(df)
```
![스크린샷 2024-03-27 082544](https://github.com/leonadro-3/python/assets/69701682/d6f5dc82-36d3-42b6-aea1-9e7d2504186e)

> 엑셀 파일을 바로 열어보면 Dataframe으로 변환하게 되는데 nan, unnamed 등의 값들이 나온다. 이는 해당 부분이 콘솔창으로 표시될 수 없는 형식이기 때문이다.
> [6 rows x 19 columns]를 통해서 6개의 행과 19개의 열로 작성되었다는 것을 알 수 있다.
> 해당 엑셀 파일을 제대로 사용하기 위해서는 데이터를 전처리할 필요가 있다.

### 03 OS로 폴더 내 모든 파일 이름 나열하기 (리스트로 반환 : 한줄에 모두 표시)
```
import os
# 주어진 디렉토리에 있는 항목들의 이름을 담고 있는 리스트를 반환합니다.
# 리스트는 임의의 순서대로 나열됩니다.
file_path = './excel/seoul'
file_names = os.listdir(file_path)
print(file_names) #폴더 내 파일 목록
print(len(file_names)) #폴더 내 파일 총갯수
print(type(file_names)) #폴더 내 파일 목록의 데이터 타입
print(file_names[0]) # 첫번째 파일명을 가져옴
```
![스크린샷 2024-03-27 083022](https://github.com/leonadro-3/python/assets/69701682/e78f5219-05ac-4bcc-9aac-cb11f02031ea)
> print(file_names)을 사용하면 한줄에 리스트 자료형으로 출력한다. 정렬 기준 (ex 수정한 날짜, 파일용량 등등)을 지정하여 나열할 수 도 있다.
> len(file_names) 폴더안에 몇개의 파일이 있는지 알 수 있게 된다.
> *중요* os - 폴더 - 폴더 내 파일에 접근한 것이지 파일 내 데이터에 접근한 것은 아니다.

> 48번 반복하여 각각 출력하는 방법
> print(file_names[0])
> print(file_names[1]) ... 반복해서 각각의 숫자를 바꾸어야 함. 반복문을 사용하면 됨.
> i = 1 , print(file_names[i])
> i 들어간 1을 가지고 print()를 48번 반복하게 하면 됨. 조건문은 rage()로 범위를 정함.


### 04 OS로 폴더 내 모든 파일 이름 출력하기 (콘솔에 출력 : 한줄에 하나씩 반복 표시)
***
```
import os
# 주어진 디렉토리에 있는 항목들의 이름을 담고 있는 리스트를 반환합니다.
# 리스트는 임의의 순서대로 나열됩니다.
file_path = './excel/seoul'
file_names = os.listdir(file_path)
for i in range(48):
    print(file_names[i])
```
> 폴더 내 총 파일 갯수를 확인한 다음 조건문 작성
***
***
```
for i in range(len(file_names)):
    print(file_names[i])
```
> 폴더 내 총 파일 갯수를 함수로 가져와서 조건문을 작성
***
> 둘다 결과 값은 같지만 상황에 따라서 조금씩 달라진다. 여기서 반복문의 횟수(48)를 명시했는데 len(file_names)으로 처리하면 더 좋다. 
> 01. 파일의 총 갯수는 계속해서 달라지기 때문이기도 하고 반복문을 돌릴 때마다 갯수를 세서 작성하지 않아도 된다.
> 02. 폴더 내 파일의 갯수가 너무 많은 경우 세는 데 시간이 너무 오래 걸린다.
> 03. 혹시나 반복문의 조건에 int 숫자로 명시할 경우 시간에 따라 갯수가 변화하는 데이터라면 처리할 수 없게 된다.
> tip 콘솔에 뜬 것을 그대로 복사하여 메모장에 넣으면 인덱스가 0~46이고 row는 48 컬럼은 1인 DF 파일을 만들 수 있게 됨. .csv로 저장할 수 있다.
> 이 때 csv 파일로 변환하여 저장 할 때 조건을 따로 주어서 col를 나눌 수 있다.
***
![스크린샷 2024-03-27 084002](https://github.com/leonadro-3/python/assets/69701682/9f389035-37ed-4b34-8a41-9044fe998c9d)


### 04 폴더 내 파일 목록들을 가져와 csv 파일 읽어보기 (head, tail, shape)

```
import pandas as pd
df1 = pd.read_csv('./List_seoul/Seoul.csv', header=None)
print(df1.head())
```
![스크린샷 2024-03-27 090845](https://github.com/leonadro-3/python/assets/69701682/4ccf1a19-a015-415b-aa25-752548cc7363)

### 05 파일의 제목을 조건에 따라서 변경하고 싶은 경우 (list와 index 범위 생각하기)

문제 : 파일의 제목을 조건에 따라서 변경하고 싶음.

-> 기존에 있던 모든 파일명을 (지역명)_(행정구역)_(갑,을,병,정...).xlsx로 바꾸고 싶음.
즉, "서울특별시" + "행정구역" + "갑,을,병,정..." + '.xlsx'이 되어야 함.

![스크린샷 2024-03-27 083022](https://github.com/leonadro-3/python/assets/69701682/b8764519-288a-4a11-af61-377941b1a91b)

문제 범위 정의 1-1. 첫번째 문자열 반환 (지역명) - 해결 완료

=> 0~34(35번째) index에 해당하는 모든 것들을 서울특별시로 바꾸면 첫번째 문자열은 해결됨. 
=> 왜냐하면 파일명이 담긴 리스트의 0~34번 인덱스는 모두 같기 때문임.
=> 이를 확인하기 위해서 ./List_seoul/Seoul.csv를 가져오고 각 row의 값들중 0~34번 텍스트의 값들이 모두 같은지 확인해보면 됨.

문제 범위 정의 1-2. 두번째 문자열 (행정구역)

35~는 행정구역별로 문자열의 길이가 달라짐. 예를들면 강동구(갑~을),영등포구(갑~을)이 있음.
따라서 갑,을,병,정,무,기,경,신,임,계 순으로 되었을 때 해당하는 12지신 앞글자가 온다면 
파일마다 달라지는 두번째 문자열의 인덱스를 특정할 수 있음.

1-2-1 파일별로 문자열이 길이가 달라지는 것을 확인해보자. (파일별 이름의 길이는 일정하지 않음)
1-2-2 35~ 문자열의 길이가 어떻게 달라지는지 확인해보자. 
1-2-3 총 문자열 = 고정 문자열(0~34) + 변동 문자열 + 고정 문자열(맨 끝에서 5개)

문제 범위 정의 1-3. 세번째 문자열 (갑,을,병,정) 



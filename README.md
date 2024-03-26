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

### 02 판다스로 .xlsx 파일 읽기
```
import  pandas as pd
filename = "./excel/seoul/[제22대_국회의원선거]_후보자_명부[국회의원선거][서울특별시][강남구갑].xlsx"
df = pd.read_excel(filename, engine='openpyxl')
print(df)
```

### 03 OS로 폴더 내 모든 파일 이름 나열하기 (리스트로 반환 : 한줄에 표시)
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

### 04 OS로 폴더 내 모든 파일 이름 출력하기 (콘솔에 출력 : 한줄에 하나씩 표시)
```
import os
# 주어진 디렉토리에 있는 항목들의 이름을 담고 있는 리스트를 반환합니다.
# 리스트는 임의의 순서대로 나열됩니다.
file_path = './excel/seoul'
file_names = os.listdir(file_path)
for i in range(48):
    print(file_names[i])
```
>여기서 반복문의 횟수(48)를 명시했는데 len(file_names)으로 처리하면 더 좋다. 왜냐하면
>파일의 총 갯수는 계속해서 달라지기 때문이기도 하고 반복문을 돌릴 때마다 갯수를 세서 돌리지 않아도 되기 때문이다.

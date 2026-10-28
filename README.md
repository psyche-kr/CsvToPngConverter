# CsvToPngConverter

CSV에 기록된 16개 지점의 RGB 값을 4×4 원형 색상 이미지(PNG)로 바꿔 주는 Windows 프로그램입니다.
[Image RGB Analyzer](https://github.com/psyche-kr)의 후속 버전으로, 지인의 화학실 실험 의뢰를 받아 제작했습니다.

## 사용 방법
1. `CSV 폴더 선택`으로 CSV 파일이 들어 있는 폴더를 고릅니다.
2. `저장 폴더 선택`으로 PNG를 저장할 폴더를 고릅니다.
3. `변환`을 누르면 CSV 파일마다 하위 폴더가 만들어지고, CSV의 행 하나가 PNG 한 장으로 저장됩니다.

## CSV 형식
- 인코딩: CP949(한글 Windows에서 저장한 CSV)
- 열: `Name`, `Time`, `1_R`, `1_G`, `1_B` … `16_R`, `16_G`, `16_B`
- RGB 값은 0–255로 보정(범위를 벗어나면 자르고, 소수는 반올림)합니다.

## 출력
- 290×290 PNG, 검은 배경에 지름 50px 원 16개를 4×4로 배치(간격 20px, 여백 10px)
- 원 순서는 1번 지점이 왼쪽 위, 16번 지점이 오른쪽 아래
- 파일명: `001_<Time>_<Name>.png` (파일명에 쓸 수 없는 문자는 `_`로 치환)

## 기술
C# / .NET 8 / Windows Forms, CsvHelper, SixLabors.ImageSharp

## 빌드
```
dotnet build -c Release
```

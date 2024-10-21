---
title: 내가 보려고 만든 Markdown 문법
date: 2024/10/21 10:01:15
categories: [내가 보려고 만든]
tags: [Markdown, .md, 문법, Blog]
thumbnail: /images/2024/10/21/markdownImge.png
---

![](/images/2024/10/21/markdownImge.png)<br>

# 📘 마크다운(Markdown) 완벽 가이드

## 목차
- [1. 제목 (Headers)](#1-제목-headers)
- [2. 강조 (Emphasis)](#2-강조-emphasis)
- [3. 목록 (Lists)](#3-목록-lists)
- [4. 링크 (Links)](#4-링크-links)
- [5. 이미지 (Images)](#5-이미지-images)
- [6. 코드 (Code)](#6-코드-code)
- [7. 표 (Tables)](#7-표-tables)
- [8. 인용문 (Blockquotes)](#8-인용문-blockquotes)
- [9. 수평선 (Horizontal Rules)](#9-수평선-horizontal-rules)
- [10. 체크박스 (Task Lists)](#10-체크박스-task-lists)
- [11. 각주 (Footnotes)](#11-각주-footnotes)
- [12. 이모지 (Emoji)](#12-이모지-emoji)

## 1. 제목 (Headers)
```markdown
# H1 제목
## H2 제목
### H3 제목
#### H4 제목
##### H5 제목
###### H6 제목
```
실제 보이는 모습:
# H1 제목
## H2 제목
### H3 제목
#### H4 제목
##### H5 제목
###### H6 제목

## 2. 강조 (Emphasis)
```markdown
*이텔릭체* 또는 _이텔릭체_
**굵은 글씨** 또는 __굵은 글씨__
***굵은 이텔릭체*** 또는 ___굵은 이텔릭체___
~~취소선~~
```
실제 보이는 모습:
*이텔릭체* 또는 _이텔릭체_
**굵은 글씨** 또는 __굵은 글씨__
***굵은 이텔릭체*** 또는 ___굵은 이텔릭체___
~~취소선~~

## 3. 목록 (Lists)
### 순서 있는 목록
```markdown
1. 첫 번째 항목
2. 두 번째 항목
3. 세 번째 항목
```
실제 보이는 모습:
1. 첫 번째 항목
2. 두 번째 항목
3. 세 번째 항목

### 순서 없는 목록
```markdown
* 항목 1
* 항목 2
  * 하위 항목 2.1
  * 하위 항목 2.2
* 항목 3

- 또는 이렇게
+ 또는 이렇게
```
실제 보이는 모습:
* 항목 1
* 항목 2
  * 하위 항목 2.1
  * 하위 항목 2.2
* 항목 3

## 4. 링크 (Links)
```markdown
[구글로 가기](https://www.google.com)
[구글로 가기](https://www.google.com "구글 홈페이지")
URL 직접 노출: <https://www.google.com>
참조 링크: [참조 링크][1]
[1]: https://www.google.com
```
실제 보이는 모습:
[구글로 가기](https://www.google.com)
[구글로 가기](https://www.google.com "구글 홈페이지")
URL 직접 노출: <https://www.google.com>

## 5. 이미지 (Images)
```markdown
![대체 텍스트](이미지_URL)
![대체 텍스트](이미지_URL "이미지 제목")

[![이미지 링크](이미지_URL)](링크_URL)
```

## 6. 코드 (Code)
### 인라인 코드
```markdown
이것은 `인라인 코드`입니다.
```
실제 보이는 모습:
이것은 `인라인 코드`입니다.

### 코드 블록
````markdown
```python
def hello_world():
    print("Hello, World!")
```
````
실제 보이는 모습:
```python
def hello_world():
    print("Hello, World!")
```

## 7. 표 (Tables)
```markdown
| 제목 1 | 제목 2 | 제목 3 |
|:--------|:--------:|--------:|
| 왼쪽 정렬 | 가운데 정렬 | 오른쪽 정렬 |
| 내용 11 | 내용 12 | 내용 13 |
| 내용 21 | 내용 22 | 내용 23 |
```
실제 보이는 모습:
| 제목 1 | 제목 2 | 제목 3 |
|:--------|:--------:|--------:|
| 왼쪽 정렬 | 가운데 정렬 | 오른쪽 정렬 |
| 내용 11 | 내용 12 | 내용 13 |
| 내용 21 | 내용 22 | 내용 23 |

## 8. 인용문 (Blockquotes)
```markdown
> 첫 번째 인용문
>> 두 번째 인용문
>>> 세 번째 인용문
```
실제 보이는 모습:
> 첫 번째 인용문
>> 두 번째 인용문
>>> 세 번째 인용문

## 9. 수평선 (Horizontal Rules)
```markdown
---
***
___
```

실제 보이는 모습:
---
***
___

## 10. 체크박스 (Task Lists)
```markdown
- [x] 완료된 작업
- [ ] 미완료된 작업
- [x] ~~취소된 작업~~
```
실제 보이는 모습:
- [x] 완료된 작업
- [ ] 미완료된 작업
- [x] ~~취소된 작업~~

## 11. 각주 (Footnotes)
```markdown
각주<sup>[1](#각주 이름)</sup>

<a name="각주 이름">1</a>: 각주에 대한 설명
```
실제 보이는 모습:
각주<sup>[1](#각주 이름)</sup>

<a name="각주 이름">1</a>: 각주에 대한 설명

## 12. 이모지 (Emoji)
```markdown
:smile: :heart: :thumbsup
```

모든 마크다운 에디터가 이모지를 지원하는 것은 아님.

---

## 🎯 마크다운 작성 팁
1. **간결성**: 마크다운의 가장 큰 장점은 간결함이다. 복잡한 서식보다는 단순하고 깔끔한 구조를 유지한다.
2. **일관성**: 문서 전체에서 일관된 서식을 사용한다.
3. **가독성**: 적절한 여백과 구분선을 사용하여 문서의 가독성을 높인다.

## 🔍 유용한 마크다운 에디터
- Visual Studio Code
- Typora
- StackEdit
- Dillinger
- HackMD

# 마크다운 문법

## 마크다운

### 마크다운

제목은 `#`로 표현가능하다. `H1`~`H6`까지 표현가능하다.

### 제목3

#### 제목4

##### 제목5

###### 제목6

* 목록은 
* 순서가 없는 목록이 있다.
  * 탭을 통해 목록 수준을 표현할 수 있다.
  * 엔터하고 탭만 잘 사용하면 된다.

1. 순서가 있는 목록도 있다.

* 섞어서 쓸 수도 있다.
  * 이렇게.



## 코드 블록

```
print('hello!')
#이것은 주석입니다.
```

```html
<!-- 주석 -->
# 주석 아님
<h1>
    안녕
</h1>
```

## 링크

외부 URL: [google](http://google.com)

특정 파일의 상대 경로: [README](./README.md)



## 이미지

![william](C:\Users\i\Desktop\william.jpg)

그냥 이걸 끌어다 놓으면 절대경로로 들어오는데, 깃허브 입장에서는 C드라이브가 없으니까

파일이 존재하지 않게 된다. 그래서 상대경로로 설정해주자. 따라서 typora에 다음과 같은 설정을 해보자.

![william](../markdown-images/william-1597904494242.jpg)

* 파일 
* 환경설정
* 이미지
* copy image to cutom folder 선택
* ./ 에다가 원하는 폴더 생성
* 밑에 3개 차례대로 선택
  * 이렇게 해주면 이 자체를 깃허브에 올릴 거기 때문에 이미지가 상대경로로
  * 알아서 같이 올릴 수 있게 된다.

| 이름   | 나이 | 성별 |
| ------ | ---- | ---- |
| 안서정 | 27   | 여   |
|        |      |      |
|        |      |      |



*기울임 이탤릭체*

**볼드체**

~~취소선~~

`인라인코드블럭`





*내가 원하는 프로젝트의 위치에서 git init을 하는지 꼭 확인해라*





# GIT 기초

Git을 윈도우에서 활용하기 위해서는 [git bash](https://gitforwindows.org/)를 설치해야 한다.

> Git은 분산형 버전관리시스템(DVCS)이다.



## 저장소 설정

### 1. 저장소 초기화

```bash
i@DESKTOP-CS5B0E0 MINGW64 ~/Desktop/TIL
$ git init
Initialized empty Git repository in C:/Users/i/Desktop/TIL/.git/

i@DESKTOP-CS5B0E0 MINGW64 ~/Desktop/TIL (master)
```

* 로컬 저장소를 만들고 나면, `.git/`폴더가 생성되고, bash에 `(master)`라고 표기 된다.
* 반드시 저장소를 만들기 전에 원하는 디렉토리인지 확인하는 습관을 가지고, 저장소 내부에 저장소를 만들지는 말자.
  * 예) Desktop ->  git 저장소, TIL -> 다른 git 저장소 (x)
  * 즉, 해당 프로젝트에서는 최초 한 번만. 
  * 그리고 잘못된 공간에서 하지 않도록.



## 2. add

작업한 내용을 커밋 대상 목록에 추가한다.

```bash
$ git status
On branch master

No commits yet
# Untracked files: Git으로 관리된 적 없는 파일
Untracked files:
#커밋 될 것들에 포함시키기 위해서는 add 명령어를 써라
  (use "git add <file>..." to include in what will be committed)
        markdown-images/
        markdown.md

#총평
#커밋될 곳에 없다(nothing)
#하지만, 새로 생성된 파일(untracked files)은 존재한다.
nothing added to commit but untracked files present (use "git add" to track)

$ git add .
# git 파일을 추가해준다.

$ git status
On branch master

No commits yet
#커밋이 될 변경사항들
#Working Directory X
#Staging area O
Changes to be committed:
  (use "git rm --cached <file>..." to unstage)
        new file:   markdown-images/william.jpg
        new file:   markdown.md
```

## 3. Commit

```bash
$ git commit -m 'Add markdown.md'
[master (root-commit) 78c4dea] Add markdown.md
 2 files changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 markdown-images/william.jpg
 create mode 100644 markdown.md
```

* 커밋은 버전(이력)을 기록하는 명령어이다.
* 커밋 메시지는 해당하는 이력을 나타낼 수 있도록 작성하여야한다.
* 커밋 이력을 확인하기 위해서는 아래의 명령을 사용한다.

```bash
$ git log
commit 78c4dea78b539a4674f4c9f102d579aab2600626 (HEAD -> master)
#이 commit이 같아야 한다.
Author: asja95 <asja95@naver.com>
Date:   Thu Aug 20 14:58:09 2020 +0900

    Add markdown.md
$ git log -1    
$ git log --oneline
$ git log --oneline -1
78c4dea (HEAD -> master) Add markdown.md

$ git status
On branch master
nothing to commit, working tree clean
```



* 작업한 내용을 커밋 대상 목록에 추가한다.

```bash
$ git add .  # 현재 디렉토리(하위 디렉토리 포함)
$ git add a.html  # 특정 파일
$ git add b.html c.html  # 특정 다수 파일
$ git add blog/  # 특정 폴더
```


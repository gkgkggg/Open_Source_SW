# Week 4 Lecture Note — Shell Commands

> 기억 순서: **현재 위치 확인 → 이동 → 목록 확인 → 만들기·복사·이동 → 삭제 → 도움말**

## 1. 터미널 실행

- **Kernel**: 하드웨어 자원 관리 (운영체제의 핵심)
- **Shell**: 사용자-> 명령 입력 ->(상호작용) ->커널 및 프로그램. Bash, zsh 등이 있다.
- **CLI**: 명령어를 글자로 입력하는 방식. 같은 작업을 반복할 때 명령을 다시 실행하거나 스크립트로 자동화할 수 있다. add -> gui, nui ..


## 2. find route
| 명령 | 기억할 뜻 | 예시 |
|---|---|---|
| `pwd` | **p**rint **w**orking **d**irectory: 현재 디렉터리의 경로 출력 | `pwd` |
| `ls` | **l**i**s**t: 파일과 디렉터리 목록 표시 | `ls`, `ls folder1` |
| `cd` | **c**hange **d**irectory: 작업 디렉터리 이동 | `cd folder1`, `cd ..` |

경로 기호는 장소를 나타낸다: `.` = 현재 디렉터리, `..` = 상위 디렉터리, `~` = 내 홈 디렉터리, `/` = 루트 또는 절대경로의 시작. **절대경로**는 `/`에서 시작하고, **상대경로**는 현재 위치를 기준으로 해석한다.

```bash
pwd                    # 현재 위치 확인
ls                     # 현재 위치의 목록
cd oss                 # oss로 이동
cd folder1             # 그 아래 folder1로 이동
cd ..                  # 다시 상위 디렉터리로
cd ~                   # 홈으로 이동
```

`ls -l`은 권한·소유자·크기·수정 시각 등을 긴 형식으로 보여준다. `ls -lh`는 크기를 읽기 쉬운 단위(K, M 등)로 표시한다. `ls -la ..`은 상위 디렉터리의 숨김 파일(`.`으로 시작)을 포함해 자세히 보여준다. 긴 형식에서 맨 앞의 `d`는 디렉터리, `-`는 일반 파일을 뜻한다.

## 3. 파일과 디렉터리 조작

| 명령 | 역할 | 바로 떠올릴 예시 |
|---|---|---|
| `mkdir` | 새 디렉터리 생성 (make directory) | `mkdir asset` |
| `cp` | 파일 복사(copy) | `cp README.md README_copy.md` |
| `cp -r` | 디렉터리와 내부 내용까지 재귀 복사 -reculsive | `cp -r folder1 folder1_backup` |
| `mv` | 이동 또는 이름 변경(move) | `mv old.txt new.txt`, `mv new.txt folder1/` |
| `rm` | 파일 삭제(remove) | `rm -i old.txt` |
| `rm -r` | 디렉터리와 내부 내용 삭제 -reculsive | `rm -r old_folder` |

기억법: **`cp`는 원본이 남고, `mv`는 원본 위치에서 사라진다.** `mv A B`에서 `B`가 없는 이름이면 이름 변경, `B`가 기존 디렉터리이면 그 안으로 이동한다. `cp`와 `mv`는 대상 파일을 덮어쓸 수 있으므로, 확인 질문이 필요한 경우 `cp -i`, `mv -i`를 쓴다.

**삭제 주의:** `rm`은 휴지통으로 보내지 않는다. 특히 `rm -r`은 내용까지 지우므로 위치와 대상을 `pwd`, `ls`로 확인한다. 강의의 `cp -r ../folder1 ./new_folder`처럼 `../`와 `./`을 구분해야 예상한 위치에 복사된다.

## 4. wildcard 파일 검색 등등(sql 그거랑 비슷)

| 패턴 | 의미 | 예시 |
|---|---|---|
| `*` | 글자 0개 이상 | `*.txt` → `.txt`로 끝나는 이름 |
| `?` | 글자 정확히 1개 | `Data???` → `Data` 뒤에 3글자 |
| `b*.txt` | `b`로 시작하고 `.txt`로 끝나는 이름 | `book.txt` |

```bash
ls *.txt                 # 먼저 일치하는 파일 확인
cp *.txt text_files/     # 해당 파일을 기존 디렉터리에 복사
```

와일드카드와 `rm`을 함께 쓸 때는 먼저 **같은 패턴을 `ls`로 확인**한다. 

## 5. 빠른 입력과 도움말

- 파일명 앞부분 입력 후 **Tab**: 경로/이름 자동 완성.
- **↑**: 이전 명령 불러오기.
- `clear`: 화면 지우기(파일은 삭제하지 않음).
- `help cd`: Bash 내장 명령 `cd`의 도움말.
- `man cp`: `cp`의 매뉴얼 페이지. `q`로 종료.

## 6. 정리

```bash
mkdir shell_practice
cd shell_practice
pwd
mkdir asset
cp -r asset asset_copy
ls -lh
mv asset_copy backup
ls -la
cd ..
```

결과  `shell_practice` 안에는 `asset`과 `backup`

## 정보처리기사 내용 그대로 하면 됨

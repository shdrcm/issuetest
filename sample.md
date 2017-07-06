# 디렉토리 구조

GitBook 은 간단한 디렉토리 구조를 사용합니다. [개요](pages.md)에 나열된 모든
마크다운/Asciidoc 파일들은 HTML 로 변환될 것 입니다. 다국어 책은 약간
[다른 구조](languages.md)를 가지고 있습니다.

기본 GitBook 은 일반적으로 다음과 같습니다:

```
.
├── book.json
├── README.md
├── SUMMARY.md
├── chapter-1/
|   ├── README.md
|   └── something.md
└── chapter-2/
    ├── README.md
    └── something.md
```

각각의 것들에 대한 개요입니다:

| 파일 | 설명 |
| -------- | ----------- |
| `book.json` | [설정](config.md) 데이터 저장 (__선택__) |
| `README.md` | 서문 / 책에 대한 소개 (**필수**) |
| `SUMMARY.md` | 목차 ([페이지](pages.md))를 보세요 (__선택__) |
| `GLOSSARY.md` | 사전 / 용어 목록 주석 ([용어](lexicon.md)를 보세요) (__선택__) |

### 정적 파일과 그림

정적 파일은 `SUMMARY.md` 에 나열되지 않은 파일입니다. 모든 정적파일은 무시하지
않는 한 출력에 복사됩니다.

### 파일 및 폴더 무시 {#ignore}

GitBook 은 무시할 파일과 폴더의 목록을 얻기위해 `.gitignore`, `.bookignore`,
`.ignore` 파일을 읽을 것 입니다. 파일의 내부 형식은 `.gitignore` 와 같은 규칙을
따르며 다음과 같습니다:

```
# 이것은 덧글입니다.

# test.md 파일 무시
test.md

# "bin" 디렉토리 무시
bin/*
```

### 하위디렉토리로 프로젝트 통합 {#subdirectory}

소프트웨어 프로젝트의 경우 프로젝트의 문서에 대한 책을 저장하기 위해
(`docs/` 같은) 하위 디렉토리를 사용할 수 있습니다. GitBook 이 책의 파일을 찾을
수 있는 폴더를 나타내기 위해 [`root` 옵션](config.md)을 설정할 수 있습니다.

```
.
├── book.json
└── docs/
    ├── README.md
    └── SUMMARY.md
```

`book.json` 은 다음을 포함합니다:

```
{
    "root": "./docs"
}
```

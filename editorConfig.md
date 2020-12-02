# .editorConfig

* [EditorConfig](https://EditorConfig.org) 는 여러 편집기(Text Editor) 에서 일관 된 코딩 스타일을 유지하도록 도와주는 설정파일입니다.

```bash
# top-most EditorConfig file
root = true

[*] # 모든 파일에 적용
charset = utf-8
# Unix Style 의 line ending (\n) 시용
end_of_line = lf
insert_final_newline = true
# 들여쓰기 형식은 4 space
indent_style = space
indent_size = 4
# 불필요한 공백 제거
trim_trailing_whitespace = true

[*.{json,xml}]
# brace({}) 안에 정의 된 json, xml 파일에는 아래 정의를 사용
indent_style = space
indent_size = 2
```

* EditorConfig 를 Native 지원하는 툴 목록
    * VisualStudio
    * GitHub
    * GitLab
    * ReSharper
    * PyCharm
    * Rider
    * RubyMine
    * ...

* Plugin 설치시 지원되는 툴 목록
    * [Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=EditorConfig.EditorConfig)
    * [Sublime Text](https://github.com/sindresorhus/editorconfig-sublime#readme)
    * [Vim](https://github.com/editorconfig/editorconfig-vim#readme)
    * Notepad++
    * Emacs
    * ...

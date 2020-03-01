순수 VSCode에서 제공하는 import 순서를 정리해줄 뿐만이 아니라, 사용하고 있지 않은, 선언되기만 한 import는 자동으로 지워주는 유용한 기능이 있습니다.  

바로 `organize imports` 인데요,
`command` + `shift` + `P` -> `Organize Imports` 로 접근할 수 있습니다.  

단축키는 `option` + `shift` + `O` 이며, 저장 시에 `organize import`를 자동으로 실행시키고 싶으면
```
    "editor.codeActionsOnSave": {
        "source.organizeImports": true
    }
```  

위의 코드를 settings.json에 추가하시면 됩니다.
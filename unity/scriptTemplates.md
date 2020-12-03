# Unity Script Templates

* Unity 에서 스크립트 (MonoBehavior), Shader 등의 코드를 생성할 때 기본이 되는 템플릿입니다.
* 템플릿 파일 경로
    * *(EditorPath)/Data/Resources/ScriptTemplates*

* Create 에 정의 된 스크립트 생성에 대한 기본 템플릿이 정의 되 있습니다. 예를 들어, Create > C# Script 를 선택 시에는 다음의 템플릿으로 파일을 생성합니다 (*81-C# Script-NewBehaviourScript.cs.txt*)

```c#
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

public class #SCRIPTNAME# : MonoBehaviour
{
  // Start is called before the first frame update
  void Start()
  {
    #NOTRIM#
  }

  // Update is called once per frame
  void Update()
  {
    #NOTRIM#
  }
}
```

Create > 메뉴와 대응하는 Script Template 을 수정하면 해당 메뉴를 실행하여 스크립트 생성시 수정 된 템플릿을 사용하여 파일을 생성합니다.

**But!**

그렇게 하면, 특정 프로젝트가 아닌 모든 프로젝트에 반영 됩니다.

**특정 프로젝트에만 반영하기 위해서**

각 프로젝트의 Assets/ScriptTemplates 폴더를 추가하고, 템플릿 파일을 작성하시면 됩니다.

## Tip!

템플릿 파일의 명명에는 일정한 룰이 있습니다.

[Order]-[Menu]__[Sub Menu]-[CreateTempName].{확장자}.txt

예를 들어, 다음과 같이 명명하여 추가하면,

```xml
0-Egg C# Script__Egg-ClassName.cs.txt
```

Create > Egg C# Script > Egg 라는 메뉴가 생성되고, 해당 메뉴를 선택 시 ClassName.cs 라는 파일이 임시 생성 됩니다.

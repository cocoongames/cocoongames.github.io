# Unity Script Templates

* Unity 에서 스크립트 (MonoBehavior), Shader 등의 코드를 생성할 때 기본이 되는 템플릿입니다.
* 템플릿 파일 경로
    * *(EditorPath)/Data/Resources/ScriptTemplates*

* 81-C# Script-NewBehaviourScript.cs.txt

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

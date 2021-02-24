# C# Coding Style

* .NET/runtime coding-guidelines 를 기본으로 제작했습니다.

---

## 들여쓰기는 스페이스 사용합니다. (간격 : 4)
## Allman style brace 사용합니다. (each brace begins on a new line).
- 단일 구문의 경우에는 brace를 생략 가능하지만, 들여쓰기는 맞춥니다.

```c#
public void Method()
{
    if (source == null)
        return;
}
```

- 단일 행은 사용하지 않습니다.

```c#
// if (source == null) return;
```

- using 문의 경우 예외로 합니다.

```c#
public void Method()
{
    using (var fileStream = new FileStram(...))
    using (var memoryStream = new MemoryStream(...))
    {
        ...
    }
}
```

## 맴버변수 (private field)는 _camelCase 을 사용
- 가능하면 readonly 로.
- 접근 지정자를 항상 표시하며, 가장 앞에 표시한다.
- 다음과 같은 케이스에서는 Prefix 를 붙인다.

```c#
private static int s_field; // static 인 경우
private static int t_field; // thread static 인 경우
```

- static 키워드는 readonly 다음에 쓴다. ( readonly static .. )

```c#
private readonly static int s_field;
```

## Public 은 PascalCasing 을 쓰며 Prefix 를 사용하지 않는다.

```c#
public int FirstName;
```

## 꼭 필요한 경우가 아니면 this. 를 사용하지 않는다.

## Namespace imports 는 알파벳 순으로 정렬한다.

```c#
using CocoonGames.Core;
using CocoonGames.Core.ComponentManagement;
using System;
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

namespace CocoonGames.Egg.UI
{

}
```

## 항상 두 줄 이상의 빈 줄을 피한다.

```c#
public int Number;
// 두 줄 이상의 빈 줄을 피한다.
private void Method()
{
    ...
}
// 두 줄 이상의 빈 줄을 피한다.
private void AnotherMethod()
{
    ...
}
```

## 라인의 끝에 빈 공백이 없도록 한다.

```c#
public void Method()
{
....int a = 0;
//..int b = 0;.
}
```

## 변수의 타입을 명확히 알 수 있을 때만 var 를 사용합니다.

```c#
var stream = new FileStream();
// var stream = OpenStandardInput();
```

## Base Class Library type 대신 키워드와 메서드 호출을 사용합니다.

```c#
int, string, float
// Int32, String, Float

int.Parse(...)
// Int32.Parse(...)
```

## const 변수는 PascalCasing 을 사용합니다.

```c#
public const string CompanyName = "CocoonGames";
```

## 로컬함수를 포함한 모든 메서드에 PascalCasing 을 사용합니다.

```c#
public class ClassName
{
    private void PrivateMethod()
    {
        ...
    }

    public void PublicMethod()
    {
        ...

        void LocalMethod()
        {
            ...
        }
    }
}
```

## nameof 를 사용할 수 있다면 리터럴은 지양하고 nameof를 사용합니다.

```c#
nameof(Something);
// "SomethingName"
```

## 필드는 상단에 선언합니다.

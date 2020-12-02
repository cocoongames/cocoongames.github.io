# Naming Guidelines

* .NET fundamentals/Framework design guidelines 를 기본으로 제작했습니다.

---

## General Naming Conventions

> ### _Readable, Semantically_

* 이해하기 쉬운 표현을 선택합니다.

```c#
CanScrollHorizontally
// ScrollableX (X 축에 대한 모호한 정의)
```

* 알파벳, 숫자가 아닌 문자를 사용하지 않습니다. (Member field 의 경우 _camelCase 로 예외적으로 _ 사용)
* 프로그래밍 언어에서 널리 사용되는 키워드들은 피합니다.
* 축약 된 단어나 두문자어의 사용을 자제합니다. 범용적인 표현인 경우에는 필요한 경우에 따라 사용합니다.
* 범용적인 두문자어인 경우 사용시, 두단어인 경우 모두 대문자로 쓰지만 아닌 경우에는 PascalCasing 으로 표현합니다.

```c#
GetWindow
// GetWin
Http
// HTTP
UI
// Ui
```

* 새로운 속성이나 함수를 작성할 때 접미사 (Ex. 제외)를 추가합니다. (IntelliSense 활용시 알파벳 순으로 표시되기 때문에 관련 함수가 같이 나오게 되는 효과가 있습니다.)

```c#
// 기존에 있던 함수
private long Clamp(long value)
{
    ...
}

// 새로 추가한 함수
private int ClampInt32(long value)
{
    ...
}

// private int Int32Clamp(long value)
// private int ClampEx(long value)
```

## Name of Namespaces

```xml
<Company>.(<Product>|<Technology>)[.<Feature>][.<Subnamespace>]>
```

```c#
namespace CocoonGames.Egg;
namespace CocoonGames.Math;
namespace CocoonGames.UI;
```

* 회사명을 추가하여 다른 회사(third party) 제품과 중복되지 않도록 합니다.
* 버전과 독립적인 프로덕트명을 사용합니다.
* PascalCasing 을 사용합니다.
* 복수 표현이 적절한 경우 복수로 표현합니다.

```c#
System.Collections
// System.Collection
```

* namespace 안의 타입과 같은 이름을 사용하지 않습니다.

```c#
// namespace CocoonGames.Egg.Log
namespace CocoonGames.Egg.Debug
{
    public class Log
    {

    }
}
```

## Names of Classes, Structs, and Interfaces
* Class와 Struct의 이름은 PascalCasing 을 사용하며, 명사 혹은 명사구로 정합니다.
    * Method 명과 구분지을 수 있게 됩니다. (메서드는 동사구로 정하기 때문)
* inteface 의 이름은 형용사구를 사용하지만, 명사나 명사구로 정할 수도 있습니다.
* Class 의 이름을 접두사로 사용하지 않습니다.
* 자식 Class 를 명명 할 때 부모 Class 의 이름이 뒤에 올 수 있도록 하면 좋습니다.
    * 해독을 쉽게 하거나, 관계를 명확하게 하는 경우 권합니다.

```c#
public class MemoryStream : Stream { ... }

public class Button : Control
//public class ButtonControl : Control
```

* interface 는 명명할 때 'I' 로 시작합니다. (형용사구를 권하지만 명사나 명사구를 사용할 수도 있어 class, struct 등과 구분짓기 위함입니다.)

* Generic 형식의 매개 변수명은 가능한 대문자 한글자로 표현합니다.

```c#
public class LinkedList<K, T> { ... }
// public class LinkedList<KeyType, DataType> { ... }
```

* 다음의 특정 .NET Framework 의 형식을 파생하여 명명할 때는 지침을 따릅니다.

|Base Type|지침|
|---|---|
|System.Attribute| * Attribute 접미사를 추가합니다.|
|System.Delegate| * 이벤트에 사용 되는 delegate 에는 EventHandler 접미사를 추가합니다. |
||  * 이벤트에 사용 된 delegate 외에는 CallBack 접미사를 추가합니다.|
|| * *Delegate 접미사를 추가하지 않습니다.*|
|System.EventArgs| * EventArgs 접미사를 추가합니다.|
|System.Exception| * Exception 접미사를 추가합니다.|

* Naming Enumerations
    * 단수형으로 명명합니다.
    * bit flag 형태의 경우 Flags 접미사를 추가합니다.
    * *Enum 을 접미사로 사용하지 않습니다.*
    * *value 에 타입명의 두문자어를 사용하지 않습니다.*

```c#
public enum AudioType { ... }
// public enum AudioTypes { ... }

[Flags]
public enum CollisionFlags
{
    None = 0,
    Sides = 1,
    Above = 2,
    Below = 4
}

public enum AudioType
{
    Unknown,
    // atUnknown,
    ...
}
```

## Names of Type Members
* Name of Methods
    * Method 명은 PascalCasing 을 사용하며, 동사나 동사구로 정합니다.
* Name of Properties
    * Property 명은 PascalCasing 을 사용하며, 명사나 명사구로 정합니다. 형용사를 사용 할 수도 있습니다.
    * Boolean Property 의 경우에는 긍적적인 구문으로 명명합니다.
    * 가능한 경우 해당 형식과 같은 이름으로 명명합니다.

```c#
public class Control
{
    public bool Enable { get; set; }
    // public bool Disable { get; set; }

    // 형식과 Property 명을 같게 한 경우
    public Color Color { get; set; }
}
```

* Name of Events
    * Event 명은 PascalCasing 을 사용하며, 동사나 동사구로 정합니다.
    * Event 발생의 시제를 알 수 있도록 명명합니다.

```c#
public delegate void ClosingEventHandler(object sender, ClosingEventArgs e);
public event ClosingEventHandler Closing; // 닫히는 도중

public delegate void ClosedEventHandler(object sender, ClosedEventArgs e);
public event ClosedEventHandler Closed; // 완전히 닫힌 후
```

## Naming Parameters
* Parameter 명은 camelCasing 을 사용합니다.

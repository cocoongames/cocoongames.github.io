# Helper Class and Method

> Helper Class 의 통용되는 의미와는 무관하게 '루마니아에'에서는 한가지 이상의 작업을 수행하는 메서드를 정의해야 할 필요가 있고, 해당 메서드를 여러 곳에서 사용하여 중복된 작업을 피할 수 있도록 하는데 이점이 있는 형태일 때 사용하는 것으로 정의합니다.

> 메서드가 특정 클래스의 기본 관심사 (primary concern) 인지 검토 해 봅니다. 그렇다면, 특정 클래스의 인스턴스 메서드로 정합니다.

---

## Utility Class 와 명확하게 구분짓지 않으며, Utility 라는 키워드를 사용하지 않고 해당 클래스의 역할이 짐작될 수 있는 네이밍을 하는 것으로 정합니다.

```c#
// public class JsonUtility
// public class JsonHelper
public class JsonLoader
```

## Helper, Extensions 의 경계도 명확하게 구분하지 않습니다. 작성자의 재량이나, 고려 해 보시길 권하는 것은 해당 메서드를 사용하는 곳에서 어떤 방법을 택하는 것이 "작성이 용이한지, 가독성이 좋은지" 판단하여 선택하는 것입니다.

### Case1.


```c#
public void Somewhere()
{
  //building.Assign(target);
  AssignHelper.Assign(building, target);
}
```

- Assign 메서드가 building, target 모두에게 특정 일을 수행하는 것이라면 Extensions 보다는 Helper 가 독해하기 용이하다고 할 수 있습니다. building.Assign(target) 의 경우 building 에게만 target 을 assign 하는 것으로 이해하기 쉽습니다.

### Case2.

```c#
public void Somewhere()
{
  // GameObjectHelper.ChangeLayerRecursively(targetObject, land.layerOrder);
  targetObject.ChangeLayerRecursively(land.layerOrder);
}
```

- Extension 으로 사용 한 경우 Helper class 명(접근자)을 알지 않아도 되고, 메서드의 인자가 줄어드는 등 가독성이 더 용이하다고 할 수 있습니다.

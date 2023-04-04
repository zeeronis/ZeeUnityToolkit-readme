# Global Events

#### Notes:
1. All subscribers will be automatically deleted every time you upload a new scene. Also, u can disable this behavior:
```cs
using Zee.Events;

EventAggregator.ForceCleanOnSceneUnloaded = false;
```

2. Any destroyed subscribers will be automatically deleted

#### How to use:

1. Example events data
```cs
public struct SomeEvent
{
    // Event data
}

public enum SomeEnumEvent
{
    One,
    Two
}
```

2. Subscribe to all events with data type
```cs
using Zee.Events;

EventAggregator.AddListener<SomeEvent>(this, data =>
{
    Debug.Log(data);
});

EventAggregator.AddListener<SomeEnumEvent>(this, data =>
{
    Debug.Log(data);
});
```

2. Unsubscribe
```cs
EventAggregator.RemoveListener<SomeEvent>(this);
EventAggregator.RemoveListener<SomeEnumEvent>(this);
```

3. Invoke event
```cs
EventAggregator.Invoke(new SomeEvent());
EventAggregator.Invoke(SomeEnumEvent.Two);
```

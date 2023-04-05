[![docs badge](https://img.shields.io/badge/docs-reference-blue.svg)](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/README.md)


# Global Events
Сontents:
-  [Notes](GlobalEvents.md#notes)
-  [Events Data](GlobalEvents.md#example-events-data)
-  [Subscribe](GlobalEvents.md#subscribe)
-  [Unsubscribe](GlobalEvents.md#unsubscribe)
-  [Invoke Event](GlobalEvents.md#invoke-event)


##
- ### Notes
All subscribers will be automatically deleted every time you unload scene. Also, u can disable this behavior.
```cs
using Zee.Events;

EventAggregator.ForceCleanOnSceneUnloaded = false;
```

- ### Example events data
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

- ### Subscribe to all events with data type
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

- ### Unsubscribe
Any destroyed(Collected by GC) subscribers will be automatically deleted from listeners.
```cs
using Zee.Events;

EventAggregator.RemoveListener<SomeEvent>(this);
EventAggregator.RemoveListener<SomeEnumEvent>(this);
```

- ### Invoke event
```cs
using Zee.Events;

EventAggregator.Invoke(new SomeEvent());
EventAggregator.Invoke(SomeEnumEvent.Two);
```

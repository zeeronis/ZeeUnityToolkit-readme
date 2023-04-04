# Code Coroutines
Works only inside in Monobehavior scripts, or while u have reference on it.

```cs
// Call inside MonoBehavior, for stop all coroutines running in this MonoBehavior
StopAllCoroutines();
```

#### 1. CustomLerp
```cs
this.DoCustomLerp(float duration, t => 
{
  // Do something
  var value = Mathf.Lerp(0, 100, t);
  Debug.Log(value);
});

// Also, u can use yelders 
this.DoCustomLerp(float duration, t => 
{
  // Do something
  return new WaitForFixedUpdate();
});
```

#### 3. Delays
```cs
Debug.Log("Start coroutine");
this.DoWait(1).ContinueWith(() =>
{
    Debug.Log("Done!");
});

this.DoWaitFrames(60).ContinueWith(() =>
{
    Debug.Log("Done!");
});
```

#### 3. Other coroutines list
```cs
this.DoLerpPosition(transform, duration, from, to)
this.DoLerpPosition(transform, duration, to)

this.DoLerpPositionLocal(transform, duration, from, to)
this.DoLerpPositionLocal(transform, duration, to)

this.DoLerpRotation(transform, duration, from, to)
this.DoLerpRotation(transform, duration, to)

this.DoLerpRotationLocal(transform, duration, from, to)
this.DoLerpRotationLocal(transform, duration, to)

this.DoLerpScaleLocal(transform, duration, from, to)
this.DoLerpScaleLocal(transform, duration, to)
```

[![docs badge](https://img.shields.io/badge/docs-reference-blue.svg)](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/README.md)

Сontents:
-  [Code Coroutines](Coroutines.md#code-coroutines)
   - [Transform Lerps](Coroutines.md#transform-coroutines)
   - [Custom Lerps](Coroutines.md#customlerp)
   - [Delays](Coroutines.md#delays)
   - [Stop Coroutines](Coroutines.md#stop-coroutines)
-  [GameObject Component](Coroutines.md#code-coroutines) - Waiting for documentation;


# Code Coroutines
Works only inside in Monobehavior scripts, or while u have reference on it.

- ### Transform Coroutines
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

- ### CustomLerp
Will lerp within 5 seconds. Also, u can use yelders.
```cs
this.DoCustomLerp(5, t => 
{
  var value = Mathf.Lerp(0, 100, t);
  Debug.Log(value);
});
```
```cs
this.DoCustomLerp(5, t => 
{
  return new WaitForFixedUpdate();
});
```

- ### Delays
Execute the delegate passed to `ContinueWith` after a delay of (1 second / 60 frames).
```cs
Debug.Log("Start coroutine");
this.DoWait(1).ContinueWith(() =>
{
    Debug.Log("Waited 1 second!");
});

this.DoWaitFrames(60).ContinueWith(() =>
{
    Debug.Log("Waited 60 frames!");
});
```

- ### Stop Coroutines
Call inside MonoBehavior, for stop all coroutines running in this MonoBehavior
```cs
StopAllCoroutines();
```

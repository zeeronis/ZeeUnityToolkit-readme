[![docs badge](https://img.shields.io/badge/docs-reference-blue.svg)](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/README.md)

Сontents:
-  [Code Coroutines](Coroutines.md#code-coroutines)
   - [Transform Lerps](Coroutines.md#transform-coroutines)
   - [Custom Lerps](Coroutines.md#customlerp)
   - [Delays](Coroutines.md#delays)
   - [Stop Coroutines](Coroutines.md#stop-coroutines)
-  [Coroutine Animation Component](Coroutines.md#coroutine-animation-component)
   - [IsLoop](Coroutines.md#1---isloop)
   - [Play On Enable](Coroutines.md#2---play-on-enable)
   - [Reset On Play](Coroutines.md#3---reset-on-play)
   - [Duration](Coroutines.md#4---duration)
   - [Update method](Coroutines.md#5---update-method)
   - [Space Type](Coroutines.md#6---space-type)
   - [Animate Type](Coroutines.md#7---animate-type)
   - [Relative Scale Operation Mode](Coroutines.md#8---relative-scale-operation-mode)
   - [Animation Curves](Coroutines.md#9---animation-curves)


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


# Coroutine Animation Component
This component is designed to create simple animations without using the heavyweight `Animator`.
It is a `MonoBehavior` script that launches the `Unity Coroutine` for animation.

![image_2023-04-15_10-03-46](https://user-images.githubusercontent.com/15892895/232194739-c2215ba4-fcca-485b-a963-72ddd2e71ed4.png)


- ### 1 - IsLoop
Animation will play in a loop.

- ### 2 - Play On Enable
When the `GameObject` is activated, the animation will start or continue playing.

- ### 3 - Reset On Play
Each time `Play()` is called, the animation will reset and start playing from the beginning. This applies both to the call from the code and during automatic playback from `Play On Enable`.

- ### 4 - Duration
The length of the current animation in seconds.

- ### 5 - Update method
1. [Update](https://docs.unity3d.com/ScriptReference/MonoBehaviour.Update.html) - `Update` is called every frame.
2. [LateUpdate](https://docs.unity3d.com/ScriptReference/MonoBehaviour.LateUpdate.html) - LateUpdate is called every frame, after `Update`.
3. [FixedUpdate](https://docs.unity3d.com/ScriptReference/MonoBehaviour.FixedUpdate.html) - Frame-rate independent `MonoBehaviour.FixedUpdate` message for physics calculations. (By default 50 times per second).
3. **RealtimeUpdate** - Will ignore the game timescale and play in realtime.

![image_2023-04-15_10-04-29](https://user-images.githubusercontent.com/15892895/232194742-bb90683c-36c3-4808-8b8b-fe554cac6b3c.png)


- ### 6 - Space Type
1. [Local](https://docs.unity3d.com/ScriptReference/Space.Self.html) - Applies transformation relative to the parent transform.
2. [World](https://docs.unity3d.com/ScriptReference/Space.World.html) - Applies transformation relative to the world coordinate system.

![image_2023-04-15_10-04-40](https://user-images.githubusercontent.com/15892895/232194744-43c7f7b1-0bab-441b-a4fa-89271eac1cd8.png)


- ### 7 - Animate Type
1. **Override** - Sets `Transform` values to values from curves.
2. **Relative** - Sets `Transform` values relative to initial `Transform` values on moment when called `Play()`. Works on the principle of adding the initial value, with the value from the curve. 

![image_2023-04-15_10-04-52](https://user-images.githubusercontent.com/15892895/232194745-f049a8c3-cb29-435a-b777-6b540282c8f7.png)


- ### 8 - Relative Scale Operation Mode
1. **Plus** - Works on the principle of adding the initial value, with the value from the curve.
2. **Multiply** - Works on the principle of multiply the initial value, with the value from the curve. 

![image_2023-04-15_10-05-35](https://user-images.githubusercontent.com/15892895/232194738-d53cc41e-bd77-42d7-b9fc-d1c40f94d124.png)


- ### 9 - Animation Curves
You can choose which values will be animated. ``AnimationCurve`` is used to animate the value.

![image_2023-04-15_10-05-17](https://user-images.githubusercontent.com/15892895/232194746-69046b6e-dd35-45fd-a6d9-0803c930a51f.png)

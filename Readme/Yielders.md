[![docs badge](https://img.shields.io/badge/docs-reference-blue.svg)](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/README.md)

Сontents:
   - [Notes](Yielders.md#notes)
   - [Use Examples](Yielders.md#use-examples)

# Yielders

- ### Notes
Namespace:
```cs
using Zee.Utils;
```
`Yielders.Get(seconds)` each `WaitForSecond(n)` with unique `n` will be hashed. It will not memory allocate when the same time delay is called again.

- ### Use Examples
```cs
private IEnumerator ExampleCoroutine()
{
    yield return null; // No changes with normal way
}
```
```cs
private IEnumerator ExampleCoroutine()
{
    yield return Yielders.EndOfFrame;
}
```
```cs
private IEnumerator ExampleCoroutine()
{
    yield return Yielders.FixedUpdate;
}
```
```cs
private IEnumerator ExampleCoroutine()
{
    yield return Yielders.Get(4); // In seconds
}
```

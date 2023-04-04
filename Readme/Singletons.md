[![docs badge](https://img.shields.io/badge/docs-reference-blue.svg)](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/README.md)

# Singletons
Сontents:
-  [C# Class Singleton](Singletons.md#c-class)
-  [Monobehavior Singleton](Singletons.md#monobehavior)


## C# class

- How to inherit and use
```cs
using Zee.Singleton;

public class ExampleClass : SingletonClass<ExampleClass>
{
    public void PrintText()
    {
        Debug.Log("Hello World");
    }
}
```
```cs
ExampleClass.Instance.SayHelloWorld();
```

## Monobehavior
- How to inherit and use
```cs
using Zee.Singleton;

public class ExampleClass : SingletonClass<ExampleClass>
{
    public void SayHelloWorld()
    {
        Debug.Log("Hello World");
    }
}
```
```cs
ExampleMono.Instance.SayHelloWorld();
```

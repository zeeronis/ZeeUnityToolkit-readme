[![docs badge](https://img.shields.io/badge/docs-reference-blue.svg)](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/README.md)

# Pool System
Сontents:
-  [Monobehaviors Pool](Pool.md#monobehavior)
   - [How to Inheir](Pool.md#how-to-inheir)
   - [Multiple inheritances](Pool.md#multiple-inheritances)
   - [Instantiate](Pool.md#instantiate)
   - [Return To Pool](Pool.md#return-to-pool)
   - [Pre Create (Code)](Pool.md#pre-create-from-code)
   - [Pre Create (Inspector)](Pool.md#pre-create-from-inspector)
-  [Particle Systems Pool](Pool.md#particlesystem)
   - [Notes](Pool.md#notes)
   - [Instantiate](Pool.md#instantiate-1)
   - [Return To Pool](Pool.md#return-to-pool-1)


## Monobehavior
- ### How to Inheir
To prepare an object, you need to inherit from `PoolableComponent` and must implement two methods.

`OnActivated()` - Called from the pool when an item is activated

`OnDeactivated()` - Will called OnReturnedToPool event, after that gameobject will disabled and returned to pool as child

```cs
using Zee.Pool;

public class Enemy: PoolableComponent<Enemy> 
{
    protected override void OnActivated()
    {
    
    }

    protected override void OnDeactivated()
    {
    
    }
}
```

- ### Multiple inheritances
```cs
using Zee.Pool;

public abstract class ProgressBar<TItem>: PoolableComponent<TItem> 
    where TItem : PoolableComponent<TItem>
{
    // ...
}

public class ProgressBarWithText: ProgressBar<ProgressBarWithText>
{
    // ...
}
```

- ### Instantiate
In simple, u need to use `ItemsPool<T>.Instance.GetItem()` instead `Instantiate()`.

`GetItem()` method have all overloads of `Instantiate()`.
```cs
// Return `GameObject` by prefab reference.
var enemy = ItemsPool<Enemy>.Instance.GetItem(prefabReference, pos, rot);
```
```cs
// Return first added prefab in pool with `Enemy` type
var enemy = ItemsPool<Enemy>.Instance.GetItem(pos, rot);
```
```cs
// Return `GameObject` by added in pool order
var enemy = ItemsPool<Enemy>.Instance.GetItem(addOrderIndex, pos, rot);
```

- ### Return to Pool
In simple, u need to use `UrScriptName.ReturnToPool()` instead `Destroy(gameobject)`.

```cs
// Return Concrete item to pool
var enemy = ItemsPool<Enemy>.Instance.GetItem(pos, rot);
enemy.ReturnToPool();
```
```cs
// Return all items by type back into pool
ItemsPool<Enemy>.Instance.ReturnAllToPool();
```
```cs
// Return all items on all pools back to pools
PoolsMaster.Instance.ReturnAllToPool();
```

- ### Pre-create from code
```cs
ItemsPool<Enemy>.Instance.PreCreateItems(prefabReference, count);
```
- ### Pre-create from inspector
Create `GameObject` on scene and add `PoolsMaster` component; Now u can drag and drop prefabs into list.


## ParticleSystem

- ### Notes 
It is based on checking the lifetime of the root `ParticleSystem`. When the root `ParticleSystem` lifetime expires, it will automatically return to the pool.

Namespace:
```cs
using Zee.Pool; 
```

- ### Instantiate
```cs
// Common way to spawn particle
var transform = RawFXPool.Instance.SpawnParticle(particlePrefab, position, opt:rot);
```
```cs
// Way when it is not known in advance whether there will be any script on the particle system inherited from PoolableComponent  or not.
var transform = RawFXPool.Instance.UniversalSpawnParticle(prefab, pos, rot);
```
- ### Return to Pool
You can't return single active `ParticleSystem` to pool at this moment but u can return all particles.
```cs
RawFXPool.Instance.ReturnAllToPool();
```

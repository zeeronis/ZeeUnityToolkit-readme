# Pool System
Has two pools, for Monobehaviour and Particle Systems.

## Monobehavior
#### 1. The object that will be stored in the pool must have been inherited from `PoolableComponent` and must implement two methods.
```cs
public class Enemy: PoolableComponent<Enemy> 
{
    protected override void OnActivated()
    {
        /// Called from the pool when an item is activated
    }

    protected override void OnDeactivated()
    {
        // Will called OnReturnedToPool event, after that gameobject will disabled and returned to pool as child
    }
}
```

How to use it with abstarctions:
```cs
public abstract class Enemy<TItem>: PoolableComponent<TItem> 
    where TItem : PoolableComponent<TItem>
{
    // ...
}

public class GreatEnemy: Enemy<GreatEnemy>
{
    // ...
}
```

#### 2. Pre-create prefabs instances in the pool in Awakening.

Create `GameObject` on scene and add `PoolsMaster` component; Now u can drag and drop prefabs into list.

Also, u can add prefabs from code: 
```cs
ItemsPool<Enemy>.Instance.PreCreateItems(prefabReference, count);
```

#### 3. Ways to get items from pool.
```cs
/// Return first added prefab in pool with Enemy type
ItemsPool<Enemy>.Instance.GetItem(pos, rot);

/// Return GameObject by added in pool order
ItemsPool<Enemy>.Instance.GetItem(addOrderIndex, pos, rot);

/// Return GameObject by prefab reference. prefab will stored in pool and get the add order
ItemsPool<Enemy>.Instance.GetItem(prefabReference, pos, rot);
```

#### 4. Ways to return items back to pool.
```cs
/// Return Concrete item to pool
var enemy = ItemsPool<Enemy>.Instance.GetItem(pos, rot);
enemy.ReturnToPool();

/// Return all items by type back into pool
ItemsPool<Enemy>.Instance.ReturnAllToPool();

/// Return all items on scene into pools
PoolsMaster.Instance.ReturnAllToPool();
```


## ParticleSystem

#### 1. Ways to return items back to pool.
It is based on checking the lifetime of the root particle system

```cs
// Spawn particle
var transform = RawFXPool.Instance.SpawnParticle(particlePrefab, position, opt:rot);
```

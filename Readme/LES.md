[![docs badge](https://img.shields.io/badge/docs-reference-blue.svg)](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/README.md)

Сontents:
-  [LES Aggregator](LES.md#les-aggregator)
   - [General](LES.md#general)
   - [Settings](LES.md#settings)
   - [Debug](LES.md#debug)
-  [LES Animator](LES.md#les-animator)
   - [...](LES.md#)
-  [LES Coroutine Animation](LES.md#les-coroutine-animation)
   - [...](LES.md#)
-  [LES GObj Activation](LES.md#les-gobj-activation)
   - [...](LES.md#)
-  [LES Particles Pool Spawner](LES.md#les-particles-pool-spawner)
   - [...](LES.md#)
-  [LES Material Property](LES.md#les-material-property)
   - [...](LES.md#)



#  LES Aggregator
The root component required for all other child `LES` components to function. Aggregates events to child components and child `LESAggregators`. 
- ### General
![image_2023-04-30_23-00-58](https://user-images.githubusercontent.com/15892895/235373876-cfe484d9-bbd5-499a-ac28-4757b0c3cce1.png)

1. List of all child `LES` listeners.
2. `Refresh` button - automatically finds all child components and adds them to the list.

- ### Settings
![image_2023-04-30_23-01-56](https://user-images.githubusercontent.com/15892895/235373953-fdf88cff-9520-4a93-b977-19bf8deada36.png)
![image_2023-04-30_23-02-391](https://user-images.githubusercontent.com/15892895/235374517-d5de15ef-95b0-401f-aa99-542d6a9c7a35.png)

1. Automatically causes a subscription for all `LES` components from the list in `Awake` / `OnEnable`
2. Automatically unsubscribes all `LES` components from the list in `OnDestroy` / `OnDisable`
3. Automatically calls `Refresh` on `Awake`. NOT recommended for performance reasons. It is better to press the button manually as the object changes.
4. If `LESAgregattor` is a child of another `LESAgregattor`, determines if it can receive events from it and forward them to self child components.
5. Specifies when it automatically (if enabled) causes a subscription/unsubscription.

- ### Debug
Available only in Play mode.

![image_2023-04-30_23-02-39](https://user-images.githubusercontent.com/15892895/235373958-35e3240a-b3e6-46b4-a318-3b321641cd00.png)

1. As information, shows top `LESAgregattor` of the hierarchy.
2. As information, shows first parent `LESAgregattor` of the hierarchy.
3. Allows you to send events manually.

#  LES Animator


#  LES Coroutine Animation



#  LES GObj Activation


#  LES Particles Pool Spawner


#  LES Material Property


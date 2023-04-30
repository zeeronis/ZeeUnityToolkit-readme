[![docs badge](https://img.shields.io/badge/docs-reference-blue.svg)](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/README.md)

Сontents:
-  [LES Aggregator](LES.md#les-aggregator)
   - [General](LES.md#general)
   - [Settings](LES.md#settings)
   - [Debug](LES.md#debug)
-  [LES Animator](LES.md#les-animator)
-  [LES Coroutine Animation](LES.md#les-coroutine-animation)
-  [LES GObj Activation](LES.md#les-gobj-activation)
-  [LES Particles Pool Spawner](LES.md#les-particles-pool-spawner)
-  [LES Material Property](LES.md#les-material-property)
   - [Events](LES.md#events-4)
   - [Effects](LES.md#effects)
   - [Groups](LES.md#groups)



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
Required `Animator` component. On events received from `LESAgregator`, sets the values in the `Animator`.
- ### Events
![image_2023-04-30_23-30-35](https://user-images.githubusercontent.com/15892895/235374941-e994eb6c-a0d5-453e-ad73-2fac55787a03.png)


#  LES Coroutine Animation
Required [Coroutine Animation](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/Readme/Coroutines.md#coroutine-animation-component) component. On events received from `LESAgregator`, call methods in the [Coroutine Animation](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/Readme/Coroutines.md#coroutine-animation-component).
- ### Events
![image_2023-04-30_23-35-29](https://user-images.githubusercontent.com/15892895/235375116-a7840e58-5f69-4101-b3e7-954ec655004f.png)


#  LES GObj Activation
On events received from `LESAgregator`, activates or deactivates `GameObjects` in the lists.
- ### Events
![image_2023-04-30_23-41-12](https://user-images.githubusercontent.com/15892895/235375319-56bb851b-9448-4129-b9ef-2d950dbef77f.png)


#  LES Particles Pool Spawner
On events received from `LESAgregator`, spawn particles from `prefabs` in target `Transform`. Uses [RawFXPool](https://github.com/zeeronis/ZeeUnityToolkit-readme/blob/main/Readme/Pool.md#particlesystem) for reuse particles.
- ### Events
![image](https://user-images.githubusercontent.com/15892895/235375591-d659543c-260c-4f92-b25f-5ae784d27648.png)

1. Uses selected `Transform` for set position for the spawned particle. By default uses self `Transform`.
2. Reference to any `ParticleSystem` `prefab` from Assets in project.
3. Spawned `ParticleSystem` will be placed as a child of the selected `GameObject`.
4. On - Uses default Unity rescale while drag object from `World` space to child `Transform`. Off - Saves prefab scale, as local scale inside targeted Transform.


#  LES Material Property
On events received from `LESAgregator`, sets the values in the `Shader` whose `Material` it is used in the `Renderer Component`. Allows to animate `Shader` properties via using `Animation Curves`.

- ### Events
![image](https://user-images.githubusercontent.com/15892895/235377250-571bd591-5479-4946-8f74-7af43be1b1de.png)

1. Allows you to use multiple `Effects` per event.
2. Allows you to use multiple `Groups` per effect.
3. `Play01` - Playing full animation, `Set0` - Sets the value from the beginning of the `Animation Curve`, `Set1` - Sets the value from the end of the `Animation Curve`.

- ### Effects
![image](https://user-images.githubusercontent.com/15892895/235376901-6c25d2a3-46ea-4571-ad8c-24364954a253.png)

1. The name of the effect to use in the `Events` tab.
2. The property name in the `Shader`.
3. `Animation Curve` used for animation, where vertical is `Value` and horizontal is `Duration`.

- ### Groups
![image](https://user-images.githubusercontent.com/15892895/235376751-0444bf86-9f15-4a81-8026-f8d051fe3746.png)

1. List of default renderer group.
2. Recursively collect all renderers in childs and add them to the default list.
3. Allows you to set up your own groups.

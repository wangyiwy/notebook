# 控制反转（Inversion of Control）

控制指的是对象的创建、初始化和销毁过程。

控制反转及控制的转移，意思是将控制逻辑由使用一方转移到第三框架或容器负责。当再发生组件变更后，只需要修改框架或容器配置，不需要修改关联组件。

假设组件A调用组件B，不再由A负责创建B对象；而是先由第三方框架或容器负责实例化B对象，然后给A对象注入。（即A对象获取B对象的方式发生了反转。）

控制反转说的是创建对象的关系，而依赖注入是实现的一种手段。

### 优势

本质的好处是解耦，而Spring的依赖注入体现为以下好处：

1. 容易测试，依赖的对象是注入的，因此可以在单元测试时Mock一个对象并注入来测试。
2. 不需要自己实现单例模式，Spring中的Bean默认都是单例模式，单例的作用是减少类实例，从而减少内存占用，并且不用每次使用时都重新实例化，提高效率。
3. 基于依赖注入使得容器可以统一管理Bean以及Bean的生命周期，在Bean的生命周期管理时，可以统一实现一些通用的公共逻辑，而不需要每个Bean单独再实现一遍。 


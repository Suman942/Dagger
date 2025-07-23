# Dagger
🚀 A simple and clean implementation of Dagger for Android. This project demonstrates how to use @Inject, @Module, and @Component to manage dependencies, build scalable architecture, and write testable code.

🟢 1. @Inject = “I need this”
You can use @Inject in two ways:
✅ On a constructor
class Engine @Inject constructor() {
    fun start() = println("Engine started")
}

class Car @Inject constructor(val engine: Engine) {
    fun drive() = engine.start()
}

✅ On a field (variable)
class Car {
    @Inject lateinit var engine: Engine

    fun drive() = engine.start()
}

 🟣 2. @Module
👉 “Here are my instructions for how to build objects.”
A Dagger Module contains functions that tell Dagger how to provide dependencies.
@Module
class EngineModule {

    @Provides
    fun provideEngine(): Engine {
        return Engine()
    }
}

🟣 3. @Provides
👉 “Here’s how to create this object.”
Used inside a Module to provide dependencies that can’t use @Inject on constructor (e.g., 3rd-party libs).
  @Provides
  @Singleton
    fun provideEngine(): Engine {
        return Engine()
    }

🟡 4. @Component
👉 “I’m the bridge between @Inject and @Module.”
A Dagger Component is an interface that tells Dagger what to inject and where.

@Component(modules = [EngineModule::class])
interface CarComponent {
    fun inject(car: Car)
}


Scope Annotation:-
@Singleton  // single instance in whole app lifecycle
@Custom scope // for activity or fragment - single instance till the lifecycle of that particular fragment or activity


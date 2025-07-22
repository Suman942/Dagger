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

 

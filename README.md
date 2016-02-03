# SCApplication
A 2d graphics engine that also acts as an abstraction layer for SDL2


##Benefits
- Entity-ish system
- Modular logic and rendering for each entity
- Smart loop logic (not tied to framerate)


##How to Start an Application
Starting an `Application` window is an easy process:

```C++
  Application app;
  app.init();
  
  app.loop();
```

Once an Application has been defined, it must be initialized by calling `Application::init()` (this returns an `int`, which could change to a `bool` in the future). Next `Application::loop()` is called to start the `Application`, but `Application::loop()` will only run if `Application::init()` was successful. The success of `Application::init()` can be determined by its return value as follows:

```C++
if(app.init()){
  app.loop()
}
```

So `app.loop` will only run if the setup process in `app.init()` was successful.

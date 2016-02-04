# SCApplication
A 2d graphics engine that also acts as an abstraction layer for SDL2


##Benefits
- Entity-ish system
- Modular logic and rendering for each entity
- Smart loop logic (not tied to framerate)


#How-To

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

So `app.loop()` will only run if the setup process in `app.init()` was successful.


##How to Use an ApplicationObject
In SCApplication, `ApplicationObject`s act as entities. They have their own modular rendering and logic objects that handle all the interaction with the application's environment. To create an `ApplicationObject`, do the following:

```C++
SDL_Rect ao_rect;
ObjectRenderer ao_renderer(app.getRenderer());
ObjectLogic ao_logic(&app, &ao_rect);
ApplicationObject ao_obj(&app, &ao_renderer, &ao_logic);
```

While the code required for creating an `ApplicationObject` appears large, doing so with pure SDL2 is an even greater task. However, there are plans to replace the above declarations for `ObjectRenderer` and `ObjectLogic` with a `ModuleManager`, which will then be added to the `ApplicationObject` and be responsible for swaping modules when needed.

After an ApplicationObject is constructed, it must be added into the application:

```C++
app.add(&ao_obj);
```

At this point, the `ApplicationObject` is now in the application; the logic and rendering are now being executed. 

#Future Plans
- Make creation of `ApplicationObject` easier (`ModuleManager`?)
- Improve access of `ApplicationObject` in the application (Some form of naming system?)

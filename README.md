This is not *cheat*  JUST UI
To render anything you need to call original __SDL_GL_SwapWindow__ before you actually call __SDL_GL_MakeCurrent__ (with original context as one of the arguments).  

Moreover, you need to call __glFlush()__ in the bottom of your __SDL_GL_SwapWindow__ override function to get rid of flickering effect.  
![image](https://user-images.githubusercontent.com/100489392/157216123-1d443c52-8262-4dad-96d7-4499823c1682.png)

## How it works
Check out the Wiki's About the IMGUI paradigm section if you want to understand the core principles behind the IMGUI paradigm. An IMGUI tries to minimize superfluous state duplication, state synchronization and state retention from the user's point of view. It is less error prone (less code and less bugs) than traditional retained-mode interfaces, and lends itself to create dynamic user interfaces.

Dear ImGui outputs vertex buffers and command lists that you can easily render in your application. The number of draw calls and state changes required to render them is fairly small. Because Dear ImGui doesn't know or touch graphics state directly, you can call its functions anywhere in your code (e.g. in the middle of a running algorithm, or in the middle of your own rendering process). Refer to the sample applications in the examples/ folder for instructions on how to integrate Dear ImGui with your existing codebase.

A common misunderstanding is to mistake immediate mode gui for immediate mode rendering, which usually implies hammering your driver/GPU with a bunch of inefficient draw calls and state changes as the gui functions are called. This is NOT what Dear ImGui does. Dear ImGui outputs vertex buffers and a small list of draw calls batches. It never touches your GPU directly. The draw call batches are decently optimal and you can render them later, in your app or even remotely.

## Integration
On most platforms and when using C++, you should be able to use a combination of the imgui_impl_xxxx backends without modification (e.g. imgui_impl_win32.cpp + imgui_impl_dx11.cpp). If your engine supports multiple platforms, consider using more of the imgui_impl_xxxx files instead of rewriting them: this will be less work for you and you can get Dear ImGui running immediately. You can later decide to rewrite a custom backend using your custom engine functions if you wish so.

Integrating Dear ImGui within your custom engine is a matter of 1) wiring mouse/keyboard/gamepad inputs 2) uploading one texture to your GPU/render engine 3) providing a render function that can bind textures and render textured triangles. The examples/ folder is populated with applications doing just that. If you are an experienced programmer at ease with those concepts, it should take you less than two hours to integrate Dear ImGui in your custom engine. Make sure to spend time reading the FAQ, comments, and some of the examples/ application!

Officially maintained backends/bindings (in repository):

Renderers: DirectX9, DirectX10, DirectX11, DirectX12, Metal, OpenGL/ES/ES2, SDL_Renderer, Vulkan, WebGPU.
Platforms: GLFW, SDL2, Win32, Glut, OSX, Android.
Frameworks: Allegro5, Emscripten.
Third-party backends/bindings wiki page:

Languages: C, C# and: Beef, ChaiScript, Crystal, D, Go, Haskell, Haxe/hxcpp, Java, JavaScript, Julia, Kotlin, Lobster, Lua, Odin, Pascal, PureBasic, Python, Ruby, Rust, Swift...
Frameworks: AGS/Adventure Game Studio, Amethyst, Blender, bsf, Cinder, Cocos2d-x, Diligent Engine, Flexium, GML/Game Maker Studio2, GLEQ, Godot, GTK3+OpenGL3, Irrlicht Engine, LÖVE+LUA, Magnum, Monogame, NanoRT, nCine, Nim Game Lib, Nintendo 3DS & Switch (homebrew), Ogre, openFrameworks, OSG/OpenSceneGraph, Orx, Photoshop, px_render, Qt/QtDirect3D, SDL_Renderer, SFML, Sokol, Unity, Unreal Engine 4, vtk, VulkanHpp, VulkanSceneGraph, Win32 GDI, WxWidgets.
Note that C bindings (cimgui) are auto-generated, you can use its json/lua output to generate bindings for other languages.

### Usage
1) Install *SDL2* library with [Homebrew](https://brew.sh/).  
```bash
brew install sdl2
```
2) Open project in XCode.  
3) Build the project.
4) Inject the lib. (for example with [osxinj](https://github.com/scen/oxinj)) 



## Disclaimer
[This program](https://github.com/NotSlater/External-Cheat-Menu-Example) is for educational purposes only!

Copyright Disclaimer under section 107 of the Copyright Act 1976, allowance is made for “fair use” for purposes such as criticism, comment, news reporting, teaching, scholarship, education and research.


![image](https://user-images.githubusercontent.com/100489392/157216195-43835192-0b43-4121-a124-55a98eaf9d3f.png)

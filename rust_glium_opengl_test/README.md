# Rust + Glium test

## about this repository

Playing with OpenGL in Rustlang.

The initial code is based on [Glium examples](https://github.com/tomaka/glium/blob/master/examples/instancing.rs).

An object is loaded from *.obj* file and displayed, while its position is being changed each frame. 
Changes are computed according to gravity interactions between all objects pairs - this can be computed 
on CPU, but there is also GLSL compute shader based GPU version. 
I had some experience with OpenCL but I decided to try compute shaders this time, 
they have better OpenGL interop after all and I don't need all those OpenCL fancy features in this project.
 

## building and running

Run in terminal:

```bash
cargo build --release
cargo run --release
```

Building phase (first build is slow, but rebuild is many times faster):

![screen0](https://raw.githubusercontent.com/michal2229/Rust-playground/master/rust_glium_opengl_test/results/screen0.png)

Running phase (two object clusters orbiting each other + interaction of objects inside clusters):

![screen1](https://raw.githubusercontent.com/michal2229/Rust-playground/master/rust_glium_opengl_test/results/screen1.png)

Not much to see so far. Hopefully I will have the time to do something interesting with it.

Update1: looks somewhat better now with spheres :) But still much to do (camera controls, perspective, some interaction...).

![screen2](https://raw.githubusercontent.com/michal2229/Rust-playground/master/rust_glium_opengl_test/results/screen2.png)

Update2: camera perspective and basic controls done (WS/AD/QE), no rotation so far. 

![screen3](https://raw.githubusercontent.com/michal2229/Rust-playground/master/rust_glium_opengl_test/results/screen3.png)

Update3: some performance and visual tweaks. 

![screen4](https://raw.githubusercontent.com/michal2229/Rust-playground/master/rust_glium_opengl_test/results/screen4.png)

Update4: better, larger buffers, more particles (max 16k). 

![screen5](https://raw.githubusercontent.com/michal2229/Rust-playground/master/rust_glium_opengl_test/results/screen5.png)

![screen6](https://raw.githubusercontent.com/michal2229/Rust-playground/master/rust_glium_opengl_test/results/screen6.png)


## about [Glium](https://github.com/tomaka/glium)

Elegant and safe OpenGL wrapper.

Glium is an intermediate layer between OpenGL and your application. 
You still need to manually handle the graphics pipeline, 
but without having to use OpenGL's old and error-prone API.

Its objectives:

* Be safe to use. Many aspects of OpenGL that can trigger a crash if misused are automatically handled by glium.
* Provide an API that enforces good practices such as RAII or stateless function calls.
* Be compatible with all OpenGL versions that support shaders, providing a unified API when things diverge.
* Avoid all OpenGL errors beforehand.
* Produce optimized OpenGL function calls, and allow the user to easily use modern OpenGL techniques.

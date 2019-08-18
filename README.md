# Minor alteration of the [Vulkano Mandelbrot example](https://github.com/vulkano-rs/vulkano-www/blob/master/examples/guide-mandelbrot.rs) to demonstrate an issue

The `vulkano_shaders::shader!` macro currently does not behave as expected with the `path` parameter. Changes to the file at `path` will not be incoporated until something forces a rebuild of the file containing the shader macro (a clean build, or a change to that file).

## Reproduction steps
1. Run the repo as is
1. Observe the `image.png` output (should be a white square)
1. Remove the `vec4(1.0)` and uncomment the code after it in `shader.glsl`.
1. `cargo run` without cleaning or modifying main.rs
1. Observe `image.png` (unchanged)
1. Change `main.rs` somehow (println!, etc.)
1. Run again
1. `image.png` should be the expected Mandelbrot visualization.

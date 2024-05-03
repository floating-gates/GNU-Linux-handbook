# Cross compilation

Cross compilation is the process of building a program on one architecture (the host) to be run on 
different one, namely, the target. It can be useful when the target platform does not have the necessary
tools or resources to build the code base.

To perform a cross compilation, you will need a cross-compiler, which is a toolchain that includes a 
compiler, linker, and other tools that are specific to the target platform. You will also need to set 
up the build system to use the cross-compiler and  specify the target platform. 

## C cross compilation tools 

The installation of the necessary tools for C to cross compile from an x86_64 machine to an aarch64 
(ARM) architecture are listed:

```sh
sudo apt install gcc make gcc-aarch64-linux-gnu binutils-aarch64-linux-gnu
```

## Rust cross compilation tools

A crate is devoted to provide cross-compilation capabilities namely ```cross```

```sh
# Start the Docker daemon, if it's not already running using systemd
sudo systemctl start docker

cross build --target aarch64-unknown-linux-gnu

cross test --target mips64-unknown-linux-gnuabi64

cross rustc --target powerpc-unknown-linux-gnu --release -- -C lto
```

<!--  Script to show the footer   -->
<html>
<script
    src="https://code.jquery.com/jquery-3.3.1.js"
    integrity="sha256-2Kok7MbOyxpgUVvAk/HJ2jigOSYS2auK4Pfzbm7uH60="
    crossorigin="anonymous">
</script>
<script>
$(function(){
  $("#footer").load("../footers/footer.html");
});
</script>
<body>
<div id="footer"></div>
</body>
</html>

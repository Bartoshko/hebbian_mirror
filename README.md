# Hebbian Mirror:

Low level http service for image recognition. Written in Rust with CUDA support.

<p align="center">
    <img 
    width="50%" height="50%" 
    src="https://github.com/Bartoshko/hebbian_mirror/blob/master/assets/mirror.jpeg"/>
</p>

## Dependencies:

This software requires:

- Rust nightly: rustc 1.40.0-nightly, cargo 1.40.0-nightly, rustup 1.20.2
- [Rocket](https://rocket.rs/)
- [tch](https://docs.rs/tch/0.1.1/tch/)
- [openssl](https://github.com/openssl/openssl)
- [Docker](https://www.docker.com/)
- and more (please see Cargo.toml)

- please if building for IoT use proper compilation settings or build on device.
- this software uses layer of virtualization only for development and QA process, which will effect running performance. Use docker 3.0 or greater,
- For AWS lambda integration I am going to create .env file instruction that will allow to build project on the go and be used with your AWS tools (but this is going to happened in near future)
- please compile with `IS_CUDA = false` first, check if your hardware is capable of CUDA

## Deep Learning assets:

- Download weights ```$ wget -c https://github.com/LaurentMazare/ocaml-torch/releases/download/v0.1-unstable/yolo-v3.ot ```

## Build for development:

- cargo: ```$ RUST_LOG=info ROCKET_ENV=development cargo run```
- docker: ```docker-compose up```

## Build for production

- ```$ RUST_LOG=error ROCKET_ENV=production cargo run```

or 

- - ```$ cargo build --release``` 
then
```chmod +x ./target/release/hebbian_mirror```
then
```$ RUST_LOG=error ROCKET_ENV=production ./target/release/hebbian_mirror```

## Authors and Contributors:

- Lenart Bartosz
- [Claire Amalfitano](https://github.com/polypodioides)
- [Janusz Roll](https://github.com/janeek1995)

## License:

- [MIT](https://opensource.org/licenses/MIT)

## Rules (one rule only)

- [Have a good reason for developing this service](https://www.youtube.com/watch?v=CZB7wlYbknM)

## How AI (yolo.v3) works:

#### YOLO v3 (you only look once) architecture

<p align="center">
    <img 
    width="100%" height="100%" 
    src="https://github.com/Bartoshko/hebbian_mirror/blob/master/assets/yolo_architecture.png"/>
</p>

#### Predictions map (boxes)

<p align="center">
    <img 
    width="100%" height="100%" 
    src="https://github.com/Bartoshko/hebbian_mirror/blob/master/assets/boxes.png"/>
</p>

#### Loss function calculation

<p align="center">
    <img 
    width="100%" height="100%" 
    src="https://github.com/Bartoshko/hebbian_mirror/blob/master/assets/loss_function_changes.png"/>
</p>

### Knowledge resources:

Very good explanation from [Ayoosh Kathuria](https://towardsdatascience.com/yolo-v3-object-detection-53fb7d3bfe6b)

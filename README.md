# Microbit V2 Project Template

A plain template to tinker with [Rust Embedded Discovery Book](https://docs.rust-embedded.org/discovery/microbit/index.html) on the Microbit V2 board.

## Setup

- Install [rustup.rs - The Rust toolchain installer](https://rustup.rs/)
- Install the chip's architecture toolchain `rustup target add thumbv7em-none-eabihf`
- Install wrappers around LLVM tools `rustup component add llvm-tools` and `cargo install cargo-binutils`
- Install [probe-rs](https://probe.rs/docs/getting-started/installation/)

## Run

Use `cargo run` or `cargo embed` to run the program.

## References

- [Microbit Hardware Spec](https://tech.microbit.org/hardware/)
- [Template to develop bare metal applications for Cortex-M microcontrollers](https://github.com/rust-embedded/cortex-m-quickstart/tree/master)
- [Embedded Rust setup explained - YouTube | The Rusty Bits](https://www.youtube.com/watch?v=TOAynddiu5M)

## Notes

`cortex-m-rt` requires the `memory.x` file which specifies the target memory layout. To get it:

- Check [Microbit Hardware Spec](https://tech.microbit.org/hardware/)
- There's an MCU's data sheet link in the `More Details` section.
- Go to [nRF52 datasheet](https://infocenter.nordicsemi.com/index.jsp?topic=%2Fstruct_nrf52%2Fstruct%2Fnrf52833.html&cp=3_1)
- In the data sheet, find `4.2.3 Memory map`

`probe-rs` requires the chip name. To figure it out:

- Check [Microbit Hardware Spec](https://tech.microbit.org/hardware/)
- The board's MCU name is `nRF52833`
- Find the corresponding name in `probe-rs chip list | grep nRF52833`

An empty `main` function might fail to build with something `rust-lld: error: undefined symbol: _critical_section_1_0_release`. Use the `microbit` crate in the code to make it link to the binary.

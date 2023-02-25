# NYMCAT - Nymsphinx Packet Crafting Machine

## Overview

This project provides a command-line interface for crafting Sphinx packets using the Nymsphinx Rust crate. It allows users to enter a message and a recipient, and can optionally modify the packet routing by changing the destination port.

The packet crafting logic is implemented in the `src/lib.rs` file, and the CLI interface is implemented in the `src/cli.rs` file.

## Usage

To use the Nymsphinx Packet Crafting Machine, you will need to have Rust installed on your machine. Once you have Rust installed, you can follow these steps:

1. Clone the repository and navigate to the project directory.
2. Run `cargo build` to build the project.
3. Run `cargo run` to start the CLI.

When the CLI starts, it will prompt you to enter a message and a recipient. You can optionally choose to modify the packet routing by changing the destination port. The CLI will then craft a Sphinx packet and print it to the console.

## Nymsphinx

[Sphinx](https://www.cypherpunks.ca/~iang/pubs/Sphinx_Oakland09.pdf) is a protocol for anonymous communication that uses layered encryption to hide the identity of both the sender and the receiver. Sphinx packets are used to transmit messages between nodes in the network.

The Nymsphinx Rust crate provides a collection of types and functions for working with Sphinx packets in Rust. It includes types for representing Sphinx headers, payloads, and routing information, as well as functions for encoding and decoding Sphinx packets.

### Packet Structure

A Sphinx packet consists of four parts:

1. The header, which contains information about the packet's size, version, and mode.
2. The routing information, which is used to route the packet through the network.
3. The Sphinx payload, which contains the encrypted message and any associated metadata.
4. The padding, which is used to obscure the size of the packet.

The `FramedSphinxPacket` type in the Nymsphinx crate represents a Sphinx packet with additional routing information. This type includes a custom routing field in the payload that can be used to route the packet to a specific destination. 

### Hidden Services

Sphinx can be used to implement hidden services, similar to the Tor network. In a Sphinx-based hidden service, clients encrypt their messages using a one-time public key provided by the service, and route them through the network to the service's endpoint. The service decrypts the messages and responds using the same route.

To create a Sphinx-based hidden service, the service provider generates a public/private key pair, and publishes the public key as the endpoint address. Clients encrypt their messages using the public key, and route them through the network to the endpoint. The service provider decrypts the messages using the private key, and responds using the same route.

## Implementation Details

The Nymsphinx Packet Crafting Machine is implemented using Rust and the Nymsphinx crate. The project is organized as a Rust library, with a separate CLI binary that uses the library to craft Sphinx packets.

The packet crafting logic is implemented in the `src/lib.rs` file. This file defines a `create_packet` function that takes a message and a recipient as input, and returns a Sphinx packet that is ready to be sent over the network. The function can optionally modify the packet routing by changing the destination port.

The CLI interface is implemented in the `src/cli.rs` file. This file defines a `run` function that prompts the user for input, calls the `create_packet` function to craft a Sphinx packet, and prints the resulting packet to the console.

## Conclusion

The Nymsphinx Packet Crafting Machine provides a simple way to craft Sphinx packets using Rust and the

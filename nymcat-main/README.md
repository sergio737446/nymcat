# NYMCAT -
# The ultimate Nymsphinx Packet Crafting Machine

## Overview

This project provides a command-line interface for crafting Sphinx packets using the Nymsphinx Rust crate. It allows users to enter a message and a recipient, and can optionally modify the packet routing by changing the destination port. This is a PoC for future frameworks to build private blockchains, hidden services and whatever you want so no one can see what is talking to what. 


The packet crafting logic is implemented in the `src/lib.rs` file, and the CLI interface is implemented in the `src/cli.rs` file.

### **DISCLAIMER**: 
**I, AS A NATURAL PERSON, HAVE NO RESPONSIBILITY FOR ANY MISUSE OF THIS SOFTWARE, ANY DAMAGES TO ANYONES MACHINE BECAUSE OF THE SOFTWARE OR BREAKING OTHER 3RD PARTY SOFTWARE. THIS IS AN EXPERIMENT OF GUIDING AI TO SEE IF IT CAN DO SOME RUST! CODE WILL FOLLOW IF I CAN GET SOME VOLUNTEERS, FUNDING ... THE PACKET BUILDER HOWEVER WORKS AND BUILDS A CUSTOM SPHINX PACKET ACCORDING TO THE LATEST NYMSPHINX**

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


### Crafting a Sphinx Packet

The Nymsphinx packet crafting machine provides a simple interface for creating Sphinx packets with custom routing information. Here's how it works:

- Collect user input: The src/main.rs file contains a command line interface that prompts the user for the message to send, the recipient's address, and whether to use custom routing information.
- Build the Sphinx packet: The src/lib.rs file contains functions for creating the Sphinx packet header, routing information, and payload. If custom routing information is selected, the routing information is created using the provided parameters. Otherwise, the default routing information is used.
- Encode the Sphinx packet: The SphinxPacket struct provided by the nym_sphinx crate is used to store the Sphinx packet. The FramedSphinxPacket struct, provided by the nym_packet crate, is used to add the custom routing information to the Sphinx packet. The Sphinx packet is then encoded into a byte array using the SphinxPacket::try_from and FramedSphinxPacket::encode functions.
- Send the Sphinx packet: The encoded Sphinx packet can then be sent over a network or stored for later use.

### Hidden Services

Creating a Hidden Service

In addition to providing anonymous communication, Sphinx packets can also be used to create hidden services. A hidden service is a network service that can only be accessed by clients that know the service's address. In the case of Sphinx, the address of a hidden service is the destination address of a Sphinx packet with a custom routing path.

To create a hidden service using NymCat, the following steps are required:

1. Create a public key: The hidden service provider generates a public/private key pair.
2. ompute the address: The address of the hidden service is computed by hashing the public key and truncating the result to the desired length. This address is the destination address of Sphinx packets sent to the hidden service.
3. Create the routing path: To create the routing path for the Sphinx packet, the hidden service provider selects a set of nodes to act as relays for the Sphinx
4. Sphinx can be used to implement hidden services, similar to the Tor network. In a Sphinx-based hidden service, clients encrypt their messages using a one-time public key provided by the service, and route them through the network to the service's endpoint. The service decrypts the messages and responds using the same route.

#### TL;DR
To create a Sphinx-based hidden service, the service provider generates a public/private key pair, and publishes the public key as the endpoint address. Clients encrypt their messages using the public key, and route them through the network to the endpoint. The service provider decrypts the messages using the private key, and responds using the same route.

## Implementation Details

The Nymsphinx Packet Crafting Machine is implemented using Rust and the Nymsphinx crate. The project is organized as a Rust library, with a separate CLI binary that uses the library to craft Sphinx packets.

The packet crafting logic is implemented in the `src/lib.rs` file. This file defines a `create_packet` function that takes a message and a recipient as input, and returns a Sphinx packet that is ready to be sent over the network. The function can optionally modify the packet routing by changing the destination port.

The CLI interface is implemented in the `src/cli.rs` file. This file defines a `run` function that prompts the user for input, calls the `create_packet` function to craft a Sphinx packet, and prints the resulting packet to the console.

## Conclusion

This is a HIGHLY THEORETHICAL PoC which might be a complete bullshit. My cat helped me wrote this README and PoC code to see if this PoC even remotely works will come someday. Take this as a food for thought. I believe Nymcat is possible to do anything over Nym Mixnet. 

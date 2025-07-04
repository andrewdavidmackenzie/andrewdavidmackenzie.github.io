---
layout: page
---

Welcome to my home page. Here you can find:

## Pigg - GUI and CLI Remote control of Raspberry Pi GPIO
A project I started and maintain that provides a GUI for remote control of the GPIO hardware of
Raspberry Pi devices, both Pi and Pico's, over USB, Wi-Fi and the Internet (via Iroh).
  * [Pigg Site](/pigg)
  * [GitHub repo](https://github.com/andrewdavidmackenzie/pigg)

## Blog
* [Blog](/blog) - mostly about programming, but also has some random personal stuff

## libproc-rs
* For some strange reason I decided to tinker with rust bindings to the Mac OS X library "libproc" that is used to 
  get information about running processes in macOS/darwin. I published it as `libproc-rs` and a number of others 
  started using it and I have got a number of external contributions to it (to the extent I hardly recognize it!) 
    * [GitHub repo](https://github.com/andrewdavidmackenzie/libproc-rs)
    * [Crate published on crates.io](https://crates.io/crates/libproc)
    * [docs.rs for libproc-rs](https://docs.rs/libproc/0.14.1/libproc/)

## Flow project
Flow is my project where I explore the paradigm of dataflow driven programming, written in rust. 
Here you can find:
* [The flow book](http://andrewdavidmackenzie.github.io/flow/book/book_intro.html) describing the project and how to use it.
* [flow](https://github.com/andrewdavidmackenzie/flow/) source code repo on GitHub, plus the
  [GitHub kanban project](https://github.com/andrewdavidmackenzie/flow/projects/2) I use to manage work on it
  
## Chromecast utilities and games
* Pongcast - my clone of the classic "Pong" game for the Chromecast to allow you to play Pong on your Big Screen TV!
    * If you want to, you can find the [Android app on the Google Play Store](https://play.google.com/store/apps/details?id=net.mackenzie.pongcast)
    * The "receiver" part of the Chromecast app can be used as a [browser based, keyboard controlled, version of the game](http://andrewdavidmackenzie.github.io/pongcast)
    * The [source code repo](https://github.com/andrewdavidmackenzie/pongcast) on GitHub
  
[comment]: <> (* TestCast &#40;[Android App on PlayStore]&#40;https://play.google.com/store/sapps/details?id=net.mackenzie.testcast&#41; and [receiver app]&#40;https://github.com/andrewdavidmackenzie/testcast&#41;&#41;)

[comment]: <> (* SnakeCast &#40;[Android App on PlayStore]&#40;https://play.google.com/store/search?q=snakecast&#41; and [receiver app]&#40;https://github.com/andrewdavidmackenzie/snakecast&#41;&#41;)

## Pingr project
A fun project to learn a bunch of stuff (almost all in rust):
* Cloudflare DurableObjects that tracks wi-fi devices via reports sent from devices (see below) and enqueues state 
  changes into a Cloudflare Queue
* Cloudflare worker (written in rust using workers-rs crate, deployed in WebAssembly) that pulls device state 
  changes from a Queue and updates device and connection states in the KV store (blow)
* Cloudflare Key-Value store that stores data for the worker, and from the UI
* Cloudflare Pages projects, including Functions. Building a website deployed to Pages as a SPA, using Leptos rust
  web framework, that reads and writes data to/from the KV store using Functions
* Writing a cross-platform (macOS, linux, windows, RaspberryPi OS for Pi4, Pi400, and Pi Zero W) wi-fi monitoring 
  program that reports to worker via API
* Writing an embedded wi-fi monitor in rust using embassy on Pi Pico W that reports to worker via API

The UI for setting up wi-ifi monitoring and tracking status is at [Pingr Home Page](https://pingr.mackenzie-serres.net)

If interested, you can view the [Source Code](https://github.com/andrewdavidmackenzie/pingr)
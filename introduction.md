# Introduction

Deno ([/ˈdiːnoʊ/](http://ipa-reader.xyz/?text=%CB%88di%CB%90no%CA%8A),
pronounced `dee-no`) is a JavaScript, TypeScript, and WebAssembly runtime with
secure defaults and a great developer experience.

It's built on V8, Rust, and Tokio.

## Feature highlights

- Provides [web platform functionality](./runtime/web_platform_apis.md) and
  adopts web platform standards. For example using ES modules, web workers, and
  support `fetch()`.
- Secure by default. No file, network, or environment access unless explicitly
  enabled.
- Supports [TypeScript](./advanced/typescript.md) out of the box.
- Ships a single executable (`deno`).
- Provides built-in [development tooling](./tools.md) like a code formatter
  ([`deno fmt`](./tools/formatter.md)), a linter
  ([`deno lint`](./tools/linter.md)), a test runner
  ([`deno test`](./basics/testing.md)), and a
  [language server for your editor](./getting_started/setup_your_environment.md#using-an-editoride).
- Has
  [a set of reviewed (audited) standard modules](https://deno.land/std@$STD_VERSION)
  that are guaranteed to work with Deno.
- Supports the use of [existing npm modules](./node.md)

## Philosophy

Deno aims to be a productive and secure scripting environment for the modern
programmer.

Deno will always be distributed as a single executable. Given a URL to a Deno
program, it is runnable with nothing more than
[the ~31 megabyte zipped executable](https://github.com/denoland/deno/releases).
Deno explicitly takes on the role of both runtime and package manager. It uses a
standard browser-compatible protocol for loading modules: URLs.

Among other things, Deno is a great replacement for utility scripts that may
have been historically written with Bash or Python.

## Goals

- Ship as just a single executable (`deno`).
- Provide secure defaults.
  - Unless specifically allowed, scripts can't access files, the environment, or
    the network.
- Be browser-compatible.
  - The subset of Deno programs which are written completely in JavaScript and
    do not use the global `Deno` namespace (or feature test for it), ought to
    also be able to be run in a modern web browser without change.
- Provide built-in tooling to improve developer experience.
  - E.g. unit testing, code formatting, and linting.
- Keep V8 concepts out of user land.
- Serve HTTP efficiently.

## Other key behaviors

- Fetch and cache remote code upon first execution, and never update it until
  the code is run with the `--reload` flag. (So, this will still work on an
  airplane.)
- Modules/files loaded from remote URLs are intended to be immutable and
  cacheable.

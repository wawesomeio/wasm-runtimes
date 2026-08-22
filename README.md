# wasm-runtimes

Precompiled JavaScript engine assets for the wawesome platform. Every
release here is cut by the `Publish Engine Assets` workflow in
`wawesomeio/wawesome-monorepo`; nothing is built by hand.

One release per `(runtime, runtime version, Wasmtime version)`, tagged
like `starling-0.3.0-wasmtime-47.0.2`, carrying the upstream engine
module, one `.cwasm` per target triple, and a `SHA256SUMS` over the set.

A `.cwasm` is Cranelift output bound to its target triple and to the
Wasmtime version that produced it, which is why the tag names all three:
a Wasmtime bump cuts a new tag rather than replacing assets under an old
one, so a commit that pins Wasmtime 47 keeps fetching artifacts built by
Wasmtime 47 forever.

These are public because the consumer has no credentials — the gateway
image is built on a host with no GitHub PAT, and a release asset on a
private repository is an API call carrying a bearer token rather than a
URL. What is published is an unmodified upstream artifact from
`bytecodealliance/StarlingMonkey` and ahead-of-time compilations of it.

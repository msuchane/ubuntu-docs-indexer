# Ubuntu documentation indexer

A tool that parses official Ubuntu documentation into a LanceDB vector database.

This is a helper program for [`ask-ubuntu-docs`](https://github.com/canonical/ask-ubuntu-docs/). It parses the official Ubuntu documentation specified in the `docs.toml` file using a local embedding model (BGE-small) and generates a LanceDB vector database. It compresses the database into the `target/index.lance.tar.gz` file. When you tag a new release of this program and upload `index.lance.tar.gz` as an artifact, `ask-ubuntu-docs` is able to download the archive at build-time and bundle it for its documentation queries.


## Build the program

1. Install the Rust toolchain:

    ```bash
    sudo snap install rustup --classic
    rustup toolchain install stable
    ```

2. Compile the program in release mode (faster docs processing):

    ```bash
    cargo build --release
    ```


## Run the program

1. Run the recently built program:

    ```bash
    cargo run --release
    ```

2. Take the `target/index.lance.tar.gz` archive and upload it as a release artifact.

    Alternatively, take the `target/index.lance` directory and use it with a local build of `ask-ubuntu-docs`.

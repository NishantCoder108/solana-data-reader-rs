# Read Solana Blockchain via API Calls

### What I Learned

- This section includes all my learnings about reading data using APIs in Rust.
- The first two lines define the workspace. This is neither a library (`lib`) nor a binary by default.

- We can structure the application by creating an API package. Use `cargo new api` — this creates an `api` directory with a `main.rs` file inside.

- `cargo new api` sets up a binary project by default, meaning it includes a `main.rs` file instead of a library.

---

### Steps:

1. Initialize a new Rust project (Turborepo-style setup).
2. Add a workspace configuration, similar to a monorepo in TypeScript.
3. Run `cargo new api` — this creates a proper folder structure with a dedicated `api` directory.
4. Build a Rust application that exposes an endpoint:
   - Use the `poem` framework, similar to Express in Node.js.
   - Run: `cargo add poem tokio`
   - `poem` is used for building the HTTP server, and `tokio` handles async/await.

   ```bash
   # Add this to the root-level Cargo.toml
   members = [
     "api",
   ]


  * Then run: `cargo add poem tokio -p api` to add dependencies to the `api` package.
  * For full Tokio features, add this to `api/Cargo.toml`:

  ```toml
  tokio = { version = "1.45.1", features = ["full"] }
  ```

5. For JSON serialization/deserialization, use `serde` and `serde_json`
   (Ref: [https://github.com/serde-rs/json](https://github.com/serde-rs/json))

   ```toml
   serde = { version = "1.0.219", features = ["derive"] }
   ```

6. Add important dependencies to the `api` package:

   * Use: `cargo add solana-client solana-sdk`

7. Write Rust code to fetch the wallet balance from the Solana blockchain.

---

### Routes:

```rust
let app = Route::new()
    .at("/hello/:name", get(hello))
    .at("/yourname/:name", get(your_name))
    .at("/health", get(health))
    .at("/", get(home))
    // Blockchain routes
    .at("/balance/:addr", get(balance))
    .at("/tx_history/:addr", get(tx_history));
```

---

### Run:

* Run the project:

  ```bash
  cargo run
  ```
* The server will start on `localhost:3000`, and you can test the API endpoints.



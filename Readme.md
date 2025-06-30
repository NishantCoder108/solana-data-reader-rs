# Read Solana Blockchain by API calls


### What I Learned

-  Here we write all the learning things about creating better up time
- Just above two lines for define workspace , not lib and not is binary 

- We can structure my application , for creating api for their package , we can run `cargo new api` , it will create a directory api and inside it will have a main.rs file

- `cargo new api` will create a directory api and inside it will have a main.rs file and this is binary project




### Steps :
1. Initialize a new Rust project (Turborepo initialize)
2. Add Workspace like monorepo project in ts
3. `cargo new api` , It will create a directory for right folder structure
4. Create a rust application that expose one end point  
   - We can use `poem` framework for end point expose like express in nodejs
   - `cargo add poem tokio`
   - `poem` is for http server and `tokio` is for async and await
   - ```bash
     members = [
     "api",
     ]
     ```
     - After adding above code inside `Cargo.toml` file in root directory and then we can run 
     - `cargo add poem tokio -p api`
     - It will install dependencies for api package
     - `tokio = { version = "1.45.1", features = ["full"] }`
     - Add above code inside `api/Cargo.toml` file for full tokio feature

5. For serialization and deserialization we can use `serde` and `serde_json` for json serialization and deserialization (https://github.com/serde-rs/json)
    - For serialization and deserialization `serde = { version = "1.0.219", features = ["derive"] }
`

6. Add important dependencies for api package
    - For `solana-client` and `solana-sdk` we can use `cargo add solana-client solana-sdk`
7. Write code for fetch balance from solana blockchain


#### Routes:
```rust

let app = Route::new()
        .at("/hello/:name", get(hello))
        .at("/yourname/:name", get(your_name))
        .at("/health", get(health))
        .at("/", get(home))
        // Adding a route for blockchain balance
        .at("/balance/:addr", get(balance))
        .at("/tx_history/:addr", get(tx_history));


```


#### RUN :
- `cargo run` : It will run on localhost:3000 and we can test api 

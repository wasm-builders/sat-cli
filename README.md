# sat-cli


> Create 2 Rust Runnables
```
subo create runnable hello
subo create runnable morgen
```

> Change the source code of each of them

```rust
impl Runnable for Hello {
    fn run(&self, input: Vec<u8>) -> Result<Vec<u8>, RunErr> {
        let in_string = String::from_utf8(input).unwrap();
    
        Ok(String::from(format!("👋 Hello world {} 🌍", in_string)).as_bytes().to_vec())
    }
}

```


```rust
impl Runnable for Morgen {
    fn run(&self, input: Vec<u8>) -> Result<Vec<u8>, RunErr> {
        let in_string = String::from_utf8(input).unwrap();
    
        Ok(String::from(format!("👋 Hallo Welt {} 🌍", in_string)).as_bytes().to_vec())
    }
}

```

> build the 2 Runnables and copy the wasm files to a `plugins` directory
```bash
subo build hello
cp hello/hello.wasm plugins/hello.wasm 
subo build morgen
cp morgen/morgen.wasm plugins/morgen.wasm
```

> build the cli, and run it with the name of the module as a parameter
```bash
go build
./sat-cli hello Bob
# 👋 Hello world Bob 🌍
./sat-cli morgen Bob
# 👋 Hallo Welt Bob 🌍
```




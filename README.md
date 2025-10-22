### First parser

Create a new simple parser for education 

<img width="1157" height="184" alt="image" src="https://github.com/user-attachments/assets/ac2c077c-ac94-4249-be67-c9f83bb05c4f" />

### Example

```rust
peg::parser! {
    pub grammar list_parser() for str {
      rule number() -> u32
        = n:$(['0'..='9']+) {? n.parse().or(Err("u32")) }
  
      pub rule list() -> Vec<u32>
        = "[" l:(number() ** ",") "]" { l }
    }
  }


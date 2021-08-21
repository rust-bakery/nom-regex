# nom-regex

This crate provides combinators for [nom parser combinators](https://crates.io/crates/nom) using the [regex](https://crates.io/crates/regex) crate.

## Example

```rust
use nom::{Err, error::ErrorKind};
use nom_regex::str::re_match;
fn main() {
  let re = regex::Regex::new(r"^\d{4}").unwrap();
  let parser = re_match::<(&str, ErrorKind)>(re);
  assert_eq!(parser("2019"), Ok(("", "2019")));
  assert_eq!(parser("abc"), Err(Err::Error(("abc", ErrorKind::RegexpMatch))));
  assert_eq!(parser("2019-10"), Ok(("", "2019-10")));
}
```

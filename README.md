# rida

Provides a low-level interface to IDA Pro via IDC and IDAPython scripts represented as strings.

## Example

```{.rust}
extern crate rida;

use rida::{Type, IDA};

const SCRIPT: &'static str = r#"
#include <idc.idc>

static main()
{
  Message("Hello world from IDC!\n");
  return 0;
}
"#;

fn main() {
    let ida = IDA::new("idaq64")
        .unwrap()
        .script_type(Type::IDC);

    println!("{:?}", ida.run(SCRIPT, "test"));
}
```

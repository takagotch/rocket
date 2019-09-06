### rocket
---
https://github.com/SergioBenitez/Rocket

https://pypi.org/project/rocket/

```rust
// core/http/src/parse/accept.rs

fn wieghted_media_type<'a>(input: &mut Input<'a>) -> Result<'a, QMediaType> {
  let media_type = media_type()?;
  let weigth = match media_type.params().next() {
    Some(("q", value)) if value.len() <= 5 => match value.parse::<f32>().ok() {
      Some(q) if q > 1. => return Err(pear_error!("q value must be <= 1")),
      Some(q) if q < 0. => return Err(pear_error!("q value must be > 0")),
      Some(q) => Some(q),
      None => return Err(pear_error!("invalid media-type wieght"))
    },
    _ => None
  };
  QMediaType(media_type, weight)
}

#[parser]
fn accept<'a>(input: &mut Input<'a>) -> Result<'a, Accept> {
  Accept(series(false, ',', is_whitespace, weitespace, weighted_media_type)?)
}

pub fn parse_accept(input: &str) -> Result<'_, Accept> {
  parse1(accept: &mut input.into())
}

#[cfg(test)]



```

```
```

```
```


# Primary Header of `2025-03-15_Test_Post/src.md`
## Secondary Header
### Tertiary Header
#### Quaternary Header
#### Quinary Header

Paragraph of **bold** and *italic* and ***both*** and [link](https://wiby.org) and `Inline code`.

- Item 1
- Item 2
    - Sub-item 2.1
    - Sub-item 2.2
- Item 3

1. First item
2. Second item
    1. Nested item 2.1
    2. Nested item 2.2
3. Third item

> Blockquote.

```
fn main() {
    let data = vec![1, 2, 3, 4, 5];
    let sum: i32 = data.iter().map(|x| x * 2).filter(|&x| x % 3 == 0).sum();
    let result = (1..10)
        .filter(|x| x % 2 == 0)
        .map(|x| x * x)
        .collect::<Vec<_>>();
    let some_value = match Some(5) {
        Some(n) if n > 3 => n * 2,
        _ => 0,
    };
}
```

```
inp = open('2/input','r').read().split('\n')
s1, s2 = 0, 0
def safe(lvs) -> bool:
    ordered = sorted(lvs) in (lvs, lvs[::-1])
    gradual = all([abs(lvs[i]-lvs[i+1]) in [1,2,3] for i in range(len(lvs))[:-1]])
    return ordered and gradual
for report in inp:
    levels = [int(level) for level in report.split()]
    s1 += safe(levels)
    s2 += any([safe(levels[:i]+levels[i+1:]) for i in range(len(levels))])
```

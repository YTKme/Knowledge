# BASH (Bourne Again SHell)

## Useful Command

### Get nth Line

```bash
# Using head and tail
<command> | head -<end> | tail -<start>

# Using sed
<command> | sed -n '<start>,<end>p
```

### Get Multiple Line

```bash
# Using sed
<command> | sed -n '<start>p,<end>p
```
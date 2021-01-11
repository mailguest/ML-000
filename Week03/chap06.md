# chap06

## Jax

1. jax.numpy 几乎和numpy一样，唯一jax的numpy无法和numpy无缝转换，比较费时间。
2. jax会自动将程序跑在TPU和GPU中。如果找不到会降到CPU中。

jit提速
block_until_ready 会等待执行

@jax.partial
static_argnums 不能用keywords argnums




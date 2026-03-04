# 总结
1. 调研了阿里百炼大模型 API，如何使用 显性 cache（主动 cache）的方法
2. 根据 4 轮调用，计算每一次出 cache token 数量，符合预期逻辑


# token返回结果

## chat
```
    "usage": {
        "completion_tokens": 317,
        "prompt_tokens": 2231,
        "prompt_tokens_details": {
            "cache_creation": {
                "ephemeral_5m_input_tokens": 0
            },
            "cache_creation_input_tokens": 0,
            "cache_type": "ephemeral",
            "cached_tokens": 1211
        },
        "total_tokens": 2548
    }
```

## anthropic

```
cache_creation=BetaCacheCreation(ephemeral_1h_input_tokens=None, ephemeral_5m_input_tokens=1698),
cache_creation_input_tokens=1698,
cache_read_input_tokens=4883,
input_tokens=4,
output_tokens=1916,
server_tool_use=None,
service_tier=None

总输入token = input_tokens + cache_creation_input_tokens + cache_read_input_tokens

```

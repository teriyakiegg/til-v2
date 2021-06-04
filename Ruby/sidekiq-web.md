# sidekiq web
https://qiita.com/ts-3156/items/2959c79c79bd9979ef97

```
sidekiqには監視APIがついており設定にもよりますが、/sidekiq/statsのURLにアクセスすると以下のようなJSONが取得できます。

{
  "sidekiq": {
    "processed": 166,
    "failed": 79,
    "busy": 0,
    "processes": 1,
    "enqueued": 0,
    "scheduled": 0,
    "retries": 0,
    "dead": 12,
    "default_latency": 0
  },
  "redis": {
    "redis_version": "2.8.23",
    "uptime_in_days": "310",
    "connected_clients": "42",
    "used_memory_human": "61.38M",
    "used_memory_peak_human": "65.63M"
  }
}
```
https://qiita.com/wapa5pow/items/de6f6718ef9318324c76#stats
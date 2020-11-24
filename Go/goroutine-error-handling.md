# goroutine error handling
context.WithCancel()で生んだcancelを使ってcancel()して、
```
select {
  case <-ctx.Done():
    // hoge
}
```
こんな感じで拾える

https://stackoverflow.com/questions/45500836/close-multiple-goroutine-if-an-error-occurs-in-one-in-go

```
func doAllWork() error {
    var wg sync.WaitGroup

    ctx, cancel := context.WithCancel(context.Background())
    defer cancel() // Make sure it's called to release resources even if no errors

    for i := 0; i < 2; i++ {
        wg.Add(1)
        go func(i int) {
            defer wg.Done()

            for j := 0; j < 10; j++ {
                // Check if any error occurred in any other gorouties:
                select {
                case <-ctx.Done():
                    return // Error somewhere, terminate
                default: // Default is must to avoid blocking
                }
                result, err := work(j)
                if err != nil {
                    fmt.Printf("Worker #%d during %d, error: %v\n", i, j, err)
                    cancel()
                    return
                }
                fmt.Printf("Worker #%d finished %d, result: %d.\n", i, j, result)
            }
        }(i)
    }
    wg.Wait()

    return ctx.Err()
}
```

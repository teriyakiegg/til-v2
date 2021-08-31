# active job sidekiq
https://qiita.com/tatsurou313/items/d3664f8dda05dcd12d56

## リトライとdead job
https://h3poteto.hatenablog.com/entry/2015/01/27/221842

### 公式ドキュメント
https://github.com/mperham/sidekiq/wiki/Error-Handling

```
Best Practices
Use an error service - Honeybadger, Airbrake, Rollbar, BugSnag, Sentry, Exceptiontrap, Raygun, etc. They're all similar in feature sets and pricing but pick one and use it. The error service will send you an email every time there is an exception in a job (Smarter ones like Honeybadger will send email on the 1st, 3rd and 10th identical error so your inbox won't be overwhelmed if 1000s of jobs are failing).
Let Sidekiq catch errors raised by your jobs. Sidekiq's built-in retry mechanism will catch those exceptions and retry the jobs regularly. The error service will notify you of the exception. You fix the bug, deploy the fix and Sidekiq will retry your job successfully.
If you don't fix the bug within 25 retries (about 21 days), Sidekiq will stop retrying and move your job to the Dead set. You can fix the bug and retry the job manually anytime within the next 6 months using the Web UI.
After 6 months, Sidekiq will discard the job.
```

```
The maximum number of retries can be globally configured by adding the following to your sidekiq.yml:

:max_retries: 1
```

```
Web UI
The Sidekiq Web UI has a "Retries" and "Dead" tab which lists failed jobs and allows you to run them, inspect them or delete them.
```
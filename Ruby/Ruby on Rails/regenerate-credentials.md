# Regenerate credentials

When you git-pushed config/master.key by mistake you should regenerate credentials.

Here is a procedure to regenerate.
```
1. Copy content of original credentials rails credentials:show somewhere temporarily.
2. Remove config/master.key and config/credentials.yml.enc
3. Run EDITOR=vim rails credentials:edit in the terminal: This command will create a new master.key and credentials.yml.enc if they do not exist.
4. Paste the original credentials you copied (step 1) in the new credentials file (and save + quit vim)
5. Add and Commit the file config/credentials.yml.enc
```

References:
https://gist.github.com/db0sch/19c321cbc727917bc0e12849a7565af9

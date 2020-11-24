# List installed perl modules
Try following command.    
$ perl -E '-d and say for @INC' | grep -E ^/ | xargs -I {} find {} -name '*.pm'

1. Output module paths located @INC.  
2. Exclude current directory.  
3. Output only .pm(module) files.

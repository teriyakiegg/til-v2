# Check if module is installed
Run "$ perldoc -m Module::Name"  
If it is installed, there is no output. If not, the output is "No module found for "Module::Name"."  
https://server.etutsplus.com/how-do-i-get-a-list-of-installed-cpan-modules/  
  
Or try following commnad.  
$ perl -E '-d and say for @INC' | grep -E ^/ | xargs -I {} find {} -name '*.pm' | grep Module/Name

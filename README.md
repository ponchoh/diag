# FOR TESTS ONLY

## Prerequisites :

* Need to have internet to access the github website.
* Only work on Central server (local or deported DB server).

##How to use : 
```
 bash <(curl -s https://raw.githubusercontent.com/alexvea/diag/main/diag.sh)
```
## Help :
```
The script will help to diagnose somes cases on your Centreon platform.
Syntax: [-h|d]
options:
h     Print this help.
d     Display debug
```

## Functionnalities :

* Compatible with SQL request, bash oneliner with characters ||(false condition) and ;;(case).
* Placeholders to get tested and retrieved values on non-expected case output.
* 4 types of output : OK, INFO, ERROR, DEBUG.

  1. OK when the expected test is matched. Only display the test description.
  2. INFO when the expected test is not matched with tag info. Display the test description and more info output.
  3. ERROR when the expected test is not matched with tag error. Display the test description and more info output.
  4. DEBUG when -d option is used. Add a line with the test command.
 

## Example :
![image](https://github.com/alexvea/diag/assets/35368807/726d4978-ba46-44d5-bc5b-2baa0bde74d5)

## Check_list syntax :

Using ||| and ;;; delimiters to be able to use the bash syntax || false condition and ;; case with oneliner.  

```
Command type[SQL|CMD]|||Description of the test|||Test command|||Expected type value[value|cmd];;;Expected value;;;Test sign[=|>|<|!=];;;Tag[info|error]|||Non expected output
```
example :
```
SQL|||Check if the local admin is blocked|||SELECT COUNT(*) FROM centreon.contact WHERE blocking_time IS NOT NULL AND contact_id = 1|||value;;;0;;;=;;;error|||Please see this link : https://support.centreon.com/hc/en-us/articles/10342991678609--User-is-blocked-error-message-on-Centreon-login-page
```



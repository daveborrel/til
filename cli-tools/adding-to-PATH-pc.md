# Adding a new CLI tool to a PC's path

Ran into this issue when trying to download GitHub CLi

`winget install --id GitHub.cli`

When I tried to run `gh create example.py`, I got:

```
gh : The term 'gh' is not recognized as the name of a cmdlet, function, script file, or operable program. Check the spelling of the name, or if a path was
included, verify that the path is correct and try again.
At line:1 char:1
+ gh gist create hennge_challenge.py
+ ~~
    + CategoryInfo          : ObjectNotFound: (gh:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

**Steps to add to PATH**

1. Search for Edit the System Environment Variables in the Control Panel
2. In the newly opene System Properties, Click Environment Variables
3. In the second table, that says System Variables, Click New...
4. Add the new variable name, and then for variable value: add the path to that file you downloaded.
   - In the case of GitHub CLI it was in `C:\Program Files\GitHub CLI\`
5. Restart your powershell and then it should work.

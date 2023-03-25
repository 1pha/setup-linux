# Files

## Count number of files
``` bash
ls | wc -l
```
!!!question "What is `|`?"
    `|` works as a pipe. This operand will take outputs from previous command and send it to next command. From above example, `wc -l` will count the number of outputs from `ls`.

## Removing certain files
```bash
find . -type f -name '*.o' -delete
```
[Reference](https://unix.stackexchange.com/questions/116389/recursively-delete-all-files-with-a-given-extension)
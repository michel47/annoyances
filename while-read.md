---
---
# while read ...


ok I am annoyed enough to write a memo as I can remember well how a read is done in /bin/sh ( not /bin/bash !)

for spliting the words or the lines 

```sh
## for each words ...
ls -md * | sed -e 's/,* /\n/g' | while read word; do
echo "# '$word'"
done
# if can be done with a for too w/o "" arround $() !
for word in $(ls -md * | sed -e 's/,//g' ); do
echo "# '$word'"
done

## for each line ...
ls -1d * | while read line; do
echo "# '$line'"
done
```


see also: [multiline read][1]


[1]: https://gist.github.com/michel47/f799d5ca79e5bd889ab68ace9df07a8c




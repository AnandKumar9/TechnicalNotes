Extract every 4th line. In below example, every 4th line beginning at line number 2 is extracted.
```
awk -v n=4 'NR%n==2' Temp.txt | pbcopy
```

Remove all empty lines.
```
sed -E '/^$/d' Temp.txt
```

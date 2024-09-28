# Bash scripting
---
## - Array
```bash
#!/bin/bash
read N
declare -a array[$N]
sum=0
for (( i = 0; i < $N; i++ )) 
do
    read x
    array+=($x)
    # echo ${array[$i]}
    sum=$(( $sum + ${array[$i]} ))
    # echo $sum
done

printf "%.3f\n" `echo $sum / $N | bc -l`
```


[↩️](../Linux.html)

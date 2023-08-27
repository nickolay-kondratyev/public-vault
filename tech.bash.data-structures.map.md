---
id: 70vd1mg0n3a9ksr5gqp20pt
title: Map
desc: ''
updated: 1679158526651
created: 1679158526651
---


<details>
<summary>Declare Map</summary>

```bash
declare -A mymap

mymap["key1"]="value1"
mymap["key2"]="value2"
mymap["key3"]="value3"

echo ${mymap["key2"]}
```

The command `declare -A mymap` is used to declare an associative array in Bash. The `-A` option is used to specify that the variable mymap is an associative array.

An associative array is a type of array in Bash that uses strings as indexes instead of numbers. In this case, mymap is an associative array that will store key-value pairs. The keys in this array are the strings "key1", "key2", and "key3", and the corresponding values are "value1", "value2", and "value3", respectively.
#chatgpt

</details>

<details>
<summary>Iterate over the map</summary>

```shell
declare -A mymap

mymap["key1"]="value1"
mymap["key2"]="value2"
mymap["key3"]="value3"

# Iterate over the keys of the associative array
for key in "${!mymap[@]}"; do
  echo "Key: $key, Value: ${mymap[$key]}"
done

```
</details>

<details>
<summary>Consider using JSON</summary>

Note: if you are using MAPs in bash consider using JSON with `jq` instead.
- JSON with jq will allow:
  - multi values per key/complex values per key.
  - allow values be read/created by other languages/tools.
</details>


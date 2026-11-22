# hash_app

## How to run

No compiling needed. Run:

```
./hash_app <n> <s>
```

or

```
python3 hash_app <n> <s>
```



- n: number of buckets
- s: max size of a bucket file

Example:

```
./hash_app 5 20
Please enter the string: Hello
Hello added to 1.txt
```

Press Ctrl+C to stop.



## Hashing algorithm

I used **FNV-1a (32-bit)**. I wrote it myself in the code, so no library needs to be installed. The bucket number is `hash % n`, and if the result is 0 the string goes to n.txt.

## Overflow buckets

If a string doesn't fit in a bucket file (it would go over s), it goes into an overflow file. Overflow files are named like this: 3.txt -> 3_1.txt -> 3_2.txt -> ...

To find where to write, the program checks 3_1.txt, 3_2.txt, ... until it finds one that doesn't exist. The last existing file is where it writes. If that file is full, it creates the next one. This way nothing extra is stored inside the files, and overflow files never get mixed up with the normal bucket files.

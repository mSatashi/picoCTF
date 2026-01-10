**Pico CTF-Journal 3**

**Challenge Name:** Hidden in Plainsight

**Level:** Easy

**Description:**

You’re given a seemingly ordinary JPG image. Something is tucked away out of sight inside the file. Your task is to discover the hidden payload and extract the flag.

**Solution:**

After we download the file we can start initial reconnaisance with this command to see if there is some good information

```
file img.jpg
exiftool img.jpg
```

okay we got valuable information on the meta part it seems like a `base64` encoding so we will try to uncover what is hidden on that part

```
...
Comment                         : c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9
Image Width                     : 640
Image Height                    : 640
...
```

to uncover what it said we will use this common command
```
echo 'c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9' | base64 -d
```

and it said 
```
steghide:cEF6endvcmlcqmQ=
```

Interesting... at this moment we need to use `steghide` command and there is something like `base64` encoding. I guess it is some password to extract the file using `steghide`

> `steghide` is a tool to extract stegonography

well we need to uncover the `base64` encoding again with the command
```
echo 'cEF6endvcmlcqmQ=' | base64 -d
```

well it seems a little bit a puzzle here, because we got output like this. When we input this to `steghide` we will throw an error
```
pAzzwori\�d   
```

I am guessing that the correct password is `'pAzzword'`. And we got the extracted `flag.txt` file to see the final flag.
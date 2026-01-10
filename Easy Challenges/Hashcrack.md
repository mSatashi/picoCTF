**Pico CTF-Journal 4**

**Challenge Name:** hashcrack

**Level:** Easy


**Description:** \
A company stored a secret message on a server which got breached due to the admin using weakly hashed passwords. Can you gain access to the secret stored within the server?

Additional details will be available after launching your challenge instance.

**Solution:**\
Once we start the instance, the app will show us the first hash
```
Welcome!! Looking For the Secret?

We have identified a hash: 482c811da5d5b4bc6d497ffa98491e38

```

this is md5 hash we can use tool like `'hashcat'` to find plain text strings that match the hash. This command will perform dictionary attack with `'rockyou.txt'` file.

```
hashcat -m 0 -a 0 '482c811da5d5b4bc6d497ffa98491e38' ~/Documents/rockyou.txt
```

after we got the first password the app will give us another hash that need to be solved.

```
Flag is yet to be revealed!! Crack this hash: b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3
```

it seems like a same hash but it is not. this is `'SHA-1'` hash. so we need to modify a little bit our `hashcat` command to uncover the hash.

```
hashcat -m 100 -a 0 'b7a875fc1ea228b9061041b7cec4bd3c52ab3ce3' ~/Documents/rockyou.txt
```

yet, another hash is showing to us after we got the password.

```
Almost there!! Crack this hash: 916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745
```

This is another type of hash named `'SHA-256'` hash it is stronger hash than `'SHA-1'` hash but it still can be cracked. so we need to modify again our `hashcat` command to cracking the hash.

```
hashcat -m 1400 -a 0 '916e8c4f79b25028c9e467f1eb8eee6d6bbdff965f9928310ad30a8d88697745' ~/Documents/rockyou.txt
```

And finally we got the flag!
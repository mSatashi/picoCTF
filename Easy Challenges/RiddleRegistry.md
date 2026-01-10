**Pico CTF-Journal 1**

**Challenge Name:** Riddle Registry

**Level:** Easy


**Description:** \
Hi, intrepid investigator! 📄🔍 You've stumbled upon a peculiar PDF filled with what seems like nothing more than garbled nonsense. But beware! Not everything is as it appears. Amidst the chaos lies a hidden treasure—an elusive flag waiting to be uncovered. Find the PDF file here Hidden Confidential Document and uncover the flag within the metadata.

**Solution:** \
We first given a file named confidential.pdf at first it just like ordinary pdf with censored part. I guess there is nothing much to seek at the plain sight. So i re-read the description and it said something about 'metadata'.

I use the command to see if there is something on the file.
```
file confidential.pdf
```
it seems there is nothing, just a information about the file type.
```
confidential.pdf: PDF document, version 1.7, 1 page(s)
```

so we go to the next step to read metadata on detailed information with this command.
```
exiftool confidential.pdf
```

`exiftool` is a tool to see all the detailed information according to file metadata. such as **File Name**, **Author**, **File Type**, **File Permission**, etc.

```
...
Page Count                      : 1
Producer                        : PyPDF2
Author                          : <REDACTED>
...
```

well we could see some interesting `strings` at the author section. My guess it wase base64 encryption we can use tool such as **CyberChef**, or just use this command 

```
echo '<REDACTED>' | base64 -d
```

and finally we got the flag! 
**Pico CTF-Journal 2**

**Challenge Name:** Log Hunt

**Level:** Easy

**Description:**

Our server seems to be leaking pieces of a secret flag in its logs. The parts are scattered and sometimes repeated. Can you reconstruct the original flag? Download the logs and figure out the full flag from the fragments.

**Solution:**

Well this is simple challenge, our objection is to find secret flag on the log file. we can use simple command like this to find matching `strings`.
```
cat server.log | grep 'pico'
```

we notice that the flag is fragmented into some parts. so, we need to change the command into this 
```
at server.log | grep "INFO FLAGPART:"
```

and we can try to put all together the flag!
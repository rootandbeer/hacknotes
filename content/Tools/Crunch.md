---
title: Crunch
description: 
draft: false
tags: 
date: 2024-10-19
---
## Example
```bash
crunch 8 8 -t k1ll0r@@ -o wordlist.txt -f /usr/share/crunch/charset.lst mixalpha-numeric-all-space
```
## Explanation
- **`crunch 8 8`**: This tells Crunch to generate words with a fixed length of 8 characters. Both the minimum and maximum length are set to 8.
    
- **`-t k1ll0r@@`**: This specifies a pattern for the generated words:
    
    - `k1ll0r` are static characters that will remain the same in each word generated.
    - `@@` are placeholders that will be replaced by characters defined in the specified charset.
- **`-o wordlist.txt`**: This outputs the generated wordlist to a file called `wordlist.txt`.
    
- **`-f /usr/share/crunch/charset.lst mixalpha-numeric-all-space`**: This tells Crunch to use the `mixalpha-numeric-all-space` charset from the file `/usr/share/crunch/charset.lst`. The charset includes mixed case letters (uppercase and lowercase), numbers, and symbols, as well as spaces.

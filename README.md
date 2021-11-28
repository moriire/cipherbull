# cipherbull
Symmetric Encryption - Ceaser, Vigenere
```sh

import string
class Ceaser:
    """
            k->key
            w-plain text
    """
    def __init__(self, k:int, w):
        self.k = k
        self.w = w
        
    def encrypt(self):
        w = ""
        li = tuple(map(
            lambda l: ord(l).__add__(self.k),
                self.w)
                   )
        for l in li:
            w += chr(l)
        return w

    def decrypt(self):
        w = ""
        li = tuple(map(
            lambda l: ord(l).__sub__(self.k),
                self.w)
                )
        for l in li:
            w += chr(l)
        return w
    
    def key(self):
        return self.k
```

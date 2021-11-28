# cipherbull
Symmetric Encryption - Ceaser, Vigenere and others

### [Ceaser Cipher](https://en.wikipedia.org/wiki/Caesar_cipher)
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

###  [Vigenere Cipher](https://en.wikipedia.org/wiki/Vigen%C3%A8re_cipher)
```sh
class Vigenere:
    string = string.ascii_lowercase
    def __init__(self, k:str, w:str):
        """
            k->key
            w-plain text
        """
        self.k = k
        self.w = w.lower()

    def __alpha(self, n):
        return self.string[n]
        
    def __key(self):
        nk = len(self.k)
        nw = len(self.w)
        mod = nw//nk
        for i in range(mod):
            self.k += self.k
        self.k = self.k + self.k[:len(self.w)-len(self.k)-1]
        return self.k

    def res(self):
        for n, i in enumerate(self.w):
            li = (self.string.index(i), self.string.index(self.k[n]))
            yield li
            
    def encrypt(self):
        res = tuple(map(lambda x: x[0].__add__(x[1]), self.res()))
        w = ""
        for l in res:
            w += self.__alpha(l-26)
        return w

    def decrypt(self):
        res = tuple(map(lambda x: x[0].__sub__(x[1])+25, self.res()))
        w = ""
        for l in self.res:
            w += self.__alpha(l-26)
        return w
    def key(self):
        return self.k

```

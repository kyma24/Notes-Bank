```
hash = FNV_offset_basis
for each octetOfData to be hashed
    hash = hash xor octetOfData
    hash = hash * FNV_prime
return hash
```

# cryptocurrency-bitcoin-mining-python

simple python code for mining bitcoin cryptocurrency

1. The Concept
2. Mining
3. Required Data
4. Python Code
5. Execution
6. Output 


# 1. The Concept

## SHA256:
When you execute the same code, you will get the same hash code for a particular string and hence it always gives a definite output for a definite input.

You can see the same output when you execute the string "ABC"

Example:
```
from hashlib import sha256
sha256("ABC".encode("ascii")).hexdigest()

Output:
b5d4045c3f466fa91fe2cc6abe79232a1a57cdf104f7a26e716e0a1e2789df78
```

# 2. Mining:
Mining is the processing of guessing a number named "Nonce" that generates hashes with first 'n' number of zeros.
Example hash output: 000000000000000000006bd3d6ef94d8a01de84e171d3553534783b128f06aad

> bitcoin mine = SHA256(block_number + transaction + previous_hash + nonce)

Bitcoin follows a protocol that the first ‘n’ number of digits of the has must be zero. Currently the value of ‘n’ stands at 20 but I am gonna show it to you using smaller ‘n’ so that the code actually finishes execution fast. The text over which you would apply SHA256 is made up of 
  the Block number 
  transition details
  previous hash value
and since all the 3 previous values are constant for a block and cannot be changed, a new value called ‘Nonce’ is introduced. Our goal is to find the Nonce value so that the hash of the block produces the required number of zeros in the beginning according to the protocol.

short code:
```
transactions='''
A->B->10
B->c->5
'''
difficulty = 4
import time as t
begin=t.time()
new_hash = mine(684260,transactions,"000000000000000000006bd3d6ef94d8a01de84e171d3553534783b128f06aad",difficulty)
print("Hash value : ",new_hash)
time_taken=t.time()- begin
print("The mining process took ",time_taken,"seconds")
```
Output:
Bitcoin mined with nonce value: 36674
Hash value :  000086ae35230f32b08e9da254bd7ba1b351f11d40bde27a7ebd5e7ec9568f8d
The mining process took  0.08681821823120117 seconds

If we change the difficulty value by even 1, hence it will be 5, the output will be.

Bitcoin mined with nonce value : 2387325
Hash value :  00000f5254db00fa0dde976d53bb39c11f9350292949493943a90610d62c1a5e
The mining process took  4.895745515823364 seconds

Hence you can see the drastic change in the time taken by the same code when the difficulty is increased from 4 to 5 and it only keeps on increasing exponentially. Thus that is the main reason why mining one bitcoin takes so much energy and computational power. If that was not enough, you have to be the first one to find the hash or you will not be rewarded. So you are also competing with all the other miners out there and this whole system works on the ‘PoW’ or ‘Proof of Work concept’.



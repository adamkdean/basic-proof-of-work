# basic-proof-of-work

Basic Proof of Work (PoW) procedure

```javascript
const crypto = require('crypto')
const SHA256 = require('crypto-js/sha256')

let start = Date.now()
let difficulty = 5
let count = 0

while (true) {
  const nonce = crypto.randomBytes(4).toString('hex')
  const hash = SHA256(nonce).toString()
  const elapsed = Date.now() - start
  count += 1

  console.log(count, elapsed, nonce, hash)

  if (hash.substr(0, difficulty) === pad('0', difficulty)) {
    console.log(`---------------------`)
    console.log(`diff : ${difficulty}`)
    console.log(`hash : ${hash}`)
    console.log(`time : ${elapsed} ms`)
    console.log(`count: ${count}`)
    console.log(`---------------------`)
    break
  }
}

function pad(char, count) {
  let s = ''
  for (let i = 0; i < count; i++) s += char
  return s
}
```

## Example run

This shows it took 17 iterations, or 6 ms, to generate a hash starting with a 0.

```
1 0 8e44f6cb b02aa92d810412dba22207281e914c9f818549de285545879712852c7439edff
2 4 0c8b1d47 97ec577098aa15740a784f5d96cc5945a65a0bd2fcd28360a521b179f9e74abf
3 4 57660a13 1793236fecde256c958d9753ff0256f4c742c346f86515352f4f54ebd8b83f8e
4 5 52046f0e 70fb51640489bf96c487cc6f07bdcd9635c074639a999a91005a15b3c05ffb06
5 5 7f72cec5 aaf9514e91f073a7412459a042e92133bdc298c6ceb5103c76b7410611ba0854
6 5 504abf27 409cf5b02350904dc69edcd8e351bc95bb1fbe702ab67516aef8600828b31394
7 5 cc935395 475f8f9ff6e3d570f08f6345951ae89d565d8cf6bc8a5f4ab47e320537d10c61
8 5 9fb226d5 bd99e3f304185f7891f1db2a2236f5570bed5f435018bf38bb26f1d9e49fde19
9 5 cba7d198 d27b934311fbeeeff2ecf9b05769b80f208a49d4de1e39a14a8f22ee9a95fb98
10 5 7b355051 f71fea8f47e9dd8d9f985c69f95cae7eaca32f7cc60632b4aa05f9a48b75a44f
11 5 9b103156 323618d9cd5dea8e4b9277e7387fb9b34237af4a5c3c6f9e025f3657ddf5808d
12 5 adf3da54 9773f673b11c542c22772c3fe477484af311baca9beb80c1c7063c6d34b5b567
13 6 5a3f9dad 620b06bddad1151e8e631ba3abd10415dde6ae429b4d6d0b87e74803e8550411
14 6 692c0e0c d6ad5c419b240dbdbb586999114564118d695e7d3f9e927508271ef33b25b441
15 6 3968a0ff e8720841906a9b58e70a0cd6a517d418f7ae0ace08a9f38fb20e0a9ab6026e16
16 6 c650356c e20a87806b25fe5dce7d51d980b5f340fe17e43ed1b81783dab44ba62f6f5cf9
17 6 388160c3 0333bfbb5bbc2a257eb1617cbebfbad197d2e08cf4da5e24158909be0bce2ef1
---------------------
diff : 1
hash : 0333bfbb5bbc2a257eb1617cbebfbad197d2e08cf4da5e24158909be0bce2ef1
time : 6 ms
count: 17
---------------------
```

## Results

As the difficult is increased, the required number of preceding zeros increases.

```
---------------------
diff : 1
hash : 0333bfbb5bbc2a257eb1617cbebfbad197d2e08cf4da5e24158909be0bce2ef1
time : 6 ms
count: 17
---------------------
diff : 2
hash : 00c18742c5023a5908b924e66179ad4d1162021e3f2f603b5d585dd5467ea544
time : 6 ms
count: 22
---------------------
diff : 3
hash : 000d5190ff8f4f299404a366eb5b1ea00eb35218f84671aa53dcde591d80997f
time : 325 ms
count: 9110
---------------------
diff : 4
hash : 00007e6d54f4137b513c60e8f49435629995f683385bb7e83a0b591d1e10cb57
time : 858 ms
count: 25933
---------------------
diff : 5
hash : 0000052130afc62034cd101b38c81862f861b71d4d02d53a395345dbc37d2f30
time : 23797 ms
count: 974818
---------------------
diff : 6
hash : 000000feed91daafee239cd5c04d85f723f25ce955fac059ff6feb2b25484d2d
time : 96499 ms
count: 4295599
---------------------
```

### Proof of Work (PoW) Solve Time

![Proof of Work (PoW) Solve Time](https://user-images.githubusercontent.com/1639527/110132269-e5f38000-7dc2-11eb-9f3d-456b4e3aca8e.png)

### Proof of Work (PoW) Solve Iterations

![Proof of Work (PoW) Solve Iterations](https://user-images.githubusercontent.com/1639527/110131845-8006f880-7dc2-11eb-922f-55d7a312d839.png)

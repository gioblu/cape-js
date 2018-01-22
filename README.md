cape-js 1.0
====

Cape implements private key, public salt, xor based symmetric stream cipher developed to offer encryption on limited microcontrollers.

Cape is an experimental project, should be used for research and educational purposes and should not be applied in production. Cape 3.0 has been posted on reddit/r/crypto to obtain feedback about its algorithm and great minds broke it in a matter of hours:
- rspencer01 exposed a full break of the algorithm using brute force and some hints about its plaintext
- silkeh exposed a known plaintext attack and poor performance of salt

This library is fully based on [Cape](https://github.com/gioblu/Cape) library developed by Giovanni Blu Mitolo. 


### How to use cape-js
Installation
```bash
    npm i @eldisniper/cape-js --save
```

Initialization
```js  
const Cape  = require("@eldisniper/cape-js").Cape;
var cape = new Cape("YOUR-ENCRYPTION-KEY", 0); // key , salt
```

Working like in C 
```js  
    var stringtoencrypt = "STRINGTOENCRYPT";
    var len = stringtoencrypt.length;
    var source = cape.stringToBinary(stringtoencrypt);
    var destination = new Array(len)
    cape.encrypt(source, destination);
    console.log("Encrypted ", cape.bin2string(destination));
    source = new Array(len);
    cape.decrypt(destination, source);
    console.log("Decrypted ", cape.bin2string(source));
```
Simplified version
```js
    const encrypted = cape.encrypt_str("STRINGTOENCRYPT");
    console.log("Encrypted ", encrypted);
    const decrypted = cape.decrypt_str(encrypted);
    console.log("Decrypted ", decrypted);
```


### License
    
```cpp  
/*  _____  _____   _____   _____    ____  ___
   |      |_____| |_____| |_____      |  |___
   |_____ |     | |       |_____  |___|   ___|     version 1.0

Cape Copyright (c) 2017, Abdelel All rights reserved.
This library is fully based on Cape by Giovanni Blu Mitolo. 

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License. */
```
